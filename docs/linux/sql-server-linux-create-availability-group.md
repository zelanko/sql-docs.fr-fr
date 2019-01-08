---
title: Créer et configurer un groupe de disponibilité pour SQL Server sur Linux | Microsoft Docs
description: Ce didacticiel montre comment créer et configurer des groupes de disponibilité pour SQL Server sur Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 06/28/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: e951e87abf7e88502597b6a3caf6f7ca4e34e60b
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53205748"
---
# <a name="create-and-configure-an-availability-group-for-sql-server-on-linux"></a>Créer et configurer un groupe de disponibilité pour SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Ce didacticiel explique comment créer et configurer un groupe de disponibilité (AG) pour [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] sur Linux. Contrairement à [!INCLUDE[sssql15-md](../includes/sssql15-md.md)] et les versions antérieures sur Windows, vous pouvez activer des groupes de disponibilité avec ou sans créer au préalable le cluster Pacemaker sous-jacent. L'intégration avec le cluster, si nécessaire, n’est effectuée qu’ultérieurement.

Le didacticiel comprend les tâches suivantes :
 
> [!div class="checklist"]
> * Activer les groupes de disponibilité.
> * Créer des certificats et des points de terminaison du groupe de disponibilité.
> * Utiliser [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] (SSMS) ou Transact-SQL pour créer un groupe de disponibilité.
> * Créer la connexion [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] et les autorisations pour Pacemaker.
> * Créer les ressources du groupe de disponibilité dans un cluster Pacemaker (type External uniquement).

## <a name="prerequisite"></a>Condition préalable
- Déployer le cluster à haute disponibilité Pacemaker, comme décrit dans [déployer un cluster Pacemaker pour SQL Server sur Linux](sql-server-linux-deploy-pacemaker-cluster.md).


## <a name="enable-the-availability-groups-feature"></a>Activez la fonctionnalité de groupes de disponibilité

Contrairement à l'environnement Windows, vous ne pouvez pas utiliser PowerShell ou [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Configuration Manager pour activer la fonctionnalité "Groupes de disponibilité (AG). Sous Linux, vous devez utiliser `mssql-conf` pour activer la fonctionnalité. Il existe deux façons d’activer la fonctionnalité de groupes de disponibilité : utiliser l'utilitaire `mssql-conf`, ou modifier le fichier `mssql.conf` manuellement.

> [!IMPORTANT]
> La fonctionnalité de groupe de disponibilité doit être activée pour les réplicas de configuration uniquement, même sur [!INCLUDE[ssexpress-md](../includes/ssexpress-md.md)].

### <a name="use-the-mssql-conf-utility"></a>Utiliser l’utilitaire mssql-conf

À l’invite de commande, exécuter ce qui suit :

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled 1
```

### <a name="edit-the-mssqlconf-file"></a>Modifier le fichier mssql.conf

Vous pouvez également modifier le fichier `mssql.conf`, situé sous le dossier `/var/opt/mssql`, pour ajouter les lignes suivantes :

```
[hadr]

hadr.hadrenabled = 1
```

### <a name="restart-includessnoversion-mdincludesssnoversion-mdmd"></a>Redémarrage [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]
Après avoir activé les groupes de disponibilité, comme sur Windows, vous devez redémarrer [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. Ceci peut être effectué avec la commande suivante :

```bash
sudo systemctl restart mssql-server
```

## <a name="create-the-availability-group-endpoints-and-certificates"></a>Créer les points de terminaison du groupe de disponibilité et les certificats

Un groupe de disponibilité utilise des points de terminaison TCP pour la communication. Sous Linux, les points de terminaison pour un groupe de disponibilité sont uniquement pris en charge si des certificats sont utilisés pour l’authentification. Cela signifie que le certificat provenant d’une instance doit être restauré sur toutes les autres instances qui seront des réplicas participant au même groupe de disponibilité. Le processus de certificat est nécessaire même pour un réplica en configuration uniquement. 

La création de points de terminaison et la restauration des certificats ne sont possibles que par le biais de Transact-SQL. Vous pouvez utiliser non - [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-certificats ainsi générés. Vous aurez également besoin d’un processus pour gérer et remplacer tous les certificats qui expirent.

> [!IMPORTANT]
> Si vous envisagez d’utiliser l'assistant [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] pour créer le groupe de disponibilité, vous devrez néanmoins créer et restaurer les certificats à l’aide de Transact-SQL sur Linux.

Pour la syntaxe complète sur les options disponibles pour les différentes commandes (par exemple, pour renforcer la sécurité), consultez :

-   [BACKUP CERTIFICATE](../t-sql/statements/backup-certificate-transact-sql.md)
-   [CREATE CERTIFICATE](../t-sql/statements/create-certificate-transact-sql.md)
-   [CREATE ENDPOINT](../t-sql/statements/create-endpoint-transact-sql.md)

> [!NOTE]
> Bien que vous allez créer un groupe de disponibilité, le type de point de terminaison utilise la clause *FOR DATABASE_MIRRORING*, car certains aspects sous-jacents étaient avant partagés par cette fonctionnalité désormais obsolète.

Cet exemple va créer des certificats pour une configuration à trois nœuds. Les noms d’instance sont LinAGN1, LinAGN2 et LinAGN3.

1.  Exécuter la commande suivante sur LinAGN1 pour créer la clé principale, le certificat et le point de terminaison, ainsi que pour sauvegarder le certificat. Pour cet exemple, le port TCP 5022 classique est utilisé pour le point de terminaison.
    
    ```SQL
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<StrongPassword>';
    
    GO
    
    CREATE CERTIFICATE LinAGN1_Cert
    WITH SUBJECT = 'LinAGN1 AG Certificate';
    
    GO
    
    BACKUP CERTIFICATE LinAGN1_Cert
    TO FILE = '/var/opt/mssql/data/LinAGN1_Cert.cer';
    
    GO
    
    CREATE ENDPOINT AGEP
    STATE = STARTED
    AS TCP (
        LISTENER_PORT = 5022,
        LISTENER_IP = ALL)
    FOR DATABASE_MIRRORING (
        AUTHENTICATION = CERTIFICATE LinAGN1_Cert,
        ROLE = ALL);
    
    GO
    ```
    
2.  Faire de même sur LinAGN2 :
    
    ```SQL
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<StrongPassword>';
    
    GO
    
    CREATE CERTIFICATE LinAGN2_Cert
    WITH SUBJECT = 'LinAGN2 AG Certificate';
    
    GO
    
    BACKUP CERTIFICATE LinAGN2_Cert
    TO FILE = '/var/opt/mssql/data/LinAGN2_Cert.cer';
    
    GO
    
    CREATE ENDPOINT AGEP
    STATE = STARTED
    AS TCP (
        LISTENER_PORT = 5022,
        LISTENER_IP = ALL)
    FOR DATABASE_MIRRORING (
        AUTHENTICATION = CERTIFICATE LinAGN2_Cert,
        ROLE = ALL);
    
    GO
    ```
    
3.  Pour finir, effectuer la même séquence sur LinAGN3 :
    
    ```SQL
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<StrongPassword>';
    
    GO
    
    CREATE CERTIFICATE LinAGN3_Cert
    WITH SUBJECT = 'LinAGN3 AG Certificate';
    
    GO
    
    BACKUP CERTIFICATE LinAGN3_Cert
    TO FILE = '/var/opt/mssql/data/LinAGN3_Cert.cer';
    
    GO
    
    CREATE ENDPOINT AGEP
    STATE = STARTED
    AS TCP (
        LISTENER_PORT = 5022,
        LISTENER_IP = ALL)
    FOR DATABASE_MIRRORING (
        AUTHENTICATION = CERTIFICATE LinAGN3_Cert,
        ROLE = ALL);
    
    GO
    ```
    
4.  À l’aide de `scp` ou d'un autre utilitaire, copier les sauvegardes du certificat sur chaque nœud qui fera partie du groupe de disponibilité.
    
    Pour cet exemple :
    
    - Copier LinAGN1_Cert.cer sur LinAGN2 et LinAGN3
    - Copier LinAGN2_Cert.cer sur LinAGN1 et LinAGN3.
    - Copier LinAGN3_Cert.cer sur LinAGN1 et LinAGN2.
    
5.  Modifier la propriété et le groupe associé avec les fichiers de certificat copiés dans `mssql`.
    
    ```bash
    sudo chown mssql:mssql <CertFileName>
    ```
    
6.  Créer les connexions au niveau de l’instance et les utilisateurs associés à LinAGN2 et LinAGN3 sur LinAGN1.
    
    ```SQL
    CREATE LOGIN LinAGN2_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN2_User FOR LOGIN LinAGN2_Login;
    
    GO
    
    CREATE LOGIN LinAGN3_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN3_User FOR LOGIN LinAGN3_Login;
    
    GO
    ```
    
7.  Restaurer LinAGN2_Cert et LinAGN3_Cert sur LinAGN1. Certificats d’autres réplicas est un aspect important de communication de groupe de disponibilité et de sécurité.
    
    ```SQL
    CREATE CERTIFICATE LinAGN2_Cert
    AUTHORIZATION LinAGN2_User
    FROM FILE = '/var/opt/mssql/data/LinAGN2_Cert.cer';
    
    GO
    
    CREATE CERTIFICATE LinAGN3_Cert
    AUTHORIZATION LinAGN3_User
    FROM FILE = '/var/opt/mssql/data/LinAGN3_Cert.cer';
    
    GO
    
8.  Grant the logins associated with LinAG2 and LinAGN3 permission to connect to the endpoint on LinAGN1.
    
    ```SQL
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN2_Login;
    
    GO
    
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN3_Login;
    
    GO
    ```
    
9.  Créer les connexions au niveau de l’instance et les utilisateurs associés à LinAGN1 et LinAGN3 sur LinAGN2.
    
    ```SQL
    CREATE LOGIN LinAGN1_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN1_User FOR LOGIN LinAGN1_Login;
    
    GO
    
    CREATE LOGIN LinAGN3_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN3_User FOR LOGIN LinAGN3_Login;
    
    GO
    ```
    
10.  Restaurer LinAGN1_Cert et LinAGN3_Cert sur LinAGN2. 
    
    ```SQL
    CREATE CERTIFICATE LinAGN1_Cert
    AUTHORIZATION LinAGN1_User
    FROM FILE = '/var/opt/mssql/data/LinAGN1_Cert.cer';
    
    GO
    
    CREATE CERTIFICATE LinAGN3_Cert
    AUTHORIZATION LinAGN3_User
    FROM FILE = '/var/opt/mssql/data/LinAGN3_Cert.cer';
    
    GO
    
11.  Grant the logins associated with LinAG1 and LinAGN3 permission to connect to the endpoint on LinAGN2.
    
    ```SQL
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN1_Login;
    
    GO
    
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN3_Login;
    
    GO
    ```
    
12.  Créer les connexions au niveau de l’instance et les utilisateurs associés à LinAGN1 et LinAGN2 sur LinAGN3.
    
    ```SQL
    CREATE LOGIN LinAGN1_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN1_User FOR LOGIN LinAGN1_Login;
    
    GO
    
    CREATE LOGIN LinAGN2_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN2_User FOR LOGIN LinAGN2_Login;
    
    GO
    ```
    
13.  Restaurer LinAGN1_Cert et LinAGN2_Cert sur LinAGN3. 
    
    ```SQL
    CREATE CERTIFICATE LinAGN1_Cert
    AUTHORIZATION LinAGN1_User
    FROM FILE = '/var/opt/mssql/data/LinAGN1_Cert.cer';
    
    GO
    
    CREATE CERTIFICATE LinAGN2_Cert
    AUTHORIZATION LinAGN2_User
    FROM FILE = '/var/opt/mssql/data/LinAGN2_Cert.cer';
    
    GO
    
14.  Grant the logins associated with LinAG1 and LinAGN2 permission to connect to the endpoint on LinAGN3.
    
    ```SQL
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN1_Login;
    
    GO
    
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN2_Login;
    
    GO
    ```

## <a name="create-the-availability-group"></a>Créer le groupe de disponibilité

Cette section explique comment utiliser [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] (SSMS) ou Transact-SQL pour créer le groupe de disponibilité pour [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)].

### <a name="use-includessmanstudiofull-mdincludesssmanstudiofull-mdmd"></a>Utiliser [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)].

Cette section montre comment créer un groupe de disponibilité avec un cluster de type External à l’aide de SSMS et l'assistant "nouveau groupe de disponibilité".

1.  Dans SSMS, développer **haute disponibilité Always On**, avec le bouton droit, cliquer sur **groupes de disponibilité**, puis sélectionner **Assistant Nouveau groupe de disponibilité**.

2.  Dans la boîte de dialogue de présentation, cliquer sur **suivant**.

3.  Dans la boîte de dialogue "spécifier les Options du groupe de disponibilité", entrer un nom pour le groupe de disponibilité, puis sélectionner un type de cluster EXTERNAL ou NONE dans la liste déroulante. "EXTERNAL" doit être utilisé quand Pacemaker sera déployé. "NONE" n’est utilisé que pour des scénarios spécifiques, telles que la lecture répartie. L’option de détection de l’intégrité au niveau de la base de données est facultative. Pour plus d’informations sur cette option, consulter l'[option de basculement détection de l’intégrité au niveau de disponibilité groupe base de données](../database-engine/availability-groups/windows/sql-server-always-on-database-health-detection-failover-option.md). Cliquer sur **Suivant**.

    ![](./media/sql-server-linux-create-availability-group/image3.png)

4.  Dans la boîte de dialogue "Sélectionner les bases de données", sélectionner les bases de données qui feront partie du groupe de disponibilité. Chaque base de données doit avoir une sauvegarde complète avant de pouvoir être ajoutée à un groupe de disponibilité. Cliquer sur **Suivant**.

5.  Dans la boîte de dialogue "spécifier les réplicas", cliquer sur **ajouter un réplica**.

6.  Dans la boîte de dialogue "Se connecter à un serveur", entrer le nom de l’instance [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] de Linux qui sera le réplica secondaire, et les informations d’identification pour se connecter. Cliquer sur **Se connecter**.

7.  Répéter les deux étapes précédentes pour l’instance qui contient un réplica en configuration uniquement ou un autre réplica secondaire.

8.  Les trois instances doivent maintenant être répertoriées dans la boîte de dialogue "spécifier les réplicas". Si vous utilisez un type de cluster EXTERNAL, pour le réplica secondaire qui sera un vrai réplica secondaire, assurez-vous que le Mode de disponibilité correspond à celle du réplica principal et que le mode de basculement est défini sur EXTERNAL. Pour le réplica en configuration uniquement, sélectionnez un mode de disponibilité de Configuration uniquement.

    L’exemple suivant montre un groupe de disponibilité avec deux réplicas, un cluster de type EXTERNAL et un réplica en configuration uniquement.

    ![](./media/sql-server-linux-create-availability-group/image4.png)

    L’exemple suivant montre un groupe de disponibilité avec deux réplicas, un cluster de type None et un réplica en configuration uniquement.

    ![](./media/sql-server-linux-create-availability-group/image5.png)

9.  Si vous souhaitez modifier les préférences de sauvegarde, cliquez sur l’onglet Préférences de sauvegarde. Pour plus d’informations sur les préférences de sauvegarde avec les groupes de disponibilité, consultez [configurer la sauvegarde sur les réplicas de disponibilité](../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md).

10. Si vous utilisez des bases de données secondaires ou si vous créez un groupe de disponibilité avec un cluster de type None pour une lecture répartie, vous pouvez créer un écouteur en sélectionnant l’onglet de l’écouteur. Un écouteur peut également être ajouté plus tard. Pour créer un écouteur, choisissez l’option **créer un écouteur de groupe de disponibilité** et entrez un nom, un port TCP/IP et déterminez s’il faut utiliser une adresse IP DHCP statique ou attribuée automatiquement. N’oubliez pas que pour un groupe de disponibilité avec un type de cluster aucun, l’adresse IP doit être statique et affectez à l’adresse du principal.

    ![](./media/sql-server-linux-create-availability-group/image6.png)

11. Si un écouteur est créé pour les scénarios lisibles, SSMS 17.3 ou ultérieure permet la création du routage en lecture seule dans l’Assistant. Il peut également être ajouté ultérieurement par le biais de SSMS ou Transact-SQL. Pour ajouter le routage en lecture seule maintenant :

    A.  Sélectionnez l’onglet routage en lecture seule.

    B.  Entrez les URL pour les réplicas en lecture seule. Ces URL sont similaires aux points de terminaison, à ceci près qu’elles utilisent le port de l’instance, pas le point de terminaison.

    c.  Sélectionnez chaque URL et en bas, sélectionnez les réplicas lisibles. Pour une sélection multiple, maintenez la touche MAJ ou cliquez et faites glisser.

12. Cliquer sur **Suivant**.

13. Choisissez comment l’ou les réplicas secondaire sera initialisé. La valeur par défaut consiste à utiliser [l’amorçage automatique](../database-engine/availability-groups/windows/automatically-initialize-always-on-availability-group.md), ce qui nécessite le même chemin d’accès sur tous les serveurs participant dans le groupe de disponibilité. Vous pouvez également laisser l’Assistant effectuer une copie de sauvegarde et de restauration (la deuxième option) ; il avoir une jointure si vous avez manuellement sauvegardé, copié et restauré la base de données sur l’ou les réplicas (troisième option) ; ou ajoutés ultérieurement de la base de données (la dernière option). Comme avec les certificats, si vous êtes manuellement les sauvegardes et les copier, les autorisations sur les fichiers de sauvegarde doit être définie sur l’ou les autres réplicas. Cliquer sur **Suivant**.

14. Dans la boîte de dialogue de Validation, si tous les éléments ne sont reçue en tant que réussite, examiner. Des avertissements sont acceptables et pas irrécupérable, comme si vous ne créez pas un écouteur. Cliquer sur **Suivant**.

15. Dans la boîte de dialogue Résumé, cliquez sur **Terminer**. Le processus pour créer le groupe de disponibilité commence.

16. Lors de la création du groupe de disponibilité est terminée, cliquez sur **fermer** sur les résultats. Vous pouvez maintenant voir le groupe de disponibilité sur les réplicas dans les vues de gestion dynamique ainsi que sous le dossier de haute disponibilité Always On dans SSMS.

### <a name="use-transact-sql"></a>Utilisation de Transact-SQL

Cette section présente des exemples de création d’un groupe de disponibilité à l’aide de Transact-SQL. L’écouteur et le routage en lecture seule peuvent être configurés après avoir créé le groupe de disponibilité. Le groupe de disponibilité peut être modifié avec `ALTER AVAILABILITY GROUP`, mais la modification du type de cluster ne peut pas être effectuée [!INCLUDE[sssql17-md](../includes/sssql17-md.md)]. Si vous n’aviez pas l’intention de créer un groupe de disponibilité avec un type de cluster externe, vous devez supprimer et recréer avec un type de cluster aucun. Vous trouverez plus d’informations et d’autres options sur les liens suivants :

-   [CREATE AVAILABILITY GROUP (Transact-SQL)](../t-sql/statements/create-availability-group-transact-sql.md)
-   [ALTER AVAILABILITY GROUP (Transact-SQL)](../t-sql/statements/alter-availability-group-transact-sql.md)
-   [Configurer le routage en lecture seule pour un groupe de disponibilité (SQL Server)](../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md)
-   [Créer ou configurer un écouteur de groupe de disponibilité (SQL Server)](../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)

#### <a name="example-one---two-replicas-with-a-configuration-only-replica-external-cluster-type"></a>Réplicas exemple un deux avec un réplica de la configuration uniquement (type de cluster externe)

Cet exemple montre comment créer un groupe de disponibilité de deux réplicas qui utilise un réplica en configuration seule.

1.  Exécuter sur le nœud qui sera le réplica principal contenant la copie en lecture/écriture complet des bases de données. Cet exemple utilise l’amorçage automatique.

    ```SQL
    CREATE AVAILABILITY GROUP [<AGName>]
    WITH (CLUSTER_TYPE = EXTERNAL)
    FOR DATABASE <DBName>
    REPLICA ON N'LinAGN1' WITH (
       ENDPOINT_URL = N' TCP://LinAGN1.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT),
    N'LinAGN2' WITH (
       ENDPOINT_URL = N'TCP://LinAGN2.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
       SEEDING_MODE = AUTOMATIC),
    N'LinAGN3' WITH (
       ENDPOINT_URL = N'TCP://LinAGN3.FullyQualified.Name:5022',
       AVAILABILITY_MODE = CONFIGURATION_ONLY);
       
    GO
    ```
    
2.  Dans une fenêtre de requête connectée à l’autre réplica, exécutez la commande suivante pour joindre le réplica au groupe de disponibilité et de lancer le processus d’amorçage du site principal vers le réplica secondaire.
    
    ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
    
    GO
    
    ALTER AVAILABILITY GROUP [<AGName>] GRANT CREATE ANY DATABASE;
    
    GO
    ```
    
3.  Dans une fenêtre de requête connectée au réplica en configuration seule, vous devez le joindre au groupe de disponibilité.
    
   ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
    
    GO
   ```

#### <a name="example-two---three-replicas-with-read-only-routing-external-cluster-type"></a>Réplicas exemple deux trois avec (type de cluster externe) de routage en lecture seule

Cet exemple illustre trois complète de réplicas et de routage comment en lecture seule peuvent être configurés dans le cadre de la création initiale du groupe de disponibilité.

1.  Exécuter sur le nœud qui sera le réplica principal contenant la copie en lecture/écriture complet des bases de données. Cet exemple utilise l’amorçage automatique.

    ```SQL
    CREATE AVAILABILITY GROUP [<AGName>]
    WITH (CLUSTER_TYPE = EXTERNAL)
    FOR DATABASE <DBName>
    REPLICA ON N'LinAGN1'
    WITH (
       ENDPOINT_URL = N'TCP://LinAGN1.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN2.FullyQualified.Name', 'LinAGN3.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL = N'TCP://LinAGN1.FullyQualified.Name:1433')),
    N'LinAGN2' WITH (
       ENDPOINT_URL = N'TCP://LinAGN2.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       SEEDING_MODE = AUTOMATIC,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN1.FullyQualified.Name', 'LinAGN3.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL = N'TCP://LinAGN2.FullyQualified.Name:1433')),
    N'LinAGN3' WITH (
       ENDPOINT_URL = N'TCP://LinAGN3.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       SEEDING_MODE = AUTOMATIC,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN1.FullyQualified.Name', 'LinAGN2.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL = N'TCP://LinAGN3.FullyQualified.Name:1433'))
    LISTENER '<ListenerName>' (WITH IP = ('<IPAddress>', '<SubnetMask>'), Port = 1433);
    
    GO
    ```
    
    Quelques points à noter concernant cette configuration :
    
    - *AGName* est le nom du groupe de disponibilité.
    - *DBName* est le nom de la base de données qui est utilisée avec le groupe de disponibilité. Il peut également être une liste de noms séparés par des virgules.
    - *ListenerName* est un nom qui est différent de celle des serveurs/nœuds sous-jacents. Il sera inscrit dans DNS avec *IPAddress*.
    - *IPAddress* est une adresse IP qui est associée avec *ListenerName*. Il est également unique et pas le même que les serveurs/nœuds. Les applications et les utilisateurs finaux utilisent soit *ListenerName* ou *IPAddress* pour se connecter au groupe de disponibilité.
    - *Masque de sous-réseau* est le masque de sous-réseau *IPAddress*; par exemple, 255.255.255.0.

2.  Dans une fenêtre de requête connectée à l’autre réplica, exécutez la commande suivante pour joindre le réplica au groupe de disponibilité et de lancer le processus d’amorçage du site principal vers le réplica secondaire.
    
    ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
    
    GO
    
    ALTER AVAILABILITY GROUP [<AGName>] GRANT CREATE ANY DATABASE;
    
    GO
    ```
    
3.  Répétez l’étape 2 pour le troisième réplica.

#### <a name="example-three---two-replicas-with-read-only-routing-none-cluster-type"></a>Réplicas de trois-le deuxième exemple avec le routage en lecture seule (aucun type de cluster)

Cet exemple illustre la création d’une configuration de deux réplicas à l’aide d’un type de cluster aucun. Il est utilisé pour le scénario de mise à l’échelle lecture où aucun basculement n’est attendue. Cette opération crée l’écouteur est en fait le réplica principal, ainsi que le routage en lecture seule, à l’aide de la fonctionnalité de tourniquet (Round Robin).

1.  Exécuter sur le nœud qui sera le réplica principal contenant la copie en lecture/écriture complet des bases de données. Cet exemple utilise l’amorçage automatique.

    ```SQL
    CREATE AVAILABILITY GROUP [<AGName>]
    WITH (CLUSTER_TYPE = NONE)
    FOR DATABASE <DBName>
    REPLICA ON N'LinAGN1'
    WITH (
       ENDPOINT_URL = N'TCP://LinAGN1.FullyQualified.Name: <PortOfEndpoint>',
       FAILOVER_MODE = MANUAL,
       AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN1.FullyQualified.Name'.'LinAGN2.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL = N'TCP://LinAGN1.FullyQualified.Name:<PortOfInstance>'));
    N'LinAGN2' WITH (
       ENDPOINT_URL = N'TCP://LinAGN2.FullyQualified.Name:<PortOfEndpoint>',
       FAILOVER_MODE = MANUAL,
       SEEDING_MODE = AUTOMATIC,
       AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN1.FullyQualified.Name', 'LinAGN2.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL =N'TCP://LinAGN2.FullyQualified.Name:<PortOfInstance>'));
    LISTENER '<ListenerName>' (WITH IP = ('<PrimaryReplicaIPAddress>', '<SubnetMask>'), Port = <PortOfListener>);
    
    GO
    ```
    
    Où
    - *AGName* est le nom du groupe de disponibilité.
    - *DBName* est le nom de la base de données qui est utilisée avec le groupe de disponibilité. Il peut également être une liste de noms séparés par des virgules.
    - *PortOfEndpoint* est le numéro de port utilisé par le point de terminaison créé.
    - *PortOfInstance* est le numéro de port utilisé par l’instance de [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)].
    - *ListenerName* est un nom qui est différente de celle des réplicas sous-jacent, mais ne sera pas réellement servir.
    - *PrimaryReplicaIPAddress* est l’adresse IP du réplica principal.
    - *Masque de sous-réseau* est le masque de sous-réseau *IPAddress*. Par exemple, 255.255.255.0.
    
2.  Joignez le réplica secondaire au groupe de disponibilité et de lancer l’amorçage automatique.
    
    ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = NONE);
    
    GO
    
    ALTER AVAILABILITY GROUP [<AGName>] GRANT CREATE ANY DATABASE;
    
    GO
    ```

## <a name="create-the-includessnoversion-mdincludesssnoversion-mdmd-login-and-permissions-for-pacemaker"></a>Créer le [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] connexion et des autorisations pour Pacemaker

Un cluster de haute disponibilité de Pacemaker sous-jacent [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] sur Linux a besoin d’accéder à la [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] instance, ainsi que des autorisations sur le groupe de disponibilité lui-même. Les étapes suivantes créent la connexion et les autorisations associées, ainsi qu’un fichier qui indique à Pacemaker comment se connecter à [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)].

1.  Dans une fenêtre de requête connectée vers le premier réplica, exécutez la commande suivante :

    ```SQL
    CREATE LOGIN PMLogin WITH PASSWORD '<StrongPassword>';
    
    GO
    
    GRANT VIEW SERVER STATE TO PMLogin;
    
    GO
    
    GRANT ALTER, CONTROL, VIEW DEFINITION ON AVAILABILITY GROUP::<AGThatWasCreated> TO PMLogin;
    
    GO
    ```
    
2.  Sur le nœud 1, entrez la commande 
    ```bash
    sudo emacs /var/opt/mssql/secrets/passwd
    ```
    
    Ceci ouvrira l’éditeur Emacs.
    
3.  Entrez les deux lignes suivantes dans l’éditeur :

    ```
    PMLogin
    <StrongPassword>
    ```
    
4.  Maintenez la touche CTRL enfoncée et appuyez sur la touche X, puis C pour quitter et enregistrer le fichier.

5.  Execute 
    ```bash
    sudo chmod 400 /var/opt/mssql/secrets/passwd
    ```
    
    Pour verrouiller le fichier.

6.  Répétez les étapes 1 à 5 sur les autres serveurs qui serviront de réplicas.

## <a name="create-the-availability-group-resources-in-the-pacemaker-cluster-external-only"></a>Créer des ressources du groupe de la disponibilité dans le cluster Pacemaker (externes uniquement)

Après une mise à disposition le groupe est créé dans [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], les ressources correspondantes doivent être créés dans Pacemaker, lorsqu’un type de cluster externe est spécifié. Il existe deux ressources associées à un groupe de disponibilité : le groupe de disponibilité et une adresse IP. Configuration de la ressource d’adresse IP est facultative si vous n’utilisez pas la fonctionnalité de l’écouteur, mais il êtes recommandé.

La ressource de groupe de disponibilité est créée est un type spécial de ressource appelé un clone. La ressource de groupe de disponibilité a essentiellement les copies sur chaque nœud et il existe une ressource de contrôle appelée principal. Le maître est associé avec le serveur qui héberge le réplica principal. Les réplicas secondaires (standard ou mode configuration seule) sont considérés comme des subordonnés et peut être promus au maître dans un basculement.

1.  Créer la ressource de groupe de disponibilité avec la syntaxe suivante :

    **Red Hat Enterprise Linux (RHEL) et Ubuntu**
    
    ```bash
    sudo pcs resource create <NameForAGResource> ocf:mssql:ag ag_name=<AGName> meta failure-timeout=30s --master meta notify=true
    ```

    >[!NOTE]
    >Sur RHEL 7.4, vous pouvez rencontrer un avertissement à l’aide de--master. Pour éviter cela, utilisez `sudo pcs resource create <NameForAGResource> ocf:mssql:ag ag_name=<AGName> meta failover-timeout=30s master notify=true`
   
    **SUSE Linux Enterprise Server (SLES)**
    
    ```bash
    primitive <NameForAGResource> \
    ocf:mssql:ag \
    params ag_name="<AGName>" \
    meta failure-timeout=60s \
    op start timeout=60s \
    op stop timeout=60s \
    op promote timeout=60s \
    op demote timeout=10s \
    op monitor timeout=60s interval=10s \
    op monitor timeout=60s interval=11s role="Master" \
    op monitor timeout=60s interval=12s role="Slave" \
    op notify timeout=60s
    ms ms-ag_cluster <NameForAGResource> \
    meta master-max="1" master-node-max="1" clone-max="3" \
    clone-node-max="1" notify="true" \
    commit
    ```
    
    où *NameForAGResource* est le nom unique donné à cette ressource de cluster pour le groupe de disponibilité, et *AGName* est le nom du groupe de disponibilité qui a été créé.
 
2.  Créer la ressource d’adresse IP pour le groupe de disponibilité qui sera associé à la fonctionnalité de l’écouteur.

    **RHEL et Ubuntu**
    
    ```bash
    sudo pcs resource create <NameForIPResource> ocf:heartbeat:IPaddr2 ip=<IPAddress> cidr_netmask=<Netmask>
    ```

    **SLES**
    
    ```bash
    crm configure \
    primitive <NameForIPResource> \
       ocf:heartbeat:IPaddr2 \
       params ip=<IPAddress> \
          cidr_netmask=<Netmask>
    ```
    
    où *NameForIPResource* est le nom unique pour la ressource d’adresse IP, et *IPAddress* est l’adresse IP statique affectée à la ressource. Sur SLES, vous devez également fournir le masque de réseau. Par exemple, 255.255.255.0 posséderait la valeur 24 pour *masque réseau.*
    
3.  Pour vous assurer que l’adresse IP et la ressource de groupe de disponibilité sont en cours d’exécution sur le même nœud, une contrainte de colocalisation doit être configurée.

    **RHEL et Ubuntu**
    
    ```bash
    sudo pcs constraint colocation add <NameForIPResource> <NameForAGResource>-master INFINITY with-rsc-role=Master
    ```

    **SLES**
    
    ```bash
    crm configure <NameForConstraint> inf: \
    <NameForIPResource> <NameForAGResource>:Master 
    commit
    ```
    
    où *NameForIPResource* est le nom de la ressource IP, *NameForAGResource* est le nom de la ressource de groupe de disponibilité et sur SLES, *NameForConstraint* est le nom de la contrainte.

4.  Créer un contrainte pour s’assurer que la ressource de groupe de disponibilité est disponible et en cours d’exécution avant l’adresse IP. Tandis que la contrainte de colocalisation implique une contrainte de classement, il met en œuvre il.

    **RHEL et Ubuntu**
    
    ```bash
    sudo pcs constraint order promote <NameForAGResource>-master then start <NameForIPResource>
    ```
    
    **SLES**
    
    ```bash
    crm configure \
    order <NameForConstraint> inf: <NameForAGResource>:promote <NameForIPResource>:start
    commit
    ```
    
    où *NameForIPResource* est le nom de la ressource IP, *NameForAGResource* est le nom de la ressource de groupe de disponibilité et sur SLES, *NameForConstraint* est le nom de la contrainte.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à créer et configurer un groupe de disponibilité pour [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] sur Linux. Vous avez appris à :
> [!div class="checklist"]
> * Activer les groupes de disponibilité.
> * Points de terminaison de créer le groupe de disponibilité et certificats.
> * Utiliser [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] (SSMS) ou Transact-SQL pour créer un groupe de disponibilité.
> * Créer la connexion [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] et les autorisations pour Pacemaker.
> * Créez des ressources de groupe de disponibilité dans un cluster Pacemaker.

Pour la plupart des tâches d’administration de groupe de disponibilité, y compris les mises à niveau et le basculement, consultez :

> [!div class="nextstepaction"]
> [Exploiter le groupe de disponibilité de haute disponibilité pour SQL Server sur Linux](sql-server-linux-availability-group-failover-ha.md)


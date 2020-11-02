---
title: Configurer le groupe de disponibilité Always On SQL Server sur Windows et Linux
description: Découvrez comment créer un groupe de disponibilité Always On (AG) SQL Server avec un réplica sur un serveur Windows et l’autre réplica sur un serveur Linux.
author: VanMSFT
ms.author: vanto
ms.reviewer: vanto
ms.date: 01/31/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ''
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 3800029fb04f058f6f2a0f00ed3f859d1385782e
ms.sourcegitcommit: 67befbf7435f256e766bbce6c1de57799e1db9ad
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92523884"
---
# <a name="configure-sql-server-always-on-availability-group-on-windows-and-linux-cross-platform"></a>Configurer le groupe de disponibilité Always On SQL Server sur Windows et Linux (multiplateforme)

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/applies-to-version/sqlserver2017.md)]

Cet article explique les étapes permettant de créer un groupe de disponibilité Always On avec un réplica sur un serveur Windows et l’autre réplica sur un serveur Linux. Cette configuration est multiplateforme, car les réplicas se trouvent sur des systèmes d’exploitation différents. Utilisez cette configuration pour la migration d’une plateforme vers l’autre ou la récupération d’urgence (DR). Cette configuration ne prend pas en charge la haute disponibilité, car il n’existe aucune solution de cluster pour gérer une configuration multiplateforme. 

![Aucun hybride](./media/sql-server-linux-availability-group-overview/image1.png)

Avant de continuer, vous devez être familiarisé avec l’installation et la configuration des instances sur Windows et Linux. 

## <a name="scenario"></a>Scénario

Dans ce scénario, deux serveurs se trouvent sur des systèmes d’exploitation différents. Windows Server 2016 nommé `WinSQLInstance` héberge le réplica principal. Un serveur Linux nommé `LinuxSQLInstance` héberge le réplica secondaire.

## <a name="configure-the-ag"></a>Configurer le groupe de disponibilité 

Les étapes de création du groupe de disponibilité sont les mêmes que celles permettant de créer un groupe de disponibilité pour les charges de travail avec échelle de lecture. Le type de cluster AG est AUCUN, car il n’existe aucun gestionnaire de clusters. 

   >[!NOTE]
   >Pour les scripts de cet article, les crochets pointus `<` et `>` identifient les valeurs que vous devez remplacer pour votre environnement. Les crochets pointus ne sont pas requis pour les scripts. 

1. Installez SQL Server 2017 sur Windows Server 2016, activez les groupes de disponibilité Always On à partir de Gestionnaire de configuration SQL Server et définissez l’authentification en mode mixte. 

   >[!TIP]
   >Si vous validez cette solution dans Azure, placez les deux serveurs dans le même groupe à haute disponibilité pour vous assurer qu’ils sont séparés dans le centre de données. 

   **Activer les groupes de disponibilité**

   Pour obtenir des instructions, consultez [Activer et désactiver les groupes de disponibilité Always On (SQL Server)](../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md).

   ![Activer les groupes de disponibilité](./media/sql-server-linux-availability-group-cross-platform/1-sqlserver-configuration-manager.png)

   Le Gestionnaire de configuration SQL Server remarque que l’ordinateur n’est pas un nœud dans un cluster de basculement. 

   Après avoir activé les groupes de disponibilité, redémarrez SQL Server.

   **Définir l’authentification en mode mixte**

   Pour obtenir des instructions, consultez [Modifier le mode d’authentification du serveur](../database-engine/configure-windows/change-server-authentication-mode.md#change-authentication-mode-with-ssms).

1. installez SQL Server 2017 sur Linux. Pour obtenir des instructions, consultez [Installer SQL Server](sql-server-linux-setup.md). Activez `hadr` via mssql-conf.

   Pour activer `hadr` via mssql-conf à partir d’une invite de Shell, émettez la commande suivante :

   ```bash
   sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled 1
   ```

   Une fois que vous avez activé `hadr`, redémarrez l’instance.  

   L’image suivante affiche cette étape complète.

   ![Capture d’écran d’une fenêtre Git Bash montrant la commande.](./media/sql-server-linux-availability-group-cross-platform/2-sqlserver-linux-set-hadr.png)

1. Configurez le fichier hôtes sur les deux serveurs ou enregistrez les noms de serveurs avec DNS.

1. Ouvrez les ports de pare-feu pour TPC 1433 et 5022 sur Windows et Linux.

1. Sur le réplica principal, créez une connexion à la base de données et un mot de passe.

   ```sql
   CREATE LOGIN dbm_login WITH PASSWORD = '<C0m9L3xP@55w0rd!>';
   CREATE USER dbm_user FOR LOGIN dbm_login;
   GO
   ```

1. Sur le réplica principal, créez une clé principale et un certificat, puis sauvegardez le certificat avec une clé privée.

   ```sql
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<C0m9L3xP@55w0rd!>';
   CREATE CERTIFICATE dbm_certificate WITH SUBJECT = 'dbm';
   BACKUP CERTIFICATE dbm_certificate
   TO FILE = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.cer'
   WITH PRIVATE KEY (
           FILE = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\DATA\dbm_certificate.pvk',
           ENCRYPTION BY PASSWORD = '<C0m9L3xP@55w0rd!>'
       );
   GO
   ```

1. Copiez le certificat et la clé privée sur le serveur Linux (réplica secondaire) à l’adresse `/var/opt/mssql/data`. Vous pouvez utiliser `pscp` pour copier les fichiers sur le serveur Linux. 

1. Définissez le groupe et la propriété de la clé privée et du certificat sur `mssql:mssql`.

   Le script suivant définit le groupe et la propriété des fichiers. 

   ```bash
   sudo chown mssql:mssql /var/opt/mssql/data/dbm_certificate.pvk
   sudo chown mssql:mssql /var/opt/mssql/data/dbm_certificate.cer
   ```

   Dans le diagramme suivant, la propriété et le groupe sont définis correctement pour le certificat et la clé.

   ![Capture d’écran d’une fenêtre Git Bash montrant .cer et .pvk dans le dossier /var/opt/mssql/data.](./media/sql-server-linux-availability-group-cross-platform/3-cert-key-owner-group.png)


1. Sur le réplica secondaire, créez une connexion à la base de données et un mot de passe, puis créez une clé principale.

   ```sql
   CREATE LOGIN dbm_login WITH PASSWORD = '<C0m9L3xP@55w0rd!>';
   CREATE USER dbm_user FOR LOGIN dbm_login;
   GO
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<M@st3rKeyP@55w0rD!>'
   GO
   ```

1. Sur le réplica secondaire, restaurez le certificat que vous avez copié sur `/var/opt/mssql/data`. 

   ```sql
   CREATE CERTIFICATE dbm_certificate   
       AUTHORIZATION dbm_user
       FROM FILE = '/var/opt/mssql/data/dbm_certificate.cer'
       WITH PRIVATE KEY (
       FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
       DECRYPTION BY PASSWORD = '<C0m9L3xP@55w0rd!>'
   )
   GO
   ```

1. Sur le réplica principal, créez un point de terminaison.

   ```sql
   CREATE ENDPOINT [Hadr_endpoint]
       AS TCP (LISTENER_IP = (0.0.0.0), LISTENER_PORT = 5022)
       FOR DATA_MIRRORING (
           ROLE = ALL,
           AUTHENTICATION = CERTIFICATE dbm_certificate,
           ENCRYPTION = REQUIRED ALGORITHM AES
           );
   ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
   GRANT CONNECT ON ENDPOINT::[Hadr_endpoint] TO [dbm_login]
   GO
   ```

   >[!IMPORTANT]
   >Le pare-feu doit être ouvert pour le port TCP de l’écouteur. Dans le script précédent, le port est 5022. Utilisez n’importe quel port TCP disponible. 

1. Sur le réplica secondaire, créez le point de terminaison. Répétez le script précédent sur le réplica secondaire pour créer le point de terminaison. 

1. Sur le réplica principal, créez un groupe de disponibilité avec `CLUSTER_TYPE = NONE`. L’exemple de script utilise `SEEDING_MODE = AUTOMATIC` pour créer le groupe de disponibilité. 

   >[!NOTE]
   >Lorsque l’instance Windows de SQL Server utilise des chemins d’accès différents pour les données et les fichiers journaux, l’amorçage automatique échoue à l’instance Linux de SQL Server, car ces chemins d’accès n’existent pas sur le réplica secondaire. Pour utiliser le script suivant pour un groupe de disponibilité multiplateforme, la base de données requiert le même chemin d’accès pour les données et les fichiers journaux sur le serveur Windows. Vous pouvez également mettre à jour le script pour définir `SEEDING_MODE = MANUAL`, puis sauvegarder et restaurer la base de données avec `NORECOVERY` pour amorcer la base de données. 
   >
   >Ce comportement s’applique aux images de la place de marché Azure. 
   >
   >Pour plus d’informations sur l’amorçage automatique, consultez [Amorçage automatique - Disposition du disque](../database-engine/availability-groups/windows/automatic-seeding-secondary-replicas.md#disklayout). 

   Avant d’exécuter le script, mettez à jour les valeurs de vos groupes de disponibilité.

      * Remplacez `<WinSQLInstance>` par le nom du serveur de l’instance du réplica principal.

      * Remplacez `<LinuxSQLInstance>` par le nom du serveur de l’instance du réplica secondaire. 

   Pour créer le groupe de disponibilité, mettez à jour les valeurs et exécutez le script sur le réplica principal.  

   ```sql
   CREATE AVAILABILITY GROUP [ag1]
       WITH (CLUSTER_TYPE = NONE)
       FOR REPLICA ON
           N'<WinSQLInstance>' 
        WITH (
           ENDPOINT_URL = N'tcp://<WinSQLInstance>:5022',
           AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            SEEDING_MODE = AUTOMATIC,
            FAILOVER_MODE = MANUAL,
           SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            ),
           N'<LinuxSQLInstance>' 
       WITH (
            ENDPOINT_URL = N'tcp://<LinuxSQLInstance>:5022',
           AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
           SEEDING_MODE = AUTOMATIC,
           FAILOVER_MODE = MANUAL,
           SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
           )
   GO
   ```
   
   Pour plus d’informations, consultez [CREATE AVAILABILITY GROUP (Transact-SQL)](../t-sql/statements/create-availability-group-transact-sql.md).

1. Sur le réplica secondaire, joignez le groupe de disponibilité.

   ```sql
   ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE)
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE
   GO
   ```

1. Créez une base de données pour le groupe de disponibilité. Les étapes de l’exemple utilisent une base de données nommée `<TestDB>`. Si vous utilisez l’amorçage automatique, définissez le même chemin d’accès pour les données et les fichiers journaux. 

   Avant d’exécuter le script, mettez à jour les valeurs de votre base de données.

      * Remplacez `<TestDB>` par le nom de votre base de données.

      * Remplacez `<F:\Path>` par le chemin d’accès de votre base de données et de vos fichiers journaux. Utilisez le même chemin d’accès pour la base de données et les fichiers journaux. 

      Vous pouvez également utiliser les chemins d’accès par défaut. 

    Pour créer votre base de données, exécutez le script. 

   ```sql
   CREATE DATABASE [<TestDB>]
      CONTAINMENT = NONE
     ON  PRIMARY ( NAME = N'<TestDB>', FILENAME = N'<F:\Path>\<TestDB>.mdf')
     LOG ON ( NAME = N'<TestDB>_log', FILENAME = N'<F:\Path>\<TestDB>_log.ldf')
   GO
   ```

1. Prenez une sauvegarde complète de la base de données. 

1. Si vous n’utilisez pas l’amorçage automatique, restaurez la base de données sur le serveur du réplica secondaire (Linux). [Migrez une base de données SQL Server de Windows vers Linux à l’aide de la sauvegarde et de la restauration](sql-server-linux-migrate-restore-database.md). Restaurez la base de données `WITH NORECOVERY` sur le réplica secondaire. 

1. Ajoutez la base de données au groupe de disponibilité. Mettez à jour l’exemple de script. Remplacez `<TestDB>` par le nom de votre base de données. Sur le réplica principal, exécutez la requête SQL pour ajouter la base de données au groupe de disponibilité.

   ```sql
   ALTER AG [ag1] ADD DATABASE <TestDB>
   GO
   ```

1. Vérifiez que la base de données est alimentée sur le réplica secondaire. 

## <a name="fail-over-the-primary-replica"></a>Basculer le réplica principal

[!INCLUDE[Force failover](../includes/ss-force-failover-read-scale-out.md)]

Cet article a examiné les étapes de création d’un groupe de disponibilité multiplateforme pour prendre en charge les charges de travail de migration ou de lecture-échelle. Il peut être utilisé pour la récupération d’urgence manuelle. Il a également expliqué comment basculer le groupe de disponibilité. Un groupe de disponibilité multiplateforme utilise un type de cluster `NONE` et ne prend pas en charge la haute disponibilité, car il n’existe pas d’outil de cluster multiplateforme. 

## <a name="next-steps"></a>Étapes suivantes

[Vue d’ensemble des groupes de disponibilité Always On](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)

[Principes de base de la disponibilité SQL Server pour les déploiements Linux](sql-server-linux-ha-basics.md)

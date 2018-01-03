---
title: "Mise à jour - SQL Server sur Linux docs | Documents Microsoft"
description: "Extraits de l’affichage de contenu mis à jour pour obtenir une documentation récemment modifié, pour Microsoft SQL Server sur Linux."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: rothja
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: linux-sql
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 12/02/2017
ms.author: genemi
ms.openlocfilehash: 030f30580b0ddb02da2a67990d0c58acf15236c9
ms.sourcegitcommit: 73043fe1ac5d60b67e33b44053c0a7733b98bc3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="new-and-recently-updated-sql-server-on-linux-docs"></a>Nouveau et récemment mis à jour : SQL Server sur Linux docs



Presque tous les jours, Microsoft met à jour certains de ses articles sur son site web de documentation [Docs.Microsoft.com](http://docs.microsoft.com/). Cet article contient des extraits d’articles récemment mis à jour. Des liens vers de nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme qui est réexécuté régulièrement. Un extrait peut parfois apparaître avec une mise en forme imparfaite ou au format Markdown de l’article source. Les images ne sont jamais affichées ici.

Les mises à jour récentes sont signalées pour la plage de dates et le sujet suivants :



- *Période des mises à jour :* &nbsp; **28-09-2017** &nbsp; au &nbsp; **02-12-2017**
- *Zone de sujet :* &nbsp; **Microsoft SQL Server sur Linux**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nouveaux articles créés récemment

Les liens suivants renvoient aux nouveaux articles ajoutés récemment.


1. [Exécutez le 2017 du serveur SQL dans le cloud](quickstart-install-connect-clouds.md)
2. [Modification des référentiels à partir du référentiel d’aperçu dans le référentiel GA](sql-server-linux-change-repo.md)
3. [Meilleures pratiques de performance et des instructions de configuration pour 2017 du serveur SQL sur Linux](sql-server-linux-performance-best-practices.md)
4. [Instances de Cluster de basculement, SQL Server sur Linux](sql-server-linux-shared-disk-cluster-concepts.md)
5. [Configurer l’instance de cluster de basculement - iSCSI - SQL Server sur Linux](sql-server-linux-shared-disk-cluster-configure-iscsi.md)
6. [Configuration d’instance de cluster de basculement - NFS - SQL Server sur Linux](sql-server-linux-shared-disk-cluster-configure-nfs.md)
7. [Configuration d’instance de cluster de basculement - SMB - SQL Server sur Linux](sql-server-linux-shared-disk-cluster-configure-smb.md)
8. [Fonctionnement de SQL Server sur Linux - instance de cluster de basculement](sql-server-linux-shared-disk-cluster-operate.md)
9. [Limitations et problèmes connus pour SSIS sur Linux](sql-server-linux-ssis-known-issues.md)
10. [Restaurer une base de données SQL Server dans un conteneur Linux Docker](tutorial-restore-backup-in-sql-server-container.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits des mises à jour collectés dans des articles qui ont récemment fait l’objet d’une mise à jour importante.

Les extraits affichés ici apparaissent séparés de leur contexte sémantique propre. Un extrait est parfois séparé de la syntaxe Markdown importante qui l’entoure dans l’article. Ces extraits sont donc donnés à titre indicatif uniquement. Les extraits vous permettent seulement de savoir si les articles correspondants vont vous intéresser et si oui, de cliquer dessus pour les consulter.

Pour cela et pour d’autres raisons, ne copiez pas le code de ces extraits et ne prenez pas à la lettre les extraits de texte. Consultez plutôt l’article.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’articles mis à jour récemment

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriés dans la section des extraits.

1. [Exécuter l’image de SQL Server 2017 conteneur avec Docker](#TitleNum_1)
2. [Configurer le groupe de disponibilité Always On pour SQL Server sur Linux](#TitleNum_2)
3. [Haute disponibilité et protection des données pour les configurations de groupe de disponibilité](#TitleNum_3)
4. [Configurer SQL Server 2017 les images de conteneur sur Docker](#TitleNum_4)
5. [Chiffrement des connexions à SQL Server sur Linux](#TitleNum_5)
6. [Créer et exécuter des travaux de l’Agent SQL Server sur Linux](#TitleNum_6)
7. [Aide à l’installation de SQL Server sur Linux](#TitleNum_7)
8. [Configurer l’instance de cluster de basculement - SQL Server sur Linux (RHEL)](#TitleNum_8)
9. [Résoudre les problèmes de SQL Server sur Linux](#TitleNum_9)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-run-the-sql-server-2017-container-image-with-dockerquickstart-install-connect-dockermd"></a>1. &nbsp;[Exécuter l’image de SQL Server 2017 conteneur avec Docker](quickstart-install-connect-docker.md)

*Mise à jour : 30/11/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Suivant](#TitleNum_2))

<!-- Source markdown line 261.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 2aaf953c2f1fb675b1304186108fbef1eebf6f8f f7cd42bb320a8892a5ec63ce999186438097636a  (PR=4150  ,  Filename=quickstart-install-connect-docker.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



**Supprimer le conteneur de votre**


Si vous souhaitez supprimer le conteneur de SQL Server utilisé dans ce didacticiel, exécutez les commandes suivantes :

```
sudo docker stop sql1
sudo docker rm sql1
```

```
docker stop sql1
docker rm sql1
```

> [!WARNING]
> L’arrêt et la suppression d’un conteneur définitivement supprime toutes les données de SQL Server dans le conteneur. Si vous avez besoin de conserver vos données, [créer et copier un fichier de sauvegarde en dehors de la container--tutorial-restore-backup-in-sql-server-container.md) ou utilisez une [conteneur persistance des données technique--sql-server-linux-configure-docker.md#persist).




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-configure-always-on-availability-group-for-sql-server-on-linuxsql-server-linux-availability-group-configure-hamd"></a>2. &nbsp;[Configurer toujours sur le groupe de disponibilité pour SQL Server sur Linux](sql-server-linux-availability-group-configure-ha.md)

*Mise à jour : 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_1) | [suivant](#TitleNum_3))

<!-- Source markdown line 129.  ms.author= mikeray.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 3c7e6bc862e5b062a855918efbeee5fe748b7236 6900c9a30ce04ce54e7aaa270ef7d276c18f9afd  (PR=4150  ,  Filename=sql-server-linux-availability-group-configure-ha.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



- Créer le groupe de disponibilité avec deux réplicas synchrones et un réplica de la configuration :

   >[!IMPORTANT]
   >Cette architecture permet à n’importe quelle édition de SQL Server pour héberger le réplica de tiers. Par exemple, le troisième réplica peut être hébergé sur SQL Server Enterprise Edition. Sur l’édition entreprise, le type de point de terminaison valide uniquement est `WITNESS`.

```sql
   CREATE AVAILABILITY GROUP [ag1]
      WITH (CLUSTER_TYPE = EXTERNAL)
      FOR REPLICA ON
       N'**<node1>**' WITH (
          ENDPOINT_URL = N'tcp://**<node1>**:**<5022>**',
          AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
          FAILOVER_MODE = EXTERNAL,
          SEEDING_MODE = AUTOMATIC
          ),
       N'**<node2>**' WITH (
          ENDPOINT_URL = N'tcp://**<node2>**:**<5022>**',
          AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
          FAILOVER_MODE = EXTERNAL,
          SEEDING_MODE = AUTOMATIC
          ),
       N'**<node3>**' WITH (
          ENDPOINT_URL = N'tcp://**<node3>**:**<5022>**',
          AVAILABILITY_MODE = CONFIGURATION_ONLY
          );
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-high-availability-and-data-protection-for-availability-group-configurationssql-server-linux-availability-group-hamd"></a>3. &nbsp;[Haute disponibilité et protection des données pour les configurations de groupe de disponibilité](sql-server-linux-availability-group-ha.md)

*Mise à jour : 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_2) | [suivant](#TitleNum_4))

<!-- Source markdown line 106.  ms.author= "mikeray".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 e6bee794ce19f1ed62298b4a0cce7207550f1595 b64726cd6e91721850721786d26c170d59fc320a  (PR=4150  ,  Filename=sql-server-linux-availability-group-ha.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



La valeur par défaut `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` est 0. Le tableau suivant décrit le comportement de la disponibilité.

| |Haute disponibilité & </br> protection de données | Protection des données
|:---|---|---
|`REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT=`|0 <sup>*</sup>| 1
|Indisponibilité du réplica principal | Basculement automatique. Nouveau réplica principal est R / w. | Basculement automatique. Nouveau réplica principal n’est pas disponible pour les transactions utilisateur.
|Panne du réplica secondaire | Primaire est en lecture/écriture, exécution exposée à des pertes de données (si principal échoue et ne peut pas être récupérée). Aucun basculement automatique si principal n’échoue également. | Principal n’est pas disponible pour les transactions utilisateur. Aucun réplica de basculer vers si principal n’échoue également.
|Panne de réplica configuration uniquement | Principal est R / w. Aucun basculement automatique si principal n’échoue également. | Principal est R / w. Aucun basculement automatique si principal n’échoue également.
|Base de données secondaire synchrone + configuration uniquement panne de réplica| Principal n’est pas disponible pour les transactions utilisateur. Aucun basculement automatique. | Principal n’est pas disponible pour les transactions utilisateur. Aucun réplica pour le basculement se principal échoue également.
<sup>*</sup>Par défaut

>[!NOTE]
>L’instance de SQL Server qui héberge le réplica uniquement configuration peut également héberger d’autres bases de données. Il peut également être inclus en tant qu’une base de données uniquement de configuration pour plus d’un groupe de disponibilité.

**Spécifications**


* Tous les réplicas dans un groupe de disponibilité avec un seul réplica de configuration doivent être SQL Server 2017 CU 1 ou version ultérieure.
* N’importe quelle édition de SQL Server peut héberger un réplica seule configuration, y compris SQL Server Express.
* Le groupe de disponibilité a besoin d’au moins un réplica secondaire - outre le réplica principal.
* Réplicas uniquement de configuration ne sont pas dans le nombre maximal de réplicas de chaque instance de SQL Server. Édition standard de SQL Server permet de configurer jusqu'à trois réplicas, SQL Server Enterprise Edition permet jusqu'à 9.



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-configure-sql-server-2017-container-images-on-dockersql-server-linux-configure-dockermd"></a>4. &nbsp;[Images de conteneur de configuration de SQL Server 2017 sur Docker](sql-server-linux-configure-docker.md)

*Mise à jour : 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_3) | [suivant](#TitleNum_5))

<!-- Source markdown line 34.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c759fb88ae8d654414202f28c5fc58dfd02581bf fd270118f2f4608fceaf563fc143951b41097bdb  (PR=4150  ,  Filename=sql-server-linux-configure-docker.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



Cette rubrique de configuration fournit des scénarios d’utilisation supplémentaires dans les sections ci-dessous.

**<a id="production"></a>Exécuter des images de conteneur de production**


Démarrage rapide dans la section précédente s’exécute à l’édition développeur gratuite de SQL Server à partir du Hub d’ancrage. La plupart des informations s’applique toujours si vous souhaitez exécuter des images de conteneur, tels que les éditions Enterprise, Standard ou Web de production. Toutefois, il existe des quelques différences sont décrites ici.

- Vous pouvez uniquement utiliser SQL Server dans un environnement de production, si vous avez une licence valide. Vous pouvez obtenir une licence de production de SQL Server Express gratuite [ici](https://go.microsoft.com/fwlink/?linkid=857693). Les licences de SQL Server Standard et Enterprise Edition sont disponibles via [Microsoft Volume Licensing](https://www.microsoft.com/Licensing/licensing-programs/licensing-programs.aspx).

- Images de conteneur de SQL Server de production doivent être extraites de [Docker magasin](https://store.docker.com). Si vous n’avez pas encore, créez un compte sur le magasin de Docker.

- L’image de conteneur de développeur sur le magasin de Docker peut être configuré pour exécuter les ainsi les éditions de production. Pour exécuter des versions de production, utilisez les étapes suivantes :

   1. Tout d’abord, vous connecter à votre id de docker à partir de la ligne de commande.

```
      docker login
```

   1. Ensuite, vous devez obtenir le développeur libre image de conteneur sur Docker magasin. Accédez à [https://store.docker.com/images/mssql-server-linux](https://store.docker.com/images/mssql-server-linux), cliquez sur **passer à l’extraction**, suivez les instructions.

   1. Passez en revue la configuration requise et exécuter des procédures dans [démarrage rapide : démarrage rapide-install-se connecter-docker.md). Il existe deux différences. Vous devez extraire l’image **magasin/microsoft/mssql-server-linux :\<-nom de la balise\>**  à partir du magasin de Docker. Et vous devez spécifier votre édition de production avec le **MSSQL_PID** variable d’environnement. L’exemple suivant montre comment exécuter la dernière image de conteneur de SQL Server 2017 pour l’édition Enterprise :



&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-encrypting-connections-to-sql-server-on-linuxsql-server-linux-encrypted-connectionsmd"></a>5. &nbsp;[Chiffrement des connexions à SQL Server sur Linux](sql-server-linux-encrypted-connections.md)

*Mise à jour : 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_4) | [suivant](#TitleNum_6))

<!-- Source markdown line 45.  ms.author= meetb;rickbyh.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 7e3187866df060903e30000d60d673edad46d210 bcb1f2771e6c29b535a30b9f23ac296954509187  (PR=4150  ,  Filename=sql-server-linux-encrypted-connections.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



        sudo chown mssql:mssql mssql.pem mssql.key
        sudo chmod 600 mssql.pem mssql.key
        sudo mv mssql.pem /etc/ssl/certs/
        sudo mv mssql.key /etc/ssl/private/

- **Configurer SQL Server**

        systemctl stop mssql-server
        cat /var/opt/mssql/mssql.conf
        sudo /opt/mssql/bin/mssql-conf set network.tlscert /etc/ssl/certs/mssqlfqdn.pem
        sudo /opt/mssql/bin/mssql-conf set network.tlskey /etc/ssl/private/mssqlfqdn.key
        sudo /opt/mssql/bin/mssql-conf set network.tlsprotocols 1.2
        sudo /opt/mssql/bin/mssql-conf set network.forceencryption 0

- **Inscrire le certificat sur votre ordinateur client (Windows, Linux ou macOS)**

    -   Si vous utilisez un certificat signé d’autorité de certification, vous devez copier le certificat d’autorité de certification (CA) au lieu du certificat de l’utilisateur sur l’ordinateur client.
    -   Si vous utilisez un certificat autosigné simplement copier le fichier .pem dans les dossiers suivants correspondant à la distribution et exécutez les commandes pour leur permettre de

        - **Windows**: importer le fichier .pem en tant que certificat sous utilisateur actuel -> approuvé autorités de certification racine -> certificats
        - **macOS**:

-   **Exemples de chaîne de connexion**

    - **..! NCLURE-NotShown--ssmanstudiofull-md--... /Includes/ssmanstudiofull-MD.MD)]** ! [ SSMS connexion dialog--media/sql-server-linux-encrypted-connections/ssms-encrypt-connection.png « SSMS boîte de dialogue Connexion »)



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-create-and-run-sql-server-agent-jobs-on-linuxsql-server-linux-run-sql-server-agent-jobmd"></a>6. &nbsp;[Création et exécution des travaux de l’Agent SQL Server sur Linux](sql-server-linux-run-sql-server-agent-job.md)

*Mise à jour : 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_5) | [suivant](#TitleNum_7))

<!-- Source markdown line 35.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1598129bb5f98434435d8ad02336a9adf76c7870 6fe3fe7df3a60dbac31f1df59aac9860d293421a  (PR=4150  ,  Filename=sql-server-linux-run-sql-server-agent-job.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



Les conditions préalables suivantes sont requises pour effectuer ce didacticiel :

* Ordinateur Linux avec les conditions préalables suivantes :
  * SQL Server 2017 ([RHEL--quickstart-install-connect-red-hat.md), [SLES : démarrage rapide-install-se connecter-suse.md) ou [Ubuntu : démarrage rapide-install-se connecter-ubuntu.md)) avec les outils de ligne de commande.

Les conditions préalables suivantes sont facultatives :

* Ordinateur Windows avec SSMS :
  * [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) pour les étapes facultatives de SSMS.

**Installer SQL Server Agent**


Pour utiliser l’Agent SQL Server sur Linux, vous devez d’abord installer le **mssql-server-agent** package sur un ordinateur équipé de SQL Server 2017 est installé.

1. Installer **mssql-server-agent** avec la commande appropriée pour votre système d’exploitation Linux.

   | Plateforme | Commandes d’installation |
   |-----|-----|
   | RHEL | `sudo yum install mssql-server-agent` |
   | SLES | `sudo zypper refresh`<br/>`sudo zypper update mssql-server-agent` |
   | Ubuntu | `sudo apt-get update`<br/>`sudo apt-get install mssql-server-agent` |

1. Redémarrez SQL Server avec la commande suivante :

```
   sudo systemctl restart mssql-server
```

**Créer une base de données exemple**


Procédez comme suit pour créer une base de données exemple nommé **SampleDB**. Cette base de données est utilisé pour le travail de sauvegarde quotidiens.

1. Sur l’ordinateur Linux, ouvrez une session Terminal Server d’un interpréteur de commandes.



&nbsp;

&nbsp;

---

<a name="TitleNum_7"/>

### <a name="7-nbsp-installation-guidance-for-sql-server-on-linuxsql-server-linux-setupmd"></a>7. &nbsp;[Aide à l’installation de SQL Server sur Linux](sql-server-linux-setup.md)

*Mise à jour : 2017-12-01* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_6) | [suivant](#TitleNum_8))

<!-- Source markdown line 125.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 8ba2bf6f9cf4b5f54a6ee0f4d16d4437d5724880 eedddcfb64c6432215f56b74dc91700d9804fce8  (PR=4160  ,  Filename=sql-server-linux-setup.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=085dd05d56afecbb454206ed8402cfbaa597cfbe) -->



**<a id="repositories"></a>Configurer des référentiels de code source**


Lorsque vous installez ou mettez à niveau de SQL Server, vous obtenez la dernière version de SQL Server à partir de votre référentiel de Microsoft.

**Options de dépôt**


Il existe deux principaux types de référentiels pour chaque point de distribution :

- **Les mises à jour cumulative (CU)**: référentiel de la mise à jour Cumulative (CU) contient des packages pour la version de SQL Server de base et tous les correctifs de bogues ou améliorations apportées depuis cette version. Mises à jour cumulatives sont spécifiques à une version release, telles que SQL Server 2017. Ils sont publiés sur une cadence régulière.

- **GDR**: référentiel du GDR contient des packages pour la base version de SQL Server et uniquement les correctifs critiques et les mises à jour de sécurité depuis cette version. Ces mises à jour sont également ajoutés à la prochaine version CU.

Chaque version de CU et correctif logiciel grand public contient le package SQL Server complète et toutes les mises à jour précédentes pour ce référentiel. Mise à jour à partir d’une version GDR vers une version CU prend en charge la modification de votre référentiel configuré pour SQL Server. Vous pouvez également [rétrograder--#rollback) à n’importe quelle version dans votre version principale (ex : 2017). Mise à jour à partir d’une CU version à une version de correctif logiciel grand public n’est pas pris en charge.

**Vérifiez votre référentiel**


Si vous souhaitez vérifier le référentiel est configurée, utilisez les techniques de dépend de la plateforme suivants.

| Plateforme | Procédure |
|-----|-----|
| RHEL | 1. Afficher les fichiers dans le **/etc/yum.repos.d** active :`sudo ls /etc/yum.repos.d`<br/>2. Recherchez le fichier qui configure le répertoire de SQL Server, tels que **mssql-server.repo**.<br/>3. Imprimer le contenu du fichier :`sudo cat /etc/yum.repos.d/mssql-server.repo`<br/>4. Le **nom** propriété est le référentiel.|
| SLES | 1. Exécutez la commande suivante : `sudo zypper info mssql-server`.<br/>2. Le **référentiel** propriété est le référentiel. |
| Ubuntu | 1. Exécutez la commande suivante : `sudo cat /etc/apt/sources.list`.<br/>2. Examinez l’URL du package pour mssql-serveur. |



&nbsp;

&nbsp;

---

<a name="TitleNum_8"/>

### <a name="8-nbsp-configure-failover-cluster-instance---sql-server-on-linux-rhelsql-server-linux-shared-disk-cluster-configuremd"></a>8. &nbsp;[Instance de cluster de basculement configurer - SQL Server sur Linux (RHEL)](sql-server-linux-shared-disk-cluster-configure.md)

*Mise à jour : 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([précédente](#TitleNum_7) | [suivant](#TitleNum_9))

<!-- Source markdown line 25.  ms.author= mikeray.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 308fa1809c80a009f7f15b5ca6917f6b76588c3e 71f18baa320041ff10c94e8c7668e40dff45cac3  (PR=4150  ,  Filename=sql-server-linux-shared-disk-cluster-configure.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



> [!div class="checklist"]
> * Installer et configurer Linux
> * Installer et configurer SQL Server
> * Configurer le fichier hosts
> * Configurer le stockage partagé et déplacer les fichiers de base de données
> * Installer et configurer STIMULATEUR sur chaque nœud de cluster
> * Configurer l’instance de cluster de basculement

Cet article explique comment créer une instance de cluster de basculement (FCI) disque partagé de deux nœuds pour SQL Server. L’article inclut des instructions et des exemples de script pour Red Hat Enterprise Linux (RHEL). Ubuntu distributions sont semblables aux RHEL afin que les exemples de script normalement fonctionnent également sur Ubuntu.

Pour obtenir des informations conceptuelles, consultez [SQL Server Cluster Instance de basculement sur Linux--sql-server-linux-shared-disk-cluster-concepts.md).

**Conditions préalables**


Pour terminer le scénario de bout en bout ci-dessous, vous avez besoin de deux ordinateurs pour déployer le cluster à deux nœuds et un autre serveur pour le stockage. Étapes ci-dessous décrivent la configuration de ces serveurs.

**Installer et configurer Linux**


La première étape consiste à configurer le système d’exploitation sur les nœuds de cluster. Sur chaque nœud du cluster, configurez une distribution linux. Utilisez la distribution et la même version sur les deux nœuds. Utilisez une ou l’autre des distributions suivantes :

* RHEL avec un abonnement valide pour le module complémentaire à haute disponibilité

**Installer et configurer SQL Server**


1. Installer et configurer SQL Server sur les deux nœuds.  Pour obtenir des instructions détaillées, consultez [installation de SQL Server sur Linux--sql-server-linux-setup.md.)
1. Désigner un nœud en tant que principal et l’autre comme secondaire, à des fins de configuration. Utiliser ces termes pour les éléments suivants ce guide.
1. Sur le nœud secondaire, arrêter et désactiver les SQL Server.
    L’exemple suivant arrête et désactive les SQL Server :
```
    sudo systemctl stop mssql-server
    sudo systemctl disable mssql-server
```

    > [!NOTE]
    > At set up time, a Server Master Key is generated for the SQL Server instance and placed at `var/opt/mssql/secrets/machine-key`. On Linux, SQL Server always runs as a local account called mssql. Because it's a local account, its identity isn't shared across nodes. Therefore, you need to copy the encryption key from primary node to each secondary node so each local mssql account can access it to decrypt the Server Master Key.



&nbsp;

&nbsp;

---

<a name="TitleNum_9"/>

### <a name="9-nbsp-troubleshoot-sql-server-on-linuxsql-server-linux-troubleshooting-guidemd"></a>9. &nbsp;[Résoudre les problèmes de SQL Server sur Linux](sql-server-linux-troubleshooting-guide.md)

*Mise à jour : 30/11/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Précédent](#TitleNum_8))

<!-- Source markdown line 125.  ms.author= anshrest.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5f8557a34b38e028ff6e5ac370b6d2d6bf315091 196e56187b57bdd79cc5cdc5e6fce3d41e82af0c  (PR=4150  ,  Filename=sql-server-linux-troubleshooting-guide.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



**Démarrage de SQL Server dans une Configuration minimale ou en Mode mono-utilisateur**


**Démarrage de SQL Server en Mode Configuration minimale**

Cette option est utile lorsqu'une valeur de configuration définie (espace mémoire insuffisant, par exemple) a empêché le serveur de démarrer.

```
   sudo -u mssql /opt/mssql/bin/sqlservr -f
```

**Démarrage de SQL Server en Mode mono-utilisateur**

Dans certaines circonstances, vous devrez peut-être démarrer une instance de SQL Server en mode mono-utilisateur à l’aide de l’option de démarrage -m. Vous pouvez par exemple vouloir modifier les options de configuration du serveur ou rétablir une base de données master ou une autre base de données système endommagées. Par exemple, vous souhaiterez modifier les options de configuration de serveur ou rétablir une base de données master endommagée ou une autre base de données système

Démarrage de SQL Server en Mode mono-utilisateur
```
   sudo -u mssql /opt/mssql/bin/sqlservr -m
```

Démarrage de SQL Server en Mode mono-utilisateur avec SQLCMD
```
   sudo -u mssql /opt/mssql/bin/sqlservr -m SQLCMD
```

> [!WARNING]
>  Démarrez SQL Server sur Linux avec l’utilisateur « mssql » afin d’éviter les problèmes de démarrage futurs. Exemple « sudo -u mssql /opt/mssql/bin/sqlservr [OPTIONS DE DÉMARRAGE] »

Si vous avez commencé par inadvertance de SQL Server avec un autre utilisateur, vous devez modifier la propriété des fichiers de base de données SQL Server à l’utilisateur 'mssql' avant de démarrer SQL Server avec systemd. Par exemple, exécutez la commande suivante pour modifier la propriété de tous les fichiers de base de données sous /var/opt/mssql à l’utilisateur « mssql »,

```
   chown -R mssql:mssql /var/opt/mssql/
```







## <a name="similar-articles"></a>Articles similaires

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

Cette section liste les articles très similaires récemment mis à jour dans d’autres domaines, dans notre dépôt public GitHub.com : [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Zones de sujet avec des articles nouveaux ou mis à jour récemment

- [Nouveaux + Mis à jour (3 + 14) : **Analytique avancée pour SQL** (documentation)](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveaux + Mis à jour (1 + 0) : **Analysis Services pour SQL** (documentation)](../analysis-services/new-updated-analysis-services.md)
- [Nouveaux + Mis à jour (87 + 0) : **Système de la plateforme d’analyse pour SQL** (documentation)](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nouveaux + Mis à jour (5 + 4) : **Connexion à SQL** (documentation)](../connect/new-updated-connect.md)
- [Nouveaux + Mis à jour (0 + 1) : **Moteur de base de données pour SQL** (documentation)](../database-engine/new-updated-database-engine.md)
- [Nouveaux + Mis à jour (2 + 2) : **Integration Services pour SQL** (documentation)](../integration-services/new-updated-integration-services.md)
- [Nouveaux + Mis à jour (10 + 9) : **Linux pour SQL** (documentation)](../linux/new-updated-linux.md)
- [Nouveaux + Mis à jour (2 + 4) : **Bases de données relationnelles pour SQL** (documentation)](../relational-databases/new-updated-relational-databases.md)
- [Nouveaux + Mis à jour (4 + 2) : **Reporting Services pour SQL** (documentation)](../reporting-services/new-updated-reporting-services.md)
- [Nouveaux + Mis à jour (0 + 1) : **Exemples pour SQL** (documentation)](../sample/new-updated-sample.md)
- [Nouveaux + Mis à jour (21 + 0) : **SQL Operations Studio** (documentation)](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nouveaux + Mis à jour (5 + 1) : **Microsoft SQL Server** (documentation)](../sql-server/new-updated-sql-server.md)
- [Nouveaux + Mis à jour (0 + 1) : **SQL Server Data Tools (SSDT)** (documentation)](../ssdt/new-updated-ssdt.md)
- [Nouveaux + Mis à jour (1 + 0) : **Assistant Migration SQL Server (SSMA)** (documentation)](../ssma/new-updated-ssma.md)
- [Nouveaux + Mis à jour (0 + 1) : **SQL Server Management Studio (SSMS)** (documentation)](../ssms/new-updated-ssms.md)
- [Nouveaux + Mis à jour (0 + 2) : **Transact-SQL** (documentation)](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Zones de sujet sans article nouveau ou mis à jour récemment

- [Nouveaux + Mis à jour (0 + 0) : **Data Migration Assistant (DMA) pour SQL** (documentation)](../dma/new-updated-dma.md)
- [Nouveaux + Mis à jour (0 + 0) : **ActiveX Data Objects (ADO) pour SQL** (documentation)](../ado/new-updated-ado.md)
- [Nouveaux + Mis à jour (0 + 0) : **Data Quality Services pour SQL** (documentation)](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Extensions DMX (Data Mining Extensions) pour SQL** (documentation)](../dmx/new-updated-dmx.md)
- [Nouveaux + Mis à jour (0 + 0) : **Master Data Services (MDS) for SQL** (documentation)](../master-data-services/new-updated-master-data-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Expressions MDX (Multidimensional Expressions) pour SQL** (documentation)](../mdx/new-updated-mdx.md)
- [Nouveaux + Mis à jour (0 + 0) : **ODBC (Open Database Connectivity) pour SQL** (documentation)](../odbc/new-updated-odbc.md)
- [Nouveaux + Mis à jour (0 + 0) : **PowerShell pour SQL** (documentation)](../powershell/new-updated-powershell.md)
- [Nouveaux + Mis à jour (0 + 0) : **Outils pour SQL** (documentation)](../tools/new-updated-tools.md)
- [Nouveaux + Mis à jour (0 + 0) : **XQuery pour SQL** (documentation)](../xquery/new-updated-xquery.md)



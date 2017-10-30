---
title: "Configurer l’instance de cluster de basculement - SQL Server sur Linux (RHEL) | Documents Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 08/28/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: 11b7c2e6a782a2e1215a75e746c6def1b42f90a1
ms.contentlocale: fr-fr
ms.lasthandoff: 10/02/2017

---
# <a name="configure-failover-cluster-instance---sql-server-on-linux-rhel"></a>Configurer l’instance de cluster de basculement - SQL Server sur Linux (RHEL)

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Une instance de cluster de basculement de disque partagé de deux nœuds SQL Server fournit la redondance au niveau du serveur pour la haute disponibilité. Dans ce didacticiel, vous allez apprendre à créer une instance de cluster de basculement à deux nœuds de SQL Server sur Linux. Vous allez effectuer les étapes spécifiques sont les suivantes :

> [!div class="checklist"]
> * Installer et configurer Linux
> * Installer et configurer SQL Server
> * Configurer le fichier hosts
> * Configurer le stockage partagé et déplacer les fichiers de base de données
> * Installer et configurer STIMULATEUR sur chaque nœud de cluster
> * Configurer l’instance de cluster de basculement

Cet article explique comment créer une instance de cluster de basculement (FCI) disque partagé de deux nœuds pour SQL Server. L’article inclut des instructions et des exemples de script pour Red Hat Enterprise Linux (RHEL). Ubuntu distributions sont semblables aux RHEL afin que les exemples de script normalement fonctionnent également sur Ubuntu. 

Pour obtenir des informations conceptuelles, consultez [basculement SQL Server Cluster Instance () sur Linux](sql-server-linux-shared-disk-cluster-concepts.md).

## <a name="prerequisites"></a>Conditions préalables

Pour terminer le scénario de bout en bout ci-dessous, vous avez besoin de deux ordinateurs pour déployer le cluster à deux nœuds et un autre serveur pour le stockage. Étapes ci-dessous décrivent la configuration de ces serveurs.

## <a name="set-up-and-configure-linux"></a>Installer et configurer Linux

La première étape consiste à configurer le système d’exploitation sur les nœuds de cluster. Sur chaque nœud du cluster, configurez une distribution linux. Utilisez la distribution et la même version sur les deux nœuds. Utilisez une ou l’autre des distributions suivantes :
    
* RHEL avec un abonnement valide pour le module complémentaire à haute disponibilité

## <a name="install-and-configure-sql-server"></a>Installer et configurer SQL Server

1. Installer et configurer SQL Server sur les deux nœuds.  Pour obtenir des instructions détaillées, consultez [installer SQL Server sur Linux](sql-server-linux-setup.md).
1. Désigner un nœud en tant que principal et l’autre comme secondaire, à des fins de configuration. Utiliser ces termes pour les éléments suivants ce guide.  
1. Sur le nœud secondaire, arrêter et désactiver les SQL Server.
    L’exemple suivant arrête et désactive les SQL Server : 
    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl disable mssql-server
    ```

    > [!NOTE] 
    > Le temps de vue d’ensemble, une clé principale du serveur est généré pour l’instance de SQL Server et mis à `var/opt/mssql/secrets/machine-key`. Sur Linux, SQL Server s’exécute toujours comme un compte local nommé mssql. S’agissant d’un compte local, son identité n’est pas partagée entre les nœuds. Par conséquent, vous devez copier la clé de chiffrement à partir du nœud principal à chaque nœud secondaire pour chaque compte mssql local puisse accéder pour déchiffrer la clé principale du serveur. 

1.  Sur le nœud principal, créez une connexion SQL server pour STIMULATEUR et accorder l’autorisation de connexion pour exécuter `sp_server_diagnostics`. STIMULATEUR utilisera ce compte pour vérifier le nœud qui exécute SQL Server. 

    ```bash
    sudo systemctl start mssql-server
    ```
   
   Se connecter à SQL Server `master` de la base de données avec le compte d’administrateur système et exécutez la commande suivante :

   ```sql
   USE [master]
   GO
   CREATE LOGIN [<loginName>] with PASSWORD= N'<loginPassword>'
   ALTER SERVER ROLE [sysadmin] ADD MEMBER [<loginName>]
   ```

   Vous pouvez aussi définir les autorisations à un niveau plus granulaire. La connexion STIMULATEUR nécessite `VIEW SERVER STATE` demander l’état d’intégrité avec sp_server_diagnostics, `setupadmin` et `ALTER ANY LINKED SERVER` pour mettre à jour le nom de l’instance FCI avec le nom de ressource en exécutant sp_dropserver et sp_addserver. 

1. Sur le nœud principal, arrêtez et désactivez les SQL Server. 

## <a name="configure-the-hosts-file"></a>Configurer le fichier hosts

Sur chaque nœud de cluster, configurez le fichier hosts. Le fichier hosts doit inclure l’adresse IP et le nom de chaque nœud de cluster.

1. Vérifiez l’adresse IP pour chaque nœud. Le script suivant montre l’adresse IP du nœud actuel. 

    ```bash
    sudo ip addr show
    ```

1. Définir le nom d’ordinateur sur chaque nœud. Donnez à chaque nœud un nom unique qui est de 15 caractères ou moins. Définir le nom d’ordinateur en l’ajoutant à `/etc/hosts`. Le script suivant vous permet de modifier `/etc/hosts` avec `vi`. 

   ```bash
   sudo vi /etc/hosts
   ```
   L’exemple suivant `/etc/hosts` avec les ajouts de deux nœuds nommés `sqlfcivm1` et `sqlfcivm2`.

   ```bash
   127.0.0.1   localhost localhost4 localhost4.localdomain4
   ::1       localhost localhost6 localhost6.localdomain6
   10.128.18.128 sqlfcivm1
   10.128.16.77 sqlfcivm2
   ```

## <a name="configure-storage--move-database-files"></a>Configurer le stockage et déplacer les fichiers de base de données  

Vous devez fournir les deux nœuds peuvent accéder à un stockage. Vous pouvez utiliser SMB, NFS ou iSCSI. Configurer le stockage, présenter le stockage pour les nœuds de cluster, puis déplacez les fichiers de base de données vers le nouveau stockage. Les articles suivants décrivent les étapes pour chaque type de stockage :

- [Configurer l’instance de cluster de basculement - iSCSI - SQL Server sur Linux](sql-server-linux-shared-disk-cluster-configure-iscsi.md)
- [Configuration d’instance de cluster de basculement - NFS - SQL Server sur Linux](sql-server-linux-shared-disk-cluster-configure-nfs.md)
- [Configuration d’instance de cluster de basculement - SMB - SQL Server sur Linux](sql-server-linux-shared-disk-cluster-configure-smb.md)

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>Installer et configurer STIMULATEUR sur chaque nœud de cluster

1. Sur les deux nœuds du cluster, créez un fichier pour stocker le nom d’utilisateur et le mot de passe SQL Server du compte de connexion Pacemaker. 

    La commande suivante a pour effet de créer et remplir ce fichier :

    ```bash
    sudo touch /var/opt/mssql/secrets/passwd
    sudo echo '<loginName>' >> /var/opt/mssql/secrets/passwd
    sudo echo '<loginPassword>' >> /var/opt/mssql/secrets/passwd
    sudo chown root:root /var/opt/mssql/secrets/passwd 
    sudo chmod 600 /var/opt/mssql/secrets/passwd    
    ```

1. Sur les deux nœuds de cluster, ouvrez les ports de pare-feu Pacemaker. Pour ouvrir ces ports avec `firewalld`, exécutez la commande suivante :

   ```bash
   sudo firewall-cmd --permanent --add-service=high-availability
   sudo firewall-cmd --reload
   ```

   > Si vous utilisez un autre pare-feu qui n’intègre pas de configuration à haute disponibilité, les ports suivants doivent être ouverts pour permettre à Pacemaker de communiquer avec les autres nœuds du cluster.
   >
   > * TCP : ports 2224, 3121, 21064
   > * UDP : port 5405

1. Installez les packages Pacemaker sur chaque nœud.

   ```bash
   sudo yum install pacemaker pcs fence-agents-all resource-agents
   ```
1. Définissez le mot de passe pour l’utilisateur par défaut qui est créé pendant l’installation des packages Pacemaker et Corosync. Utilisez le même mot de passe sur les deux nœuds. 

   ```bash
   sudo passwd hacluster
   ```
1. Activez et démarrez le service `pcsd` et Pacemaker. Cela permettra aux nœuds de rejoindre le cluster après le redémarrage. Exécutez la commande suivante sur les deux nœuds.

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   sudo systemctl enable pacemaker
   ```

1. Installez l’agent de ressources FCI pour SQL Server. Exécutez les commandes suivantes sur les deux nœuds. 

   ```bash
   sudo yum install mssql-server-ha
   ```

## <a name="configure-the-failover-cluster-instance"></a>Configurer l’instance de cluster de basculement

L’instance FCI est créé dans un groupe de ressources. Il s’agit un peu plus facile, car le groupe de ressources permet de ne pas pour les contraintes. Toutefois, ajouter les ressources dans le groupe de ressources dans l’ordre, qu'ils doivent démarrer. L’ordre, qu'ils doivent démarrer est : 

1. Ressource de stockage
2. Ressources réseau
3. Ressource d’application

Cet exemple crée une instance de cluster dans le groupe NewLinFCIGrp. Le nom du groupe de ressources doit être unique à partir de n’importe quelle ressource créé dans STIMULATEUR.

1.  Créez la ressource de disque. Vous n’obtiendrez aucune réponse si il n’est pas un problème. Le type de stockage dépend de la façon de créer la ressource de disque. Voici un exemple de chaque type de stockage. Utilisez l’exemple s’applique au type de stockage de votre stockage en cluster.

    **iSCSI**

    ```bash
    sudo pcs resource create <iSCSIDiskResourceName> Filesystem device="/dev/<VolumeGroupName>/<LogicalVolumeName>" directory="<FolderToMountiSCSIDisk>" fstype="<FileSystemType>" --group RGName
    ```

    \<iSCSIDIskResourceName > est le nom de la ressource associée au disque iSCSI

    \<VolumeGroupName > est le nom du groupe de volumes  

    \<LogicalVolumeName > est le nom du volume logique qui a été créé  

    \<FolderToMountiSCSIDIsk > est le dossier pour monter le disque (pour les bases de données système et l’emplacement par défaut, il serait /var/opt/mssql/data)

    \<FileSystemType > serait EXT4 ou XFS selon comment les choses ont été mis en forme et la distribution de quel prend en charge. 

    **NFS**

    ```bash
    sudo pcs resource create <NFSDiskResourceName> Filesystem device="<IPAddressOfNFSServer>:<FolderOnNFSServer>" directory="<FolderToMountNFSShare>" fstype=nfs4 options=" nfsvers=4.2,timeo=14,intr" --group RGName
    mount -t nfs4 IPAddressOfNFSServer:FolderOnNFSServer /var/opt/mssql/data -o 
    ```

    \<NFSDIskResourceName > est le nom de la ressource associé au partage NFS

    \<IPAddressOfNFSServer > est l’adresse IP du serveur NFS que vous vous apprêtez à utiliser

    \<FolderOnNFSServer > est le nom du partage NFS

    \<FolderToMountNFSShare > est le dossier pour monter le disque (pour les bases de données système et l’emplacement par défaut, il serait /var/opt/mssql/data)

     Vous trouverez ci-dessous un exemple :

    ```bash
    mount -t nfs4 200.201.202.63:/var/nfs/fci1 /var/opt/mssql/data -o nfsvers=4.2,timeo=14,intr
    ```

    **SMB**

    ```bash
    sudo pcs resource create SMBDiskResourceName Filesystem device="//<ServerName>/<ShareName>" directory="<FolderName>" fstype=cifs options="vers=3.0,username=<UserName>,password=<Password>,domain=<ADDomain>,uid=<mssqlUID>,gid=<mssqlGID>,file_mode=0777,dir_mode=0777" --group <RGName>
    ```

    \<ServerName > est le nom du serveur avec le partage SMB

    \<Nom de partage > est le nom du partage

    \<Nom_dossier > est le nom du dossier créé dans la dernière étape
    
    \<Nom d’utilisateur > est le nom de l’utilisateur pour accéder au partage

    \<Mot de passe > est le mot de passe pour l’utilisateur

    \<DomaineAD > est le domaine AD DS (le cas échéant, lorsque vous utilisez un partage SMB de basée sur Windows Server)

    \<mssqlUID > est l’UID de l’utilisateur mssql

    \<mssqlGID > est codé de l’utilisateur mssql

    \<RGName > est le nom du groupe de ressources
 
2.  Créez l’adresse IP qui sera utilisé par l’instance FCI. Vous n’obtiendrez aucune réponse si il n’est pas un problème.

    ```bash
    sudo pcs resource create <IPResourceName> ocf:heartbeat:IPaddr2 ip=<IPAddress> nic=<NetworkCard> cidr_netmask=<NetMask> --group <RGName>
    ```

    \<IPResourceName > est le nom de la ressource associée à l’adresse IP

    \<Adresse IP > est l’adresse IP de l’instance FCI

    \<NetworkCard > est la carte réseau associée au sous-réseau (par exemple, eth0)

    \<Masque de sous-réseau > est le masque de sous-réseau (par exemple, 24)

    \<RGName > est le nom du groupe de ressources
 
3.  Créer la ressource FCI. Vous n’obtiendrez aucune réponse si il n’est pas un problème.

    ```bash
    sudo pcs resource create FCIResourceName ocf:mssql:fci op defaults timeout=60s --group RGName
    ```

    \<FCIResourceName > est non seulement le nom de la ressource, mais le nom convivial qui est associé à l’instance FCI. Voici ce que les utilisateurs et applications utilisera pour se connecter. 

    \<RGName > est le nom du groupe de ressources.
 
4.  Exécutez la commande `sudo pcs resource`. L’instance FCI doit être en ligne.
 
5.  Se connecter à l’instance FCI avec SSMS ou sqlcmd à l’aide du nom DNS/de ressources de l’instance FCI.

6.  Exécutez l’instruction `SELECT @@SERVERNAME`. Elle doit retourner le nom de l’instance FCI.

7.  Exécutez l’instruction `SELECT SERVERPROPERTY('ComputerNamePhysicalNetBIOS')`. Elle doit retourner le nom de l’instance FCI s’exécute sur le nœud.

8.  Procéder manuellement l’instance FCI pour les autres nœuds. Consultez les instructions situées sous [instance de cluster de basculement opérer - SQL Server sur Linux](sql-server-linux-shared-disk-cluster-operate.md).

9.  Enfin, Échec de l’instance de cluster vers le nœud d’origine et supprimez la contrainte de colocalisation.

<!---
|Distribution |Topic 
|----- |-----
|**Red Hat Enterprise Linux with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)<br/>[Operate](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-sles-configure.md)
-->
## <a name="summary"></a>Résumé

Dans ce didacticiel vous terminé les tâches suivantes.

> [!div class="checklist"]
> * Installer et configurer Linux
> * Installer et configurer SQL Server
> * Configurer le fichier hosts
> * Configurer le stockage partagé et déplacer les fichiers de base de données
> * Installer et configurer STIMULATEUR sur chaque nœud de cluster
> * Configurer l’instance de cluster de basculement

## <a name="next-steps"></a>Étapes suivantes

- [Fonctionnement de SQL Server sur Linux - instance de cluster de basculement](sql-server-linux-shared-disk-cluster-operate.md)

<!--Image references-->


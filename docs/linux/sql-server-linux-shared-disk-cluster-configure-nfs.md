---
title: Configurer le stockage instance cluster de basculement NFS - SQL Server sur Linux | Documents Microsoft
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 08/28/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.workload: Inactive
ms.openlocfilehash: e4e783017d594e07c35e33cc6ac1485abad4af4f
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="configure-failover-cluster-instance---nfs---sql-server-on-linux"></a>Configuration d’instance de cluster de basculement - NFS - SQL Server sur Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Cet article explique comment configurer le stockage NFS pour une instance de cluster de basculement (FCI) sur Linux. 

NFS ou système de fichiers réseau, est une méthode courante pour le partage dans le monde Linux, mais pas les fenêtres d’un des disques. Similaire à iSCSI, NFS peut être configuré sur un serveur ou une sorte d’appareil ou l’unité de stockage tant qu’il répond aux exigences du stockage SQL Server.

## <a name="important-nfs-server-information"></a>Informations importantes du serveur NFS

La source d’hébergement NFS (un serveur Linux ou quelque chose d’autre) doit être à l’aide de/conforme à la version 4.2 ou ultérieure. Les versions antérieures ne fonctionnera pas avec SQL Server sur Linux.

Lorsque vous configurez l’ou les dossiers à partager sur le serveur NFS, assurez-vous qu’ils les options générales de ces instructions :
- `rw`Pour vous assurer que le dossier permettre être lues et écrites dans
- `sync`Pour garantir la garantie d’écritures dans le dossier
- N’utilisez pas `no_root_squash` en tant qu’option ; il est considéré comme un risque de sécurité
- Assurez-vous que le dossier dispose des droits d’accès complets (777) appliquées

Assurez-vous que vos normes de sécurité sont appliquées pour accéder à. Lorsque vous configurez le dossier, assurez-vous que seuls les serveurs participant à l’instance FCI consulter le dossier NFS. Un exemple d’un /etc/exports modifié sur une solution NFS basés sur Linux est indiqué ci-dessous dans lequel le dossier est limité à FCIN1 et FCIN2.

![05-nfsacl][1]

## <a name="instructions"></a>Instructions

1. Dans la configuration ICF, choisissez un des serveurs participant à la. Quel que soit l’application. 

2. Vérifiez que le serveur peut voir le mount(s) sur le serveur NFS.

    ```bash
    sudo showmount -e <IPAddressOfNFSServer>
    ```

    \<IPAddressOfNFSServer > est l’adresse IP du serveur NFS que vous vous apprêtez à utiliser.

3. Pour les bases de données système ou les informations stockées dans l’emplacement de données par défaut, procédez comme suit. Sinon, passez à l’étape 4.
 
   * Vérifiez que SQL Server est arrêté sur le serveur que vous utilisez.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```
   * Commutateur entièrement le super utilisateur. Vous ne recevrez pas tout accusé de réception en cas de réussite.

    ```bash
    sudo -i
    ```

   * Basculer vers l’utilisateur mssql. Vous ne recevrez pas tout accusé de réception en cas de réussite.

    ```bash
    su mssql
    ```

   * Créez un répertoire temporaire pour stocker les données de SQL Server et les fichiers journaux. Vous ne recevrez pas tout accusé de réception en cas de réussite.

    ```bash
    mkdir <TempDir>
    ```

    \<TempDir > est le nom du dossier. L’exemple suivant crée un dossier nommé /var/opt/mssql/tmp.

    ```bash
    mkdir /var/opt/mssql/tmp
    ```

   * Copiez les fichiers journaux et de données de SQL Server dans le répertoire temporaire. Vous ne recevrez pas tout accusé de réception en cas de réussite.
    
    ```bash
    cp /var/opt/mssql/data/* <TempDir>
    ```

    \<TempDir > est le nom du dossier à partir de l’étape précédente.

   * Vérifiez que les fichiers se trouvent dans le répertoire.

    ```bash
    ls TempDir
    ```

    \<TempDir > est le nom du dossier à partir de l’étape d.

   * Supprimez les fichiers à partir du répertoire de données SQL Server existant. Vous ne recevrez pas tout accusé de réception en cas de réussite.

    ```bash
    rm – f /var/opt/mssql/data/*
    ```

   * Vérifiez que les fichiers ont été supprimés. 

    ```bash
    ls /var/opt/mssql/data
    ```
    
   * Tapez exit pour revenir à l’utilisateur racine.

   * Montez le partage NFS dans le dossier de données SQL Server. Vous ne recevrez pas tout accusé de réception en cas de réussite.

    ```bash
    mount -t nfs4 <IPAddressOfNFSServer>:<FolderOnNFSServer> /var/opt/mssql/data -o nfsvers=4.2,timeo=14,intr
    ```

    \<IPAddressOfNFSServer > est l’adresse IP du serveur NFS que vous vous apprêtez à utiliser 

    \<FolderOnNFSServer > est le nom du partage NFS. L’exemple de syntaxe ci-dessous correspondent aux informations NFS à l’étape 2.

    ```bash
    mount -t nfs4 200.201.202.63:/var/nfs/fci1 /var/opt/mssql/data -o nfsvers=4.2,timeo=14,intr
    ```

   * Vérifiez que le montage a réussi en émettant un montage sans commutateurs.

    ```bash
    mount
    ```

    ![10-mountnoswitches][2]

   * Basculez vers l’utilisateur mssql. Vous ne recevrez pas tout accusé de réception en cas de réussite.

    ```bash
    su mssql
    ```

   * Copiez les fichiers à partir du répertoire temporaire /var/opt/mssql/data. Vous ne recevrez pas tout accusé de réception en cas de réussite.

    ```bash
    cp /var/opt/mssql/tmp/* /var/opt/mssqldata
    ```

   * Vérifiez les fichiers.

    ```bash
    ls /var/opt/mssql/data
    ```

   * Entrez exit pour ne pas être mssql 
    
   * Entrez exit pour être racine

   * Démarrez SQL Server. Si tout a été correctement copié et sécurité appliquée, SQL Server doit afficher correctement a démarré.

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ```
    
   * Créer une base de données pour tester que sécurité est correctement configuré. L’exemple ci-dessous illustre qui en cours d’exécution via Transact-SQL ; Il est possible via SSMS.
 
    ![CreateTestdatabase][3]

   * Arrêt de SQL Server et vérifiez qu’il est arrêté.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```

   * Si vous ne créez pas de n’importe quel autres montages NFS, démontez le partage. Si vous êtes, démontez pas.

    ```bash
    sudo umount <IPAddressOfNFSServer>:<FolderOnNFSServer> <FolderToMountIn>
    ```

    \<IPAddressOfNFSServer > est l’adresse IP du serveur NFS que vous vous apprêtez à utiliser

    \<FolderOnNFSServer > est le nom du partage NFS

    \<FolderMountedIn > est le dossier créé à l’étape précédente. 

4. Pour les éléments autres que des bases de données système, telles que les bases de données utilisateur ou des sauvegardes, procédez comme suit. Si uniquement à l’aide de l’emplacement par défaut, passez à l’étape 5.

   * Commutateur le super utilisateur. Vous ne recevrez pas tout accusé de réception en cas de réussite.

    ```bash
    sudo -i
    ```

   * Créez un dossier qui sera utilisé par SQL Server. 

    ```bash
    mkdir <FolderName>
    ```

    \<Nom_dossier > est le nom du dossier. Le chemin du dossier complet sera doivent être spécifiés if pas au bon emplacement. L’exemple suivant crée un dossier nommé /var/opt/mssql/userdata.

    ```bash
    mkdir /var/opt/mssql/userdata
    ```

   * Montez le partage NFS dans le dossier qui a été créé à l’étape précédente. Vous ne recevrez pas tout accusé de réception en cas de réussite.

    ```bash
    Mount -t nfs4 <IPAddressOfNFSServer>:<FolderOnNFSServer> <FolderToMountIn> -o nfsvers=4.2,timeo=14,intr
    ```

    \<IPAddressOfNFSServer > est l’adresse IP du serveur NFS que vous vous apprêtez à utiliser

    \<FolderOnNFSServer > est le nom du partage NFS

    \<FolderToMountIn > est le dossier créé à l’étape précédente. Voici un exemple. 

    ```bash
    mount -t nfs4 200.201.202.63:/var/nfs/fci2 /var/opt/mssql/userdata -o nfsvers=4.2,timeo=14,intr
    ```

   * Vérifiez que le montage a réussi en émettant un montage sans commutateurs.
  
   * Type de sortie ne peut plus être le super utilisateur.

   * Pour tester, créez une base de données dans ce dossier. L’exemple ci-dessous utilise sqlcmd pour créer une base de données, basculer vers elle, vérifiez les fichiers existent au niveau du système d’exploitation, puis supprime l’emplacement temporaire. Vous pouvez utiliser SSMS.

    ![15-createtestdatabase][4]
 
   * Démontez le partage 

    ```bash
    sudo umount <IPAddressOfNFSServer>:<FolderOnNFSServer> <FolderToMountIn>
    ```

    \<IPAddressOfNFSServer > est l’adresse IP du serveur NFS que vous vous apprêtez à utiliser
    
    \<FolderOnNFSServer > est le nom du partage NFS

    \<FolderMountedIn > est le dossier créé à l’étape précédente. Voici un exemple. 
 
5. Répétez les étapes sur les autres nœuds.


## <a name="next-steps"></a>Étapes suivantes

[Configurer l’instance de cluster de basculement - SQL Server sur Linux](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
[1]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/05-nfsacl.png
[2]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/10-mountnoswitches.png
[3]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/20-createtestdatabase.png
[4]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/15-createtestdatabase.png

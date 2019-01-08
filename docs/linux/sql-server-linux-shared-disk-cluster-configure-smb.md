---
title: Configurer le stockage instance cluster de basculement SMB - SQL Server sur Linux | Microsoft Docs
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/28/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: e93f85302417674b31de0129650dbb85092f8962
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52532006"
---
# <a name="configure-failover-cluster-instance---smb---sql-server-on-linux"></a>Configuration d’instance de cluster de basculement - SMB - SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article explique comment configurer le stockage SMB pour une instance de cluster de basculement (FCI) sur Linux. 
 
Dans le monde non Windows, SMB est souvent référencé par le système CIFS (Common Internet File System) et implémenté par le biais de Samba. Dans le monde de Windows, l’accès à un partage SMB s’effectue ainsi : \\NOM_SERVEUR\NOM_PARTAGE. Pour les installations de SQL Server basées sur Linux, le partage SMB doit être monté en tant que dossier.

## <a name="important-source-and-server-information"></a>Informations importantes sur la source et le serveur

Voici quelques conseils et les notes relatives à l’aide de SMB :
- Le partage SMB peut se trouver sur Windows, Linux, ou même sur une appliance s'il propose SMB 3.0 ou version ultérieure. Pour plus d’informations sur Samba et SMB 3.0, consultez [SMB 3.0](https://wiki.samba.org/index.php/Samba3/SMB2#SMB_3.0) pour voir si votre implémentation Samba est compatible avec SMB 3.0.
- Le partage SMB doit être hautement disponible.
- La sécurité doit être définie correctement sur le partage SMB. Voici un exemple de /etc/samba/smb.conf, où SQLData1 est le nom du partage.

![05-smbsource][1]

## <a name="instructions"></a>Instructions

1.  Choisissez un des serveurs (peu importe lequel) qui participera à la configuration de l'instance de cluster de basculement. Peu importe lequel.

2.  Obtenir des informations sur l’utilisateur mssql.

    ```bash
    sudo id mssql
    ```
    
    Notez l’uid, le gid et les groupes. 

3. Exécutez `sudo smbclient -L //NameOrIP/ShareName -U User`.

    \<NameOrIP > est le nom DNS ou l’adresse IP du serveur qui héberge le partage SMB.

    \<Nom de partage > est le nom du partage SMB. 

4. Pour le système de bases de données ou tout élément stocké dans l’emplacement de données par défaut, procédez comme suit. Sinon, passez à l’étape 5. 

   *    Vérifiez que SQL Server est arrêté sur le serveur que vous utilisez.
    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```

   *    Basculez entièrement en super utilisateur. Vous ne recevrez pas d’accusé de réception en cas de réussite.

    ```bash
    sudo -i
    ```

   *    Basculez vers l’utilisateur mssql. Vous ne recevrez pas d’accusé de réception en cas de réussite.

    ```bash
    su mssql
    ```

   *    Créez un répertoire temporaire pour stocker les données de SQL Server et les fichiers journaux. Vous ne recevrez pas d’accusé de réception en cas de réussite.

    ```bash
    mkdir <TempDir>
    ```

    <TempDir> est le nom du dossier. L’exemple suivant crée un dossier nommé /var/opt/mssql/tmp.

    ```bash
    mkdir /var/opt/mssql/tmp
    ```

   *    Copiez les fichiers journaux et de données de SQL Server dans le répertoire temporaire. Vous ne recevrez pas d’accusé de réception en cas de réussite.

    ```bash
    cp /var/opt/mssql/data/* <TempDir>
    ```

    \<TempDir > est le nom du dossier à partir de l’étape précédente.
    
   *    Vérifiez que les fichiers se trouvent dans le répertoire.

    ```bash
    ls <TempDir>
    ```

    \<TempDir > est le nom du dossier à partir de l’étape d.
    
   *    Supprimez les fichiers à partir du répertoire de données SQL Server existant. Vous ne recevrez pas d’accusé de réception en cas de réussite.
 
    ```bash
    rm - f /var/opt/mssql/data/*
    ```

   *    Vérifiez que les fichiers ont été supprimés. 

    ```bash
    ls /var/opt/mssql/data
    ```
 
   *    Tapez exit pour revenir à l’utilisateur "root".

   *    Montez le partage SMB dans le dossier de données SQL Server. Vous ne recevrez pas d’accusé de réception en cas de réussite. Cet exemple montre la syntaxe pour la connexion à un partage basée sur Windows Server SMB 3.0.

    ```bash
    Mount -t cifs //<ServerName>/<ShareName> /var/opt/mssql/data -o vers=3.0,username=<UserName>,password=<Password>,domain=<domain>,uid=<mssqlUID>,gid=<mssqlGID>,file_mode=0777,dir_mode=0777
    ```

    \<ServerName > est le nom du serveur avec le partage SMB
    
    \<Nom de partage > est le nom du partage

    \<Nom d’utilisateur > est le nom de l’utilisateur pour accéder au partage

    \<Mot de passe > est le mot de passe pour l’utilisateur

    \<domaine > est le nom d’Active Directory

    \<mssqlUID > est l’UID de l’utilisateur mssql 
 
    \<mssqlGID > est le GID de l’utilisateur mssql
 
   *    Vérifiez que le montage a réussi en émettant une commande mount sans commutateurs.

    ```bash
    mount
    ```
 
   *    Basculez vers l’utilisateur mssql. Vous ne recevrez pas d’accusé de réception en cas de réussite.

    ```bash
    su mssql
    ```

   *    Copiez les fichiers à partir du répertoire temporaire /var/opt/mssql/data. Vous ne recevrez pas d’accusé de réception en cas de réussite.

    ```bash
    cp /var/opt/mssql/tmp/* /var/opt/mssql/data
    ```

   *    Vérifiez les fichiers.

    ```bash
    ls /var/opt/mssql/data
    ```

   *    Entrez exit pour ne plus être mssql 

   *    Entrez exit pour ne plus être root

   *    Démarrez SQL Server. Si tout a été correctement copié et la sécurité appliquée, SQL Server doit s'afficher comme démarré.

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ```
 
   *    Pour poursuivre le test, créez une base de données pour vérifier que les autorisations sont correctes. L’exemple suivant utilise Transact-SQL ; Vous pouvez utiliser SSMS.

    ![10_testcreatedb][2] 
  
   *    Arrêtez SQL Server et vérifiez qu’il est bien arrêté. Si vous vous apprêtez à ajouter ou à tester d’autres disques, n’arrêtez pas SQL Server tant que ceux-ci n'ont pas été ajoutés et testés.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```

   *    Uniquement si vous avez terminé, démontez le partage. Si ce n’est pas le cas, démontez après avoir terminé le test/Ajout de tous les disques supplémentaires.

    ```bash
    sudo umount //<IPAddressorServerName>/<ShareName /<FolderMountedIn>
    ```

    \<IPAddressOrServerName > est l’adresse IP ou le nom de l’hôte SMB

    \<Nom de partage > est le nom du partage
    
    \<FolderMountedIn > est le nom du dossier où SMB est monté

5.  Pour les éléments autres que les bases de données système, tels que les bases de données utilisateur ou les sauvegardes, suivez ces étapes. Si vous utilisez uniquement l’emplacement par défaut, passez à l’étape 14.
    
   *    Passez en mode superutilisateur. Vous ne recevrez pas d’accusé de réception en cas de réussite.

    ```bash
    sudo -i
    ```
    
   *    Créez un dossier qui sera utilisé par SQL Server. 

    ```bash
    mkdir <FolderName>
    ```

    \<Nom_dossier > est le nom du dossier. Chemin d’accès complet du dossier doit être spécifié sinon dans l’emplacement approprié. L’exemple suivant crée un dossier nommé /var/opt/mssql/userdata.

    ```bash
    mkdir /var/opt/mssql/userdata
    ```

   *    Montez le partage SMB dans le dossier de données SQL Server. Vous ne recevrez pas d’accusé de réception en cas de réussite. Cet exemple montre la syntaxe pour la connexion à un partage en fonction du Samba SMB 3.0.

    ```bash
    Mount -t cifs //<ServerName>/<ShareName> <FolderName> -o vers=3.0,username=<UserName>,password=<Password>,uid=<mssqlUID>,gid=<mssqlGID>,file_mode=0777,dir_mode=0777
    ```

    \<ServerName > est le nom du serveur avec le partage SMB

    \<Nom de partage > est le nom du partage

    \<Nom_dossier > est le nom du dossier créé à l’étape précédente  

    \<Nom d’utilisateur > est le nom de l’utilisateur pour accéder au partage

    \<Mot de passe > est le mot de passe pour l’utilisateur

    \<mssqlUID > est l’UID de l’utilisateur mssql

    \<mssqlGID > est le GID de l’utilisateur mssql.
 
   * Vérifiez que le montage a réussi en émettant une commande mount sans commutateurs.
 
   * Tapez exit pour ne plus plus être super utilisateur.

   * Pour tester, créez une base de données dans ce dossier. L’exemple suivant utilise sqlcmd pour créer une base de données, changer le contexte vers cette base, et vérifier que les fichiers existent bien au niveau du système d’exploitation, puis supprime l’emplacement temporaire. Vous pouvez aussi utiliser SSMS.
 
   * Démonter le partage 

    ```bash
    sudo umount //<IPAddressorServerName>/<ShareName> /<FolderMountedIn>
    ```
    
    \<IPAddressOrServerName > est l’adresse IP ou le nom de l’hôte SMB
 
    \<Nom de partage > est le nom du partage
 
    \<FolderMountedIn > est le nom du dossier où SMB est monté.
 
6.  Répétez les étapes sur les autres nœuds.

Vous êtes maintenant prêt à configurer l’instance FCI.

## <a name="next-steps"></a>Étapes suivantes

[Configurer l’instance de cluster de basculement - SQL Server sur Linux](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
[1]: ./media/sql-server-linux-shared-disk-cluster-configure-smb/05-smbsource.png 
[2]: ./media/sql-server-linux-shared-disk-cluster-configure-smb/10-testcreatedb.png 

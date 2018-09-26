---
title: Migrer une base de données SQL Server à partir de Windows et Linux | Microsoft Docs
description: Ce didacticiel montre comment sauvegarder une base de données SQL Server sur Windows et restaurez-la sur une machine Linux exécutant SQL Server.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/16/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 9ac64d1a-9fe5-446e-93c3-d17b8f55a28f
ms.openlocfilehash: e3aa22603fa79a2d03b69b1043ea9b0200706925
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46713011"
---
# <a name="migrate-a-sql-server-database-from-windows-to-linux-using-backup-and-restore"></a>Migrer une base de données SQL Server à partir de Windows pour Linux à l’aide de la sauvegarde et restauration

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server de sauvegarde et de la fonctionnalité de restauration est la méthode recommandée pour migrer une base de données SQL Server sur Windows pour SQL Server sur Linux. Ce didacticiel vous guidera à travers les étapes requises pour déplacer une base de données pour Linux avec les techniques de sauvegarde et restauration.

> [!div class="checklist"]
> * Créer un fichier de sauvegarde sur Windows SSMS
> * Installer un interpréteur de commandes Bash sur Windows
> * Déplacer le fichier de sauvegarde pour Linux à partir de l’interpréteur de commandes Bash
> * Restaurer le fichier de sauvegarde sur Linux avec Transact-SQL
> * Exécuter une requête pour vérifier la migration

Vous pouvez également créer un SQL Server groupe de disponibilité AlwaysOn pour migrer une base de données SQL Server à partir de Windows et Linux. Consultez [sql-server-linux-availability-group-cross-platform](sql-server-linux-availability-group-cross-platform.md).

## <a name="prerequisites"></a>Prérequis

Les conditions préalables suivantes sont nécessaires pour suivre ce didacticiel :

* Machine Windows avec les éléments suivants :
  * [SQL Server](https://www.microsoft.com/sql-server/sql-server-2016-editions) installé.
  * [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) installé.
  * Base de données cible à migrer.

* Ordinateur Linux avec les composants suivants :
  * SQL Server ([RHEL](quickstart-install-connect-red-hat.md), [SLES](quickstart-install-connect-suse.md), ou [Ubuntu](quickstart-install-connect-ubuntu.md)) avec les outils de ligne de commande.

## <a name="create-a-backup-on-windows"></a>Créer une sauvegarde sur Windows

Il existe plusieurs façons de créer un fichier de sauvegarde d’une base de données sur Windows. Les étapes suivantes utilisent SQL Server Management Studio (SSMS).

1. Démarrez **SQL Server Management Studio** sur votre ordinateur Windows. 

1. Dans la boîte de dialogue de connexion, entrez **localhost**.

1. Dans l’Explorateur d’objets, développez **bases de données**.

1. Cliquez sur votre base de données cible, sélectionnez **tâches**, puis cliquez sur **sauvegarder...** .

   ![Utiliser SSMS pour créer un fichier de sauvegarde](./media/sql-server-linux-migrate-restore-database/ssms-create-backup.png)

1. Dans la boîte de dialogue **Sauvegarder une base de données**, vérifiez que **Type de sauvegarde** est défini sur **Complète** et **Sauvegarder vers** sur **Disque**. Notez le nom et l’emplacement du fichier. Par exemple, une base de données nommée **YourDB** sur SQL Server 2016 utilise `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\YourDB.bak` comme chemin de sauvegarde par défaut.

1. Cliquez sur **OK** pour sauvegarder votre base de données.

> [!NOTE]
> Une autre option consiste à exécuter une requête Transact-SQL pour créer le fichier de sauvegarde. La commande Transact-SQL suivante exécute les mêmes actions que les étapes précédentes pour une base de données appelée **YourDB**:
>
> ```sql
> BACKUP DATABASE [YourDB] TO  DISK =
> N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\YourDB.bak'
> WITH NOFORMAT, NOINIT, NAME = N'YourDB-Full Database Backup',
> SKIP, NOREWIND, NOUNLOAD, STATS = 10
> GO
> ```

## <a name="install-a-bash-shell-on-windows"></a>Installer un interpréteur de commandes Bash sur Windows

Pour restaurer la base de données, vous devez d’abord transférer le fichier de sauvegarde à partir de l’ordinateur Windows vers l’ordinateur Linux cible. Dans ce didacticiel, nous allons déplacer le fichier Linux à partir d’un interpréteur de commandes Bash (fenêtre de terminal) s’exécutant sous Windows.

1. Installez un interpréteur de commandes Bash sur votre ordinateur Windows qui prend en charge la **scp** (copie sécurisée) et les commandes **ssh** (connexion à distance). Deux exemples incluent :

   * Le [sous-système Windows pour Linux](https://msdn.microsoft.com/commandline/wsl/about) (Windows 10)
   * L’interpréteur de commandes Git Bash ([https://git-scm.com/downloads](https://git-scm.com/downloads))

1. Ouvrez une session Bash sur Windows.

## <a id="scp"></a> Copiez le fichier de sauvegarde pour Linux

1. Dans votre session d’interpréteur de commandes, accédez au répertoire contenant votre fichier de sauvegarde. Exemple :

   ```bash
   cd 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\'
   ```

1. Utilisez la commande **scp** pour transférer le fichier sur l’ordinateur Linux cible. L'exemple suivant transfère **YourDB.bak** vers le répertoire de base de *user1* sur le serveur Linux avec une adresse IP de *192.0.2.9*:

   ```bash
   scp YourDB.bak user1@192.0.2.9:./
   ```
   ![commande SCP](./media/sql-server-linux-migrate-restore-database/scp-command.png)

> [!TIP]
> Il existe des alternatives à l’utilisation de scp pour le transfert de fichiers. L'une consiste à utiliser [Samba](https://help.ubuntu.com/community/Samba) pour configurer un partage de réseau SMB entre Windows et Linux. Pour une procédure pas à pas sur Ubuntu, consultez [la création d’un partage réseau Via Samba](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way!). Une fois établie, vous pouvez y accéder en tant que partage de fichier réseau à partir de Windows, tel que  **\\ \\machinenameorip\\partager**.

## <a name="move-the-backup-file-before-restoring"></a>Déplacer le fichier de sauvegarde avant la restauration

À ce stade, le fichier de sauvegarde est sur votre serveur Linux dans votre répertoire de base utilisateur. Avant de restaurer la base de données vers SQL Server, vous devez placer la sauvegarde dans un sous-répertoire de **/var/opt/mssql**.

1. Dans la même session Windows Bash, connectez-vous à distance à votre ordinateur Linux cible avec **ssh**. L’exemple suivant se connecte à l’ordinateur Linux **192.0.2.9** en tant qu’utilisateur **user1**.

   ```bash
   ssh user1@192.0.2.9
   ```

   Vous exécutez à présent commandes sur le serveur Linux distant.

1. Activez le mode super utilisateur.

   ```bash
   sudo su
   ```

1. Créez un nouveau répertoire de sauvegarde. Le paramètre -p ne fait rien si le répertoire existe déjà. 

   ```bash
   mkdir -p /var/opt/mssql/backup
   ```

1. Déplacez le fichier de sauvegarde vers ce répertoire. Dans l’exemple suivant, le fichier de sauvegarde réside dans le répertoire de base de *user1*. Modifiez la commande pour correspondre à l’emplacement et au nom de votre fichier de sauvegarde.

   ```bash
   mv /home/user1/YourDB.bak /var/opt/mssql/backup/
   ```

1. Quittez le mode super utilisateur.

   ```bash
   exit
   ```

## <a name="restore-your-database-on-linux"></a>Restaurer votre base de données sur Linux

Pour restaurer la sauvegarde de base de données, vous pouvez utiliser la commande Transact-SQL (T-SQL) **RESTORE DATABASE**.

> [!NOTE]
> Les étapes suivantes utilisent l'outil **sqlcmd**. Si vous n’avez pas installé les outils SQL Server, reportez-vous à la section [Installation des outils de ligne de commande de SQL Server sur Linux](sql-server-linux-setup-tools.md).

1. Dans le même terminal, lancez **sqlcmd**. L’exemple suivant se connecte à l’instance locale de SQL Server avec l'utilisateur **SA**. Entrez le mot de passe lorsque vous y êtes invité, ou spécifiez le mot de passe en ajoutant le paramètre **-P**.

   ```bash
   sqlcmd -S localhost -U SA
   ```

1. À l'invite `>1`, entrez la commande suivante **RESTORE DATABASE** suivante, en appuyant sur ENTRÉE après chaque ligne (vous ne pouvez pas copier-coller la commande multiligne entière à la fois). Remplacez toutes les occurrences de `YourDB` par le nom de votre base de données.

   ```sql
   RESTORE DATABASE YourDB
   FROM DISK = '/var/opt/mssql/backup/YourDB.bak'
   WITH MOVE 'YourDB' TO '/var/opt/mssql/data/YourDB.mdf',
   MOVE 'YourDB_Log' TO '/var/opt/mssql/data/YourDB_Log.ldf'
   GO
   ```

   Vous devez obtenir un message indiquant que la base de données est restaurée avec succès.

   `RESTORE DATABASE` peut retourner une erreur telle que l’exemple suivant :

   ```bash
   File 'YourDB_Product' cannot be restored to 'Z:\Microsoft SQL Server\MSSQL11.GLOBAL\MSSQL\Data\YourDB\YourDB_Product.ndf'. Use WITH MOVE to identify a valid location for the file.
   Msg 5133, Level 16, State 1, Server servername, Line 1
   Directory lookup for the file "Z:\Microsoft SQL Server\MSSQL11.GLOBAL\MSSQL\Data\YourDB\YourDB_Product.ndf" failed with the operating system error 2(The system cannot find the file specified.).
   ```
   
   Dans ce cas, la base de données contient des fichiers secondaires. Si ces fichiers ne sont pas spécifiés dans le `MOVE` clause de `RESTORE DATABASE`, la procédure de restauration tente de les créer dans le même chemin que le serveur d’origine. 

   Vous pouvez répertorier tous les fichiers inclus dans la sauvegarde :
   ```sql
   RESTORE FILELISTONLY FROM DISK = '/var/opt/mssql/backup/YourDB.bak'
   GO
   ```
   Vous devez obtenir une liste comme celle ci-dessous (liste uniquement les deux premières colonnes) :
   ```sql
   LogicalName         PhysicalName                                                                 ..............
   ----------------------------------------------------------------------------------------------------------------------
   YourDB              Z:\Microsoft SQL Server\MSSQL11.GLOBAL\MSSQL\Data\YourDB\YourDB.mdf          ..............
   YourDB_Product      Z:\Microsoft SQL Server\MSSQL11.GLOBAL\MSSQL\Data\YourDB\YourDB_Product.ndf  ..............
   YourDB_Customer     Z:\Microsoft SQL Server\MSSQL11.GLOBAL\MSSQL\Data\YourDB\YourDB_Customer.ndf ..............
   YourDB_log          Z:\Microsoft SQL Server\MSSQL11.GLOBAL\MSSQL\Data\YourDB\YourDB_Log.ldf      ..............
   ```
   
   Vous pouvez utiliser cette liste pour créer `MOVE` clauses pour les fichiers supplémentaires. Dans cet exemple, le `RESTORE DATABASE` est :

   ```sql
   RESTORE DATABASE YourDB
   FROM DISK = '/var/opt/mssql/backup/YourDB.bak'
   WITH MOVE 'YourDB' TO '/var/opt/mssql/data/YourDB.mdf',
   MOVE 'YourDB_Product' TO '/var/opt/mssql/data/YourDB_Product.ndf',
   MOVE 'YourDB_Customer' TO '/var/opt/mssql/data/YourDB_Customer.ndf',
   MOVE 'YourDB_Log' TO '/var/opt/mssql/data/YourDB_Log.ldf'
   GO
   ```


1. Vérifiez la restauration en répertoriant toutes les bases de données du serveur. La base de données restaurée doit être répertoriée.

   ```sql
   SELECT Name FROM sys.Databases
   GO
   ```

1. Exécutez d’autres requêtes sur votre base de données migrée. La commande suivante change le contexte de base de données pour**YourDB** et sélectionne les lignes d'une table.

   ```sql
   USE YourDB
   SELECT * FROM YourTable
   GO
   ```

1. Lorsque vous avez terminé d'utiliser **sqlcmd**, tapez `exit`.

1. Lorsque vous avez terminé avec la session distante **ssh**, tapez `exit` à nouveau.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à sauvegarder une base de données sur Windows et déplacez-le vers un serveur Linux exécutant SQL Server. Vous avez appris à :
> [!div class="checklist"]
> * Créer un fichier de sauvegarde sur Windows SSMS et Transact-SQL
> * Installer un interpréteur de commandes Bash sur Windows
> * Utiliser **scp** pour déplacer les fichiers de sauvegarde à partir de Windows et Linux
> * Utiliser **ssh** pour se connecter à distance à l’ordinateur Linux
> * Déplacer le fichier de sauvegarde pour préparer la restauration
> * Utiliser **sqlcmd** pour exécuter des commandes Transact-SQL
> * Restaurer la sauvegarde de base de données avec la commande **RESTORE DATABASE** 
> * Exécutez la requête pour vérifier la migration

Ensuite, explorez les autres scénarios de migration pour SQL Server sur Linux. 

> [!div class="nextstepaction"]
>[Migrer des bases de données vers SQL Server sur Linux](sql-server-linux-migrate-overview.md)

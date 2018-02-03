---
title: "Migrer une base de données SQL Server à partir de Windows et Linux | Documents Microsoft"
description: "Ce didacticiel montre comment exécuter la sauvegarde une base de données SQL Server sur Windows et de restauration sur un ordinateur Linux en cours d’exécution SQL Server 2017."
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 08/16/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 9ac64d1a-9fe5-446e-93c3-d17b8f55a28f
ms.workload: On Demand
ms.openlocfilehash: bd27b9e7d69698137c8f16f6e4439462a55fa007
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="migrate-a-sql-server-database-from-windows-to-linux-using-backup-and-restore"></a>Migrer une base de données SQL Server à partir de Windows et Linux à l’aide de la sauvegarde et restauration

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

La sauvegarde et la restauration SQL Server est la méthode recommandée pour migrer une base de données SQL Server sur Windows vers du SQL Server 2017 sur Linux. Ce didacticiel vous guidera à travers les étapes requises pour déplacer une base de données pour Linux avec les techniques de sauvegarde et restauration.

> [!div class="checklist"]
> * Créer un fichier de sauvegarde de Windows avec SSMS
> * Installer un interpréteur de commandes Bash sur Windows
> * Déplacer le fichier de sauvegarde pour Linux à partir du shell Bash
> * Restaurer le fichier de sauvegarde sur Linux avec Transact-SQL
> * Exécutez une requête pour vérifier la migration

## <a name="prerequisites"></a>Conditions préalables

Les conditions préalables suivantes sont requises pour effectuer ce didacticiel :

* Ordinateur Windows avec les éléments suivants :
  * [SQL Server](https://www.microsoft.com/sql-server/sql-server-2016-editions) installé.
  * [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) installé.
  * Base de données cible à migrer.

* Ordinateur Linux avec les éléments suivants :
  * SQL Server 2017 ([RHEL](quickstart-install-connect-red-hat.md), [SLES](quickstart-install-connect-suse.md), ou [Ubuntu](quickstart-install-connect-ubuntu.md)) avec les outils de ligne de commande.

## <a name="create-a-backup-on-windows"></a>Créer une sauvegarde sur Windows

Il existe plusieurs façons de créer un fichier de sauvegarde de base de données sur Windows. Les étapes suivantes utilisent SQL Server Management Studio (SSMS).

1. Démarrer **SQL Server Management Studio** sur votre ordinateur Windows.

1. Dans la boîte de dialogue de connexion, entrez **localhost**.

1. Dans l’Explorateur d’objets, développez **bases de données**.

1. Avec le bouton droit de votre base de données cible, sélectionnez **tâches**, puis cliquez sur **sauvegarder...** .

   ![Utilisez SSMS pour créer un fichier de sauvegarde](./media/sql-server-linux-migrate-restore-database/ssms-create-backup.png)

1. Dans la boîte de dialogue **sauvegarder la base de données** , vérifiez que **type de sauvegarde** est **complète** et **sauvegarde sur** est **disque**. Notez le nom et l’emplacement du fichier. Par exemple, une base de données nommée **YourDB** sur SQL Server 2016 a un chemin de sauvegarde par défaut de `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\YourDB.bak`.

1. Cliquez sur **OK** pour sauvegarder votre base de données.

> [!NOTE]
> Une autre option consiste à exécuter une requête Transact-SQL pour créer le fichier de sauvegarde. La commande Transact-SQL suivante effectue les mêmes actions que les étapes précédentes pour une base de données appelée **YourDB**:
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

1. Installer un interpréteur de commandes Bash sur votre ordinateur Windows qui prend en charge la **scp** (copie sécurisée) et les commandes **ssh**  (connexion à distance). Deux exemples : 

   * Le [sous-système Windows pour Linux](https://msdn.microsoft.com/commandline/wsl/about) (Windows 10)
   * L’interface de l’interpréteur de commandes Git ([https://git-scm.com/downloads](https://git-scm.com/downloads))

1. Ouvrez une session d’interpréteur de commandes sous Windows.

## <a id="scp"></a>Copiez le fichier de sauvegarde pour Linux

1. Dans votre session d’interpréteur de commandes, accédez au répertoire contenant votre fichier de sauvegarde. Exemple :

   ```bash
   cd 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\'
   ```

1. Utilisez la commande **scp**  pour transférer le fichier sur l’ordinateur Linux cible. L'exemple suivant transfère **YourDB.bak** vers le répertoire de base de *user1* sur le serveur Linux avec une adresse IP de *192.0.2.9*:

   ```bash
   scp YourDB.bak user1@192.0.2.9:./
   ```
   ![commande de SCP](./media/sql-server-linux-migrate-restore-database/scp-command.png)

> [!TIP]
> Il existe des alternatives à l’utilisation de scp pour le transfert de fichiers. Une consiste à utiliser [Samba](https://help.ubuntu.com/community/Samba) pour configurer un partage de réseau SMB entre Windows et Linux. Pour une procédure pas à pas sur Ubuntu, consultez [la création d’un partage réseau Via Samba](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way!). Une fois configuré, vous pouvez y accéder comme partage de fichiers réseau à partir de Windows, comme  **\\ \\machinenameorip\\partager**.

## <a name="move-the-backup-file-before-restoring"></a>Déplacer le fichier de sauvegarde avant la restauration

À ce stade, le fichier de sauvegarde est sur votre serveur Linux dans votre répertoire de base. Avant de restaurer la base de données vers SQL Server, vous devez placer la sauvegarde dans un sous-répertoire de **/var/opt/mssql**.

1. Dans la même session Windows Bash, se connecter à distance à votre ordinateur Linux cible avec **ssh**. L’exemple suivant se connecte à l’ordinateur Linux **192.0.2.9** en tant qu’utilisateur **user1**.

   ```bash
   ssh user1@192.0.2.9
   ```

   Vous exécutez maintenant des commandes sur le serveur Linux distant.

1. Activer le mode de super utilisateur.

   ```bash
   sudo su
   ```

1. Créer un nouveau répertoire de sauvegarde. Le paramètre -p ne fait rien si le répertoire existe déjà.

   ```bash
   mkdir -p /var/opt/mssql/backup
   ```

1. Déplacer le fichier de sauvegarde vers ce répertoire. Dans l’exemple suivant, le fichier de sauvegarde réside dans le répertoire de base de *user1*. Modifiez la commande pour correspondre à l’emplacement et le nom de votre fichier de sauvegarde.

   ```bash
   mv /home/user1/YourDB.bak /var/opt/mssql/backup/
   ```

1. Quitter le mode super utilisateur.

   ```bash
   exit
   ```

## <a name="restore-your-database-on-linux"></a>Restaurer votre base de données sur Linux

Pour restaurer la sauvegarde de base de données, vous pouvez utiliser la commande Transact-SQL (T-SQL) **RESTORE DATABASE**.

> [!NOTE]
> Les étapes suivantes utilisent l'outil **sqlcmd**. Si vous n’avez pas pas installés les outils SQL Server, reportez-vous à la section [Installation des outils de ligne de commande de SQL Server sur Linux](sql-server-linux-setup-tools.md).

1. Dans le même terminal, lancez **sqlcmd**. L’exemple suivant se connecte à l’instance locale de SQL Server avec l'utilisateur **SA**. Entrez le mot de passe lorsque vous y êtes invité, ou spécifiez le mot de passe en ajoutant le paramètre **-P**.

   ```bash
   sqlcmd -S localhost -U SA
   ```

1. À l'invite `>1`, entrez la commande suivante **RESTORE DATABASE**. Remplacez toutes les occurrences de `YourDB` par le nom de votre base de données.

   ```sql
   RESTORE DATABASE YourDB
   FROM DISK = '/var/opt/mssql/backup/YourDB.bak'
   WITH MOVE 'YourDB' TO '/var/opt/mssql/data/YourDB.mdf',
   MOVE 'YourDB_Log' TO '/var/opt/mssql/data/YourDB_Log.ldf'
   GO
   ```

   Vous devez obtenir un message indiquant que base de données est restaurée avec succès.

1. Vérifiez que la restauration avec la liste de toutes les bases de données du serveur. La base de données restaurée doit être répertoriée.

   ```sql
   SELECT Name FROM sys.Databases
   GO
   ```

1. Exécutez d’autres requêtes sur votre base de données migrée. La commande suivante change le contexte de base de données pour **YourDB** et sélectionne les lignes d'une table.

   ```sql
   USE YourDB
   SELECT * FROM YourTable
   GO
   ```

1. Lorsque vous avez terminé d'utiliser **sqlcmd**, type `exit`.

1. Lorsque vous avez terminé avec la session distante **ssh**, tapez `exit` à nouveau.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris comment sauvegarder une base de données sur Windows et la déplacer vers un serveur SQL Server 2017 sur Linux. Vous avez appris comment à :
> [!div class="checklist"]
> * Créer un fichier de sauvegarde sur Windows SSMS et Transact-SQL
> * Installer un interpréteur de commandes Bash sur Windows
> * Utiliser **scp** pour déplacer les fichiers de sauvegarde à partir de Windows et Linux
> * Utiliser **ssh** se connecter à distance à l’ordinateur Linux
> * Déplacer le fichier de sauvegarde pour la préparation de la restauration
> * Utiliser **sqlcmd** pour exécuter des commandes Transact-SQL
> * Restaurer la sauvegarde de base de données avec le **restaurer la base de données** commande 

Ensuite, explorez les autres scénarios de migration pour SQL Server sur Linux. 

> [!div class="nextstepaction"]
>[Migrer des bases de données vers SQL Server sur Linux](sql-server-linux-migrate-overview.md)

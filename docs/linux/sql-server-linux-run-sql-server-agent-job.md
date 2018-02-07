---
title: "Créer et exécuter des travaux de SQL Server sur Linux | Documents Microsoft"
description: "Ce didacticiel montre comment exécuter le travail de l’Agent SQL Server sur Linux."
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 1d93d95e-9c89-4274-9b3f-fa2608ec2792
ms.workload: Inactive
ms.openlocfilehash: 526375f9f9f96c9ea0402dcb84f20a2c214fd13f
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="create-and-run-sql-server-agent-jobs-on-linux"></a>Créer et exécuter des travaux de l’Agent SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Les travaux de SQL Server sont utilisés pour exécuter régulièrement la même séquence de commandes dans votre base de données SQL Server. Ce didacticiel fournit un exemple montrant comment créer un travail de l’Agent SQL Server sur Linux à l’aide de Transact-SQL et SQL Server Management Studio (SSMS).

> [!div class="checklist"]
> * Installer l’Agent SQL Server sur Linux
> * Créer un nouveau travail pour effectuer des sauvegardes quotidiennes de base de données
> * Planifier et exécuter la tâche
> * Procédez de même dans SSMS (facultatif)

Pour les problèmes connus avec l’Agent SQL Server sur Linux, consultez le [Notes de publication](sql-server-linux-release-notes.md).

## <a name="prerequisites"></a>Configuration requise

Les conditions préalables suivantes sont requises pour effectuer ce didacticiel :

* Ordinateur Linux avec les conditions préalables suivantes :
  * SQL Server 2017 ([RHEL](quickstart-install-connect-red-hat.md), [SLES](quickstart-install-connect-suse.md), ou [Ubuntu](quickstart-install-connect-ubuntu.md)) avec les outils de ligne de commande.

Les conditions préalables suivantes sont facultatives :

* Ordinateur Windows avec SSMS :
  * [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) pour les étapes facultatives de SSMS.

## <a name="install-sql-server-agent"></a>Installer l’Agent SQL Server

Pour utiliser l’Agent SQL Server sur Linux, vous devez d’abord installer le **mssql-server-agent** package sur un ordinateur équipé de SQL Server 2017 est installé.

1. Installer **mssql-server-agent** avec la commande appropriée pour votre système d’exploitation Linux.

   | Plateforme | Commandes d’installation |
   |-----|-----|
   | RHEL | `sudo yum install mssql-server-agent` |
   | SLES | `sudo zypper refresh`<br/>`sudo zypper update mssql-server-agent` |
   | Ubuntu | `sudo apt-get update`<br/>`sudo apt-get install mssql-server-agent` |

1. Redémarrez SQL Server avec la commande suivante :

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a name="create-a-sample-database"></a>Créer un exemple de base de données

Procédez comme suit pour créer une base de données exemple nommé **SampleDB**. Cette base de données est utilisé pour le travail de sauvegarde quotidiens.

1. Sur l’ordinateur Linux, ouvrez une session Terminal Server d’un interpréteur de commandes.

1. Utilisez **sqlcmd** pour exécuter Transact-SQL **CREATE DATABASE** commande.

   ```bash
   /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -Q 'CREATE DATABASE SampleDB'
   ```

1. Vérifiez que la base de données est créé en répertoriant les bases de données sur votre serveur.

   ```bash
   /opt/mssql-tools/bin/sqlcmd -S localhost -U SA -Q 'SELECT Name FROM sys.Databases'
   ```

## <a name="create-a-job-with-transact-sql"></a>Créer un travail avec Transact-SQL

La procédure suivante crée un travail de l’Agent SQL Server sur Linux avec les commandes Transact-SQL. La tâche s’exécute une sauvegarde quotidienne de la base de données exemple **SampleDB**.

> [!TIP]
> Vous pouvez utiliser n’importe quel client de T-SQL pour exécuter ces commandes. Par exemple, sur Linux, vous pouvez utiliser [sqlcmd](sql-server-linux-setup-tools.md) ou [Visual Studio Code](sql-server-linux-develop-use-vscode.md). À partir d’un serveur à distance de Windows, vous pouvez également exécuter des requêtes dans SQL Server Management Studio (SSMS) ou utiliser l’interface utilisateur pour la gestion des travaux, qui est décrit dans la section suivante.

1. Utilisez [sp_add_job](../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md) pour créer une tâche nommée `Daily SampleDB Backup`.

   ```sql
   -- Adds a new job executed by the SQLServerAgent service
   -- called 'Daily SampleDB Backup'
   USE msdb ;
   GO
   EXEC dbo.sp_add_job
      @job_name = N'Daily SampleDB Backup' ;
   GO
   ```

1. Appelez [sp_add_jobstep](../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md) pour créer une étape de travail qui crée une sauvegarde de la `SampleDB` base de données.

   ```sql
   -- Adds a step (operation) to the job
   EXEC sp_add_jobstep
      @job_name = N'Daily SampleDB Backup',
      @step_name = N'Backup database',
      @subsystem = N'TSQL',
      @command = N'BACKUP DATABASE SampleDB TO DISK = \
         N''/var/opt/mssql/data/SampleDB.bak'' WITH NOFORMAT, NOINIT, \
         NAME = ''SampleDB-full'', SKIP, NOREWIND, NOUNLOAD, STATS = 10',
      @retry_attempts = 5,
      @retry_interval = 5 ;
   GO
   ```

1. Puis créer une planification quotidienne pour votre projet avec [sp_add_schedule](../relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql.md).

   ```sql
   -- Creates a schedule called 'Daily'
   EXEC dbo.sp_add_schedule
      @schedule_name = N'Daily SampleDB',
      @freq_type = 4,
      @freq_interval = 1,
      @active_start_time = 233000 ;
   USE msdb ;
   GO
   ```

1. Attachez la planification du travail pour la tâche avec [sp_attach_schedule](../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md).

   ```sql
   -- Sets the 'Daily' schedule to the 'Daily SampleDB Backup' Job
   EXEC sp_attach_schedule
      @job_name = N'Daily SampleDB Backup',
      @schedule_name = N'Daily SampleDB';
   GO
   ```

1. Utilisez [sp_add_jobserver](../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md) pour affecter le travail sur un serveur cible. Dans cet exemple, la cible est le serveur local.

   ```sql
   EXEC dbo.sp_add_jobserver
      @job_name = N'Daily SampleDB Backup',
      @server_name = N'(LOCAL)';
   GO
   ```
1. Démarrer le travail avec [sp_start_job](../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md).

   ```sql
   EXEC dbo.sp_start_job N' Daily SampleDB Backup' ;
   GO
   ```

## <a name="create-a-job-with-ssms"></a>Créer une tâche avec SSMS

Vous pouvez également créer et gérer des travaux à distance à l’aide de SQL Server Management Studio (SSMS) sur Windows.

1. Démarrez SSMS sur Windows et connectez-vous à votre instance de SQL Server de Linux. Pour plus d’informations, consultez [gérer SQL Server sur Linux avec SSMS](sql-server-linux-develop-use-ssms.md).

1. Vérifiez que vous avez créé une base de données exemple nommé **SampleDB**.

   <img src="./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-0.png" alt="Create a SampleDB database" style="width: 550px;"/>

1. Vérifiez que l’Agent SQL a été [installé](sql-server-linux-setup-sql-agent.md) et correctement configuré. Recherchez le signe plus en regard de l’Agent SQL Server dans l’Explorateur d’objets. Si l’Agent SQL Server n’est pas activée, essayez de redémarrer le **mssql-serveur** service sur Linux.

   ![Vérifiez que l’Agent SQL Server a été installé.](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-1.png)

1. Créer un nouveau travail.

   ![Créer un nouveau travail](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-2.png)

1. Donnez un nom à votre travail et créer votre étape de travail.

   ![Créer une étape de travail](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-3.png)

1. Spécifier le sous-système dans lequel vous souhaitez utiliser et l’action que doit effectuer l’étape de travail.

   ![Sous-système de travail](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-4.png)

   ![Action d’étape de travail](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-5.png)

1. Créer une nouvelle planification du travail.

   ![Planification du travail](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-6.png)

   ![Planification du travail](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-8.png)

1. Démarrez votre travail.

   <img src="./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-9.png" alt="Start the SQL Server Agent job" style="width: 550px;"/>

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris comment :

> [!div class="checklist"]
> * Installer l’Agent SQL Server sur Linux
> * Utilisation de Transact-SQL et procédures stockées système pour créer des tâches
> * Créer une tâche qui effectue des sauvegardes de base de données quotidiennes
> * SSMS UI permet de créer et gérer des tâches

Ensuite, Explorer les autres fonctionnalités permettant de créer et gérer des travaux :

> [!div class="nextstepaction"]
>[Documentation de l’Agent SQL Server](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent)

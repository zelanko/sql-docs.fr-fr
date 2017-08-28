---
title: "Créer et exécuter des travaux de SQL Server sur Linux | Documents Microsoft"
description: "Ce didacticiel montre comment exécuter le travail de l’Agent SQL Server sur Linux."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 1d93d95e-9c89-4274-9b3f-fa2608ec2792
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3ffb76838940f42d7a696e1c17f227517d89012d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="create-and-run-sql-server-agent-jobs-on-linux"></a>Créer et exécuter des travaux de l’Agent SQL Server sur Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Travaux de SQL Server sont utilisés pour exécuter régulièrement la même séquence de commandes dans votre base de données SQL Server. Cette rubrique fournit des exemples montrant comment créer des travaux de l’Agent SQL Server sur Linux à l’aide de Transact-SQL et SQL Server Management Studio (SSMS).

Pour les problèmes connus avec l’Agent SQL Server dans cette version, consultez le [Release Notes](sql-server-linux-release-notes.md).

## <a name="prerequisites"></a>Configuration requise 
Pour créer et exécuter des travaux, vous devez d’abord installer le service de l’Agent SQL Server. Pour obtenir des instructions d’installation, consultez le [rubrique installation de l’Agent SQL Server](sql-server-linux-setup-sql-agent.md).

## <a name="create-a-job-with-transact-sql"></a>Créer un travail avec Transact-SQL

Les étapes suivantes fournissent un exemple montrant comment créer un travail de l’Agent SQL Server sur Linux avec les commandes Transact-SQL. Ces travaux dans cet exemple s’exécute une sauvegarde quotidienne sur une base de données exemple `SampleDB`. 


> [!TIP]
> Vous pouvez utiliser n’importe quel client de T-SQL pour exécuter ces commandes. Par exemple, sur Linux, vous pouvez utiliser [sqlcmd](sql-server-linux-setup-tools.md) ou [Visual Studio Code](sql-server-linux-develop-use-vscode.md). À partir d’un serveur à distance de Windows, vous pouvez également exécuter des requêtes dans SQL Server Management Studio (SSMS) ou utiliser l’interface utilisateur pour la gestion des travaux, qui est décrit dans la section suivante.

1. **Créer le travail**. L’exemple suivant utilise [sp_add_job](https://msdn.microsoft.com/library/ms182079.aspx) pour créer une tâche nommée `Daily AdventureWorks Backup`.

    ```tsql
     -- Adds a new job executed by the SQLServerAgent service 
     -- called 'Daily SampleDB Backup'  
     CREATE DATABASE SampleDB
     USE msdb ;  
     GO  
     EXEC dbo.sp_add_job  
         @job_name = N'Daily SampleDB Backup' ;  
     GO

    ```

2. **Ajouter un ou plusieurs étapes de travail**. Le script Transact-SQL suivant utilise [sp_add_jobstep](https://msdn.microsoft.com/library/ms187358.aspx) pour créer une étape de travail qui crée une sauvegarde de la `AdventureWlorks2014` base de données.

    ```tsql
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

3. **Créer une planification de travail**. Cet exemple utilise [sp_add_schedule](https://msdn.microsoft.com/library/ms366342.aspx) pour créer une planification quotidienne de la tâche.

    ```tsql
    -- Creates a schedule called 'Daily'  
    EXEC dbo.sp_add_schedule  
     @schedule_name = N'Daily SampleDB',  
     @freq_type = 4,  
     @freq_interval = 1,
     @active_start_time = 233000 ;  
   USE msdb ;  
   GO
    ```

4. **Attachez la planification du travail pour la tâche**. Utilisez [sp_attach_schedule](https://msdn.microsoft.com/library/ms186766.aspx) pour attacher la planification du travail pour la tâche.

    ```tsql
    -- Sets the 'Daily' schedule to the 'Daily AdventureWorks Backup' Job  
    EXEC sp_attach_schedule  
     @job_name = N'Daily SampleDB Backup',  
     @schedule_name = N'Daily SampleDB';  
    GO
    ```

5. **Affecter le travail sur un serveur cible**. Affecter le travail à un serveur cible avec [sp_add_jobserver](https://msdn.microsoft.com/library/ms178625.aspx). Dans cet exemple, le serveur local est la cible.

    ```tsql
    EXEC dbo.sp_add_jobserver  
     @job_name = N'Daily SampleDB Backup',  
     @server_name = N'(LOCAL)';  
    GO
    ```
6. **Démarrer le travail**. 

    ```tsql
    EXEC dbo.sp_start_job N' Daily SampleDB Backup' ;
    GO
    ```
## <a name="create-a-job-with-ssms"></a>Créer une tâche avec SSMS

Vous pouvez également créer et gérer des travaux à distance à l’aide de SQL Server Management Studio (SSMS) sur Windows.

1. **Démarrez SSMS sur Windows et connectez-vous à votre instance de SQL Server de Linux.** Pour plus d’informations, consultez [gérer SQL Server sur Linux avec SSMS](sql-server-linux-develop-use-ssms.md).

1. **Créer une base de données appelée SampleDB**.

   <img src="./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-0.png" alt="Create a SampleDB database" style="width: 550px;"/>

2. **Vérifiez que l’Agent SQL a été installé et configuré correctement.** Recherchez le signe plus en regard de l’Agent SQL Server dans l’Explorateur d’objets. Si l’Agent SQL Server n’est pas installé, consultez [installer l’Agent SQL Server sur Linux](sql-server-linux-setup-sql-agent.md).

    ![Vérifiez que l’Agent SQL Server a été installé.](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-1.png)


3. **Créer un nouveau travail.**

    ![Créer un nouveau travail](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-2.png)


4. **Donnez un nom à votre travail et créer votre étape de travail.**

    ![Créer une étape de travail](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-3.png)


5. **Spécifier le sous-système dans lequel vous souhaitez utiliser et l’action que doit effectuer l’étape de travail.**

    ![Sous-système de travail](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-4.png)

    ![Action d’étape de travail](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-5.png)

6. **Créer une nouvelle planification du travail.**

    ![Planification du travail](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-6.png)
  
    ![Planification du travail](./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-8.png)

7. **Démarrez votre travail.**

   <img src="./media/sql-server-linux-run-sql-server-agent-job/ssms-agent-9.png" alt="Start the SQL Server Agent job" style="width: 550px;"/>

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur la création et la gestion des travaux de l’Agent SQL Server, consultez [l’Agent SQL Server](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent).


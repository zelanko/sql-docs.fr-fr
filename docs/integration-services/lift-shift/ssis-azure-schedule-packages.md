---
title: "Planifier l’exécution du package SSIS sur Azure | Documents Microsoft"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2f28400200105e8e63f787cbcda58c183ba00da5
ms.openlocfilehash: 2130e68d5e29671a2881d8762666cf852ff51259
ms.contentlocale: fr-fr
ms.lasthandoff: 10/18/2017

---
# <a name="schedule-the-execution-of-an-ssis-package-on-azure"></a>Planifier l’exécution d’un package SSIS sur Azure
Vous pouvez planifier l’exécution des packages stockés dans la base de données de catalogue SSISDB sur un serveur de base de données SQL Azure en choisissant une des options de planification suivantes :
-   [Agent SQL Server](#agent)
-   [Travaux élastique de base de données SQL](#elastic)
-   [L’activité de procédure stockée Azure données fabrique SQL Server](#sproc)

## <a name="agent"></a>Planifier un package avec l’Agent SQL Server

### <a name="prerequisite"></a>Condition préalable

Avant de pouvoir utiliser l’Agent SQL Server sur site pour planifier l’exécution des packages stockés sur un serveur de base de données SQL Azure, vous devez ajouter le serveur de base de données SQL comme serveur lié. Pour plus d’informations, consultez [créer des serveurs liés](../../relational-databases/linked-servers/create-linked-servers-sql-server-database-engine.md) et [des serveurs liés](../../relational-databases/linked-servers/linked-servers-database-engine.md).

### <a name="create-a-sql-server-agent-job"></a>Créer un travail de l’Agent SQL Server

Pour planifier un package avec l’Agent SQL Server sur site, de créer une tâche avec une étape de travail qui appelle le catalogue SSIS procédures stockées `[catalog].[create_execution]` , puis `[catalog].[start_execution]`. Pour plus d’informations, consultez [travaux de l’Agent SQL Server pour les Packages](../packages/sql-server-agent-jobs-for-packages.md).

1.  Dans SQL Server Management Studio, connectez-vous à la base de données SQL Server sur site sur lequel vous souhaitez créer le travail.

2.  Avec le bouton droit sur le **l’Agent SQL Server** nœud, sélectionnez **nouveau**, puis sélectionnez **travail** pour ouvrir le **nouveau travail** boîte de dialogue.

3.  Dans le **nouveau travail** boîte de dialogue, sélectionnez le **étapes** page, puis sélectionnez **nouveau** pour ouvrir le **nouvelle étape du travail** boîte de dialogue.

4.  Dans le **nouvelle étape du travail** boîte de dialogue, sélectionnez `SSISDB` comme le **base de données.**

5.  Dans le champ de la commande, entrez un script Transact-SQL similaire au script indiqué dans l’exemple suivant :

    ```sql
    DECLARE @return_value int, @exe_id bigint 

    EXEC @return_value = [YourLinkedServer].[SSISDB].[catalog].[create_execution] 
    @folder_name=N'folderName', @project_name=N'projectName', 
    @package_name=N'packageName', @use32bitruntime=0, 
    @runinscaleout=1, @useanyworker=1, @execution_id=@exe_id OUTPUT 
 
    EXEC [YourLinkedServer].[SSISDB].[catalog].[start_execution] @execution_id=@exe_id

    GO
    ```

6.  Terminer la configuration et de planification du travail.

## <a name="elastic"></a>Planifier un package avec des travaux élastique de base de données SQL

Pour plus d’informations sur les tâches élastiques de base de données SQL, consultez [bases de données de gestion à grande échelle cloud](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-elastic-jobs-overview).

### <a name="prerequisites"></a>Conditions préalables

Avant de pouvoir utiliser les travaux élastiques pour planifier les packages SSIS stockés dans la base de données de catalogue SSISDB sur un serveur de base de données SQL Azure, vous devez effectuer les opérations suivantes :

1.  Installer et configurer les composants de tâches de base de données élastique. Pour plus d’informations, consultez [vue d’ensemble des travaux de l’installation de la base de données élastique](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-elastic-jobs-service-installation).

2. Créer une étendue de base de données d’informations d’identification que travaux peuvent utiliser pour envoyer des commandes à la base de données du catalogue SSIS. Pour plus d’informations, consultez [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md).

### <a name="create-an-elastic-job"></a>Créer un travail élastique

Créer le travail à l’aide d’un script Transact-SQL similaire au script indiqué dans l’exemple suivant :

```sql
-- Create Elastic Jobs target group 
EXEC jobs.sp_add_target_group 'TargetGroup' 

-- Add Elastic Jobs target group member 
EXEC jobs.sp_add_target_group_member @target_group_name='TargetGroup', 
    @target_type='SqlDatabase', @server_name='YourSQLDBServer.database.windows.net',
    @database_name='SSISDB' 

-- Add a job to schedule SSIS package execution
EXEC jobs.sp_add_job @job_name='ExecutePackageJob', @description='Description', 
    @schedule_interval_type='Minutes', @schedule_interval_count=60

-- Add a job step to create/start SSIS package execution using SSISDB catalog stored procedures
EXEC jobs.sp_add_jobstep @job_name='ExecutePackageJob', 
    @command=N'DECLARE @exe_id bigint 
        EXEC [SSISDB].[catalog].[create_execution]
            @folder_name=N''folderName'', @project_name=N''projectName'',
            @package_name=N''packageName'', @use32bitruntime=0,
            @runinscaleout=1, @useanyworker=1, 
            @execution_id=@exe_id OUTPUT         
        EXEC [SSISDB].[catalog].[start_execution] @exe_id, @retry_count=0', 
    @credential_name='YourDBScopedCredentials', 
    @target_group_name='TargetGroup' 

-- Enable the job schedule 
EXEC jobs.sp_update_job @job_name='ExecutePackageJob', @enabled=1, 
    @schedule_interval_type='Minutes', @schedule_interval_count=60 
```

## <a name="sproc"></a>Planifier un package avec l’activité de procédure stockée Azure données fabrique SQL Server

> [!IMPORTANT]
> Utilisez les scripts JSON dans l’exemple suivant, avec la version 1 Azure Data Factory activité de procédure stockée.

Pour planifier un package avec l’activité de procédure stockée Azure données fabrique SQL Server, procédez comme suit :

1.  Créer une fabrique de données.

2.  Créer un service lié pour la base de données SQL qui héberge SSISDB.

3.  Créez un dataset de sortie qui gère la planification.

4.  Créer un pipeline de fabrique de données qui utilise l’activité de procédure stockée SQL Server pour exécuter le package SSIS.

Cette section fournit une vue d’ensemble de ces étapes. Un didacticiel complet de la fabrique de données est dépasse le cadre de cet article. Pour plus d’informations, consultez [activité de la procédure stockée SQL Server](https://docs.microsoft.com/en-us/azure/data-factory/data-factory-stored-proc-activity).

### <a name="created-a-linked-service-for-the-sql-database-that-hosts-ssisdb"></a>Création d’un service lié pour la base de données SQL qui héberge SSISDB
Service lié Data Factory permet de se connecter à SSISDB.

```json
{
    "name": "AzureSqlLinkedService",
    "properties": {
        "description": "",
        "type": "AzureSqlDatabase",
        "typeProperties": {
            "connectionString": "Data Source = tcp: YourSQLDBServer.database.windows.net, 1433; Initial Catalog = SSISDB; User ID = YourUsername; Password = YourPassword; Integrated Security = False; Encrypt = True; Connect Timeout = 30"
        }
    }
}
```

### <a name="create-an-output-dataset"></a>Créez un dataset de sortie
Le dataset de sortie contient les informations de planification.

```json
{
    "name": "sprocsampleout",
    "properties": {
        "type": "AzureSqlTable",
        "linkedServiceName": "AzureSqlLinkedService",
        "typeProperties": {
            "tableName": "sampletable"
        },
        "availability": {
            "frequency": "Hour",
            "interval": 1
        }
    }
}
```
### <a name="create-a-data-factory-pipeline"></a>Créer un pipeline Azure Data Factory
Le pipeline utilise l’activité de procédure stockée SQL Server pour exécuter le package SSIS.

```json
{
    "name": "SprocActivitySamplePipeline",
    "properties": {
        "activities": [{
            "name": "SprocActivitySample",
            "type": "SqlServerStoredProcedure",
            "typeProperties": {
                "storedProcedureName": "sp_executesql",
                "storedProcedureParameters": {
                    "stmt": "Transact-SQL script to create and start SSIS package execution using SSISDB catalog stored procedures"
                }
            },
            "outputs": [{
                "name": "sprocsampleout"
            }],
            "scheduler": {
                "frequency": "Hour",
                "interval": 1
            }
        }],
        "start": "2017-10-01T00:00:00Z",
        "end": "2017-10-01T05:00:00Z",
        "isPaused": false
    }
}
```

Vous n’êtes pas obligé de créer une nouvelle procédure stockée pour encapsuler les commandes Transact-SQL nécessaires pour créer et démarrer l’exécution du package SSIS. Vous pouvez fournir la totalité du script en tant que la valeur de le `stmt` paramètre dans l’exemple précédent de JSON. Voici un exemple de script :

```sql
-- T-SQL script to create and start SSIS package execution using SSISDB catalog stored procedures
DECLARE @return_value INT,@exe_id BIGINT,@err_msg NVARCHAR(150)

-- Create the exectuion
EXEC @return_value=[SSISDB].[catalog].[create_execution] @folder_name=N'folderName', @project_name=N'projectName', @package_name=N'packageName', @use32bitruntime=0, @runinscaleout=1,@useanyworker=1, @execution_id=@exe_id OUTPUT

-- To synchronize SSIS package execution, set the SYNCHRONIZED execution parameter
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @exe_id, @object_type=50, @parameter_name=N'SYNCHRONIZED', @parameter_value=1

-- Start the execution                                                         
EXEC [SSISDB].[catalog].[start_execution] @execution_id=@exe_id,@retry_count=0
                                          
-- Raise an error for unsuccessful package execution
-- Execution status values include the following:
-- created (1)
-- running (2)
-- canceled (3)
-- failed (4)
-- pending (5)
-- ended unexpectedly (6)
-- succeeded (7)
-- stopping (8)
-- completed (9) 
IF(SELECT [status]
   FROM [SSISDB].[catalog].[executions]
   WHERE execution_id=@exe_id)<>7
BEGIN
    SET @err_msg=N'Your package execution did not succeed for execution ID: ' + CAST(@exe_id AS NVARCHAR(20))
    RAISERROR(@err_msg,15,1)
END
GO
```

Pour plus d’informations sur le code de ce script, consultez [déployer et exécuter des Packages SSIS à l’aide de procédures stockées](../packages/deploy-integration-services-ssis-projects-and-packages.md#deploy-and-execute-ssis-packages-using-stored-procedures).

## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur l’Agent SQL Server, consultez [travaux de l’Agent SQL Server pour les Packages](../packages/sql-server-agent-jobs-for-packages.md).

Pour plus d’informations sur les tâches élastiques de base de données SQL, consultez [bases de données de gestion à grande échelle cloud](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-elastic-jobs-overview).


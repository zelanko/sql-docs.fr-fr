---
title: "Planifier l’exécution d’un package SSIS sur Azure | Microsoft Docs"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: lift-shift
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d0b8dbc635523b33a480ad887b73d9f395d71c8d
ms.sourcegitcommit: ffa4ce9bd71ecf363604966c20cbd2710d029831
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2017
---
# <a name="schedule-the-execution-of-an-ssis-package-on-azure"></a>Planifier l’exécution d’un package SSIS sur Azure
Vous pouvez planifier l’exécution de packages stockés dans la base de données de catalogues SSISDB sur un serveur Azure SQL Database en choisissant l’une des options de planification suivantes :
-   [Agent SQL Server](#agent)
-   [Travaux élastiques SQL Database](#elastic)
-   [Activité de procédure stockée SQL Server Azure Data Factory](#sproc)

## <a name="agent"></a> Planifier un package avec SQL Server Agent

### <a name="prerequisite"></a>Condition préalable

Avant de pouvoir utiliser SQL Server Agent localement pour planifier l’exécution des packages stockés sur un serveur Azure SQL Database, vous devez ajouter le serveur SQL Database en tant que serveur lié. Pour plus d’informations, consultez [Créer des serveurs liés](../../relational-databases/linked-servers/create-linked-servers-sql-server-database-engine.md) et [Serveurs liés](../../relational-databases/linked-servers/linked-servers-database-engine.md).

### <a name="create-a-sql-server-agent-job"></a>Créer un travail de SQL Server Agent

Pour planifier un package avec SQL Server Agent localement, créez un travail avec une étape de travail qui appelle les procédures stockées du catalogue SSIS `[catalog].[create_execution]`, puis `[catalog].[start_execution]`. Pour plus d’informations, consultez [Travaux de SQL Server Agent pour les packages](../packages/sql-server-agent-jobs-for-packages.md).

1.  Dans SQL Server Management Studio, connectez-vous à la base de données SQL Server locale sur laquelle vous souhaitez créer le travail.

2.  Cliquez avec le bouton droit sur le nœud **SQL Server Agent**, sélectionnez **Nouveau**, puis **Travail** pour ouvrir la boîte de dialogue **Nouveau travail**.

3.  Dans la boîte de dialogue **Nouveau travail**, sélectionnez la page **Étapes**, puis **Nouveau** pour ouvrir la boîte de dialogue **Nouvelle étape du travail**.

4.  Dans la boîte de dialogue **Nouvelle étape du travail**, sélectionnez `SSISDB` en tant que **Base de données**.

5.  Dans le champ de commande, entrez un script Transact-SQL similaire au script indiqué dans l’exemple suivant :

    ```sql
    DECLARE @return_value int, @exe_id bigint 

    EXEC @return_value = [YourLinkedServer].[SSISDB].[catalog].[create_execution] 
    @folder_name=N'folderName', @project_name=N'projectName', 
    @package_name=N'packageName', @use32bitruntime=0, 
    @runinscaleout=1, @useanyworker=1, @execution_id=@exe_id OUTPUT 
 
    EXEC [YourLinkedServer].[SSISDB].[catalog].[start_execution] @execution_id=@exe_id

    GO
    ```

6.  Finissez de configurer et de planifier le travail.

## <a name="elastic"></a> Planifier un package avec des travaux élastiques SQL Database

Pour plus d’informations sur les travaux élastiques SQL Database, consultez [Gestion des bases de données cloud avec augmentation de la taille des instances](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-jobs-overview).

### <a name="prerequisites"></a>Conditions préalables

Pour pouvoir utiliser des travaux élastiques afin de planifier des packages SSIS stockés dans la base de données de catalogues SSISDB sur un serveur Azure SQL Database, vous devez effectuer les actions suivantes :

1.  Installez et configurez les tâches de base de données élastique. Pour plus d’informations, consultez [Vue d’ensemble de l’installation des tâches de base de données élastique](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-jobs-service-installation).

2. Créez des informations d’identification au niveau de la base de données pour permettre aux travaux d’envoyer des commandes à la base de données de catalogues SSIS. Pour plus d’informations, consultez [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md).

### <a name="create-an-elastic-job"></a>Créer un travail élastique

Créez le travail à l’aide d’un script Transact-SQL similaire au script indiqué dans l’exemple suivant :

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

## <a name="sproc"></a> Planifier un package avec l’activité de procédure stockée SQL Server Azure Data Factory

> [!IMPORTANT]
> Utilisez les scripts JSON de l’exemple suivant avec l’activité de procédure stockée Azure Data Factory version 1.

Pour planifier un package avec l’activité de procédure stockée SQL Server Azure Data Factory, effectuez les actions suivantes :

1.  Créez une fabrique Data Factory.

2.  Créez un service lié pour l’instance SQL Database qui héberge SSISDB.

3.  Créez un jeu de données de sortie qui gère la planification.

4.  Créez un pipeline Data Factory qui utilise l’activité de procédure stockée SQL Server pour exécuter le package SSIS.

Cette section fournit une vue d’ensemble de ces étapes. La description complète du didacticiel Data Factory dépasse le cadre de cet article. Pour plus d’informations, consultez [Activité de procédure stockée SQL Server](https://docs.microsoft.com/azure/data-factory/data-factory-stored-proc-activity).

Si une exécution planifiée échoue et que l’activité de la procédure stockée ADF fournit un ID d’exécution pour l’exécution qui a échoué, vérifiez le rapport d’exécution pour cet ID dans SSMS, dans le catalogue SSIS.

### <a name="created-a-linked-service-for-the-sql-database-that-hosts-ssisdb"></a>Créer un service lié pour l’instance SQL Database qui héberge SSISDB
Le service lié permet à Data Factory de se connecter à SSISDB.

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

### <a name="create-an-output-dataset"></a>Créer un jeu de données de sortie
Le jeu de données de sortie contient les informations de planification.

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
### <a name="create-a-data-factory-pipeline"></a>Créer un pipeline Data Factory
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

Vous n’avez pas à créer de procédure stockée pour encapsuler les commandes Transact-SQL permettant de créer et de démarrer l’exécution du package SSIS. Vous pouvez fournir la totalité du script en tant que valeur du paramètre `stmt` dans l’exemple JSON précédent. Voici un exemple de script :

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

Pour fournir le script SQL montré ci-dessus comme valeur du paramètre `stmt`, vous devez en général inclure la totalité du script sur une seule ligne, comme illustré dans l’exemple suivant. (Le [standard JSON](https://json.org/) ne prend pas en charge les caractères de contrôle, notamment le caractère de contrôle de nouvelle ligne `\n` utilisé dans d’autres langages pour séparer les lignes dans une chaîne multiligne.)

```json
{
    "name": "SprocActivitySamplePipeline",
    "properties": {
        "activities": [
            {
                "type": "SqlServerStoredProcedure",
                "typeProperties": {
                    "storedProcedureName": "sp_executesql",
                    "storedProcedureParameters": {
                        "stmt": "DECLARE @return_value INT, @exe_id BIGINT, @err_msg NVARCHAR(150)    EXEC @return_value=[SSISDB].[catalog].[create_execution] @folder_name=N'test', @project_name=N'TestProject', @package_name=N'STestPackage.dtsx', @use32bitruntime=0, @runinscaleout=1, @useanyworker=1, @execution_id=@exe_id OUTPUT    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @exe_id, @object_type=50, @parameter_name=N'SYNCHRONIZED', @parameter_value=1    EXEC [SSISDB].[catalog].[start_execution] @execution_id=@exe_id, @retry_count=0    IF(SELECT [status] FROM [SSISDB].[catalog].[executions] WHERE execution_id=@exe_id)<>7 BEGIN SET @err_msg=N'Your package execution did not succeed for execution ID: ' + CAST(@exe_id AS NVARCHAR(20)) RAISERROR(@err_msg,15,1) END"
                    }
                },
                "outputs": [
                    {
                        "name": "sprocsampleout"
                    }
                ],
                "scheduler": {
                    "frequency": "Minute",
                    "interval": 15
                },
                "name": "SprocActivitySample"
            }
        ],
        "start": "2017-12-06T12:00:00Z",
        "end": "2017-12-06T12:30:00Z",
        "isPaused": false,
        "hubName": "test_hub",
        "pipelineMode": "Scheduled"
    }
}
```

Pour plus d’informations sur le code de ce script, consultez [Déployer et exécuter des packages SSIS à l’aide de procédures stockées](../packages/deploy-integration-services-ssis-projects-and-packages.md#deploy-and-execute-ssis-packages-using-stored-procedures).

## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur SQL Server Agent, consultez [Travaux de SQL Server Agent pour les packages](../packages/sql-server-agent-jobs-for-packages.md).

Pour plus d’informations sur les travaux élastiques SQL Database, consultez [Gestion des bases de données cloud avec augmentation de la taille des instances](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-jobs-overview).

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
ms.openlocfilehash: 26160f982982b1a8163662f57cb317e7252ab0e4
ms.sourcegitcommit: 6e016a4ffd28b09456008f40ff88aef3d911c7ba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2017
---
# <a name="schedule-the-execution-of-an-ssis-package-on-azure"></a>Planifier l’exécution d’un package SSIS sur Azure
Vous pouvez planifier l’exécution de packages stockés dans la base de données de catalogues SSISDB sur un serveur Azure SQL Database en choisissant l’une des options de planification suivantes :
-   [SQL Server Agent](#agent)
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

### <a name="prerequisites"></a>Prerequisites

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

Pour plus d’informations sur la façon de planifier un package SSIS à l’aide de l’activité de procédure stockée Azure Data Factory, consultez les articles suivants :

-   Pour Data Factory version 2 : [Appeler un package SSIS à l’aide de l’activité de procédure stockée dans Azure Data Factory](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-stored-procedure-activity)

-   Pour Data Factory version 1 : [Appeler un package SSIS à l’aide de l’activité de procédure stockée dans Azure Data Factory](https://docs.microsoft.com/azure/data-factory/v1/how-to-invoke-ssis-package-stored-procedure-activity)

## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur SQL Server Agent, consultez [Travaux de SQL Server Agent pour les packages](../packages/sql-server-agent-jobs-for-packages.md).

Pour plus d’informations sur les travaux élastiques SQL Database, consultez [Gestion des bases de données cloud avec augmentation de la taille des instances](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-jobs-overview).

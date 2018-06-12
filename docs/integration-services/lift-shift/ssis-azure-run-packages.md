---
title: Exécuter des packages SSIS dans Azure | Microsoft Docs
ms.description: Provides an overview of the available methods for running packages deployed to Azure SQL Database.
ms.date: 05/29/2018
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.component: lift-shift
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e4d733b49f8353fc430f90161ef25c352c8cac8f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34586084"
---
# <a name="run-an-ssis-package-in-azure"></a>Exécuter un package SSIS dans Azure

Choisissez l’une des options décrites dans cet article pour exécuter des packages SSIS déployés sur la base de données de catalogue SSISDB sur un serveur Azure SQL Database. Vous pouvez exécuter un package directement ou dans le cadre d’un pipeline Azure Data Factory. Pour obtenir une vue d’ensemble de SSIS sur Azure, consultez [Effectuer un « lift-and-shift » des charges de travail SQL Server Integration Services vers le cloud](ssis-azure-lift-shift-ssis-packages-overview.md).

- Exécuter un package directement

  - [Exécuter avec SSMS](#ssms)

  - [Exécuter avec des procédures stockées](#sproc)

  - [Exécuter avec un script ou du code](#script)

- Exécuter un package dans le cadre d’un pipeline Azure Data Factory

  - [Exécuter avec l’activité Exécuter le package SSIS](#exec_activity)

  - [Exécuter avec l’activité Procédure stockée](#sproc_activity)

> [!NOTE]
> L’exécution d’un package avec `dtexec.exe` n’a pas été testée avec les packages déployés sur Azure.

## <a name="ssms"></a> Exécuter un package avec SSMS

Dans SSMS (SQL Server Management Studio), vous pouvez cliquer avec le bouton droit sur un package déployé sur la base de données du catalogue SSIS, SSISDB, puis sélectionner **Exécuter** pour ouvrir la boîte de dialogue **Exécuter le package**. Pour plus d’informations, consultez [Exécuter un package SSIS avec SQL Server Management Studio (SSMS)](../ssis-quickstart-run-ssms.md).

## <a name="sproc"></a> Exécuter des packages avec des procédures stockées

Dans tout environnement à partir duquel vous pouvez vous connecter à Azure SQL Database et exécuter du code Transact-SQL, vous pouvez exécuter un package en appelant les procédures stockées suivantes :

1. **[catalog].[create_execution]**. Pour plus d’informations, consultez [catalog.create_execution](../system-stored-procedures/catalog-create-execution-ssisdb-database.md).

2. **[catalog].[set_execution_parameter_value]**. Pour plus d’informations, consultez [catalog.set_execution_parameter_value](../system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md).

3. **[catalog].[start_execution]**. Pour plus d’informations, consultez [catalog.start_execution](../system-stored-procedures/catalog-start-execution-ssisdb-database.md).

Pour plus d’informations, consultez les exemples suivants :

- [Exécuter un package SSIS à partir de SSMS avec Transact-SQL](../ssis-quickstart-run-tsql-ssms.md)

- [Exécuter un package SSIS à partir de Visual Studio Code avec Transact-SQL](../ssis-quickstart-run-tsql-vscode.md)

## <a name="script"></a> Exécuter un package avec un script ou du code

Dans tout environnement de développement à partir duquel vous pouvez appeler une API managée, vous pouvez exécuter un package en appelant la méthode `Execute` de l’objet `Package` dans l’espace de noms `Microsoft.SQLServer.Management.IntegrationServices`.

Pour plus d’informations, consultez les exemples suivants :

- [Exécuter un package SSIS avec PowerShell](../ssis-quickstart-run-powershell.md)

- [Exécuter un package SSIS avec du code C# dans une application .NET](../ssis-quickstart-run-dotnet.md)

## <a name="exec_activity"></a> Exécuter un package avec l’activité Exécuter le package SSIS

Pour plus d’informations, consultez [Exécuter un package SSIS à l’aide de l’activité Exécuter le package SSIS dans Azure Data Factory](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity).

## <a name="sproc_activity"></a> Exécuter un package avec l’activité Procédure stockée

Pour plus d’informations, consultez [Exécuter un package SSIS à l’aide de l’activité Procédure stockée dans Azure Data Factory](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-stored-procedure-activity).

## <a name="next-steps"></a>Étapes suivantes

Découvrez les options disponibles pour planifier des packages SSIS déployés sur Azure. Pour plus d’informations, consultez [Planifier l’exécution d’un package SSIS dans Azure](ssis-azure-schedule-packages.md).
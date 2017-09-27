---
title: "Déployer un projet SSIS avec PowerShell | Documents Microsoft"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: 656e62f36446db4ef5b232129130a0253d2aebdf
ms.openlocfilehash: 37fe358eb7e11cb878ebd9b0c8356ac2295ca7e9
ms.contentlocale: fr-fr
ms.lasthandoff: 09/22/2017

---
# <a name="deploy-an-ssis-project-with-powershell"></a>Déployer un projet SSIS avec PowerShell
Ce didacticiel de démarrage rapide montre comment utiliser un script PowerShell pour vous connecter à un serveur de base de données et de déployer un projet SSIS dans le catalogue SSIS.

## <a name="powershell-script"></a>Script PowerShell
Entrez les valeurs appropriées pour les variables en haut du script suivant, puis exécutez le script pour déployer le projet SSIS.

> [!NOTE]
> L’exemple suivant utilise l’authentification Windows. Pour utiliser l’authentification SQL Server, remplacez le `Integrated Security=SSPI;` argument avec `User ID=<user name>;Password=<password>;`.

```powershell
# Variables
$SSISNamespace = "Microsoft.SqlServer.Management.IntegrationServices"
$TargetServerName = "localhost"
$TargetFolderName = "Project1Folder"
$ProjectFilePath = "C:\Projects\Integration Services Project1\Integration Services Project1\bin\Development\Integration Services Project1.ispac"
$ProjectName = "Integration Services Project1"

# Load the IntegrationServices assembly
$loadStatus = [System.Reflection.Assembly]::Load("Microsoft.SQLServer.Management.IntegrationServices, "+
    "Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91, processorArchitecture=MSIL")

# Create a connection to the server
$sqlConnectionString = `
    "Data Source=" + $TargetServerName + ";Initial Catalog=master;Integrated Security=SSPI;"
$sqlConnection = New-Object System.Data.SqlClient.SqlConnection $sqlConnectionString

# Create the Integration Services object
$integrationServices = New-Object $SSISNamespace".IntegrationServices" $sqlConnection

# Get the Integration Services catalog
$catalog = $integrationServices.Catalogs["SSISDB"]

# Create the target folder
$folder = New-Object $SSISNamespace".CatalogFolder" ($catalog, $TargetFolderName,
    "Folder description")
$folder.Create()

Write-Host "Deploying " $ProjectName " project ..."

# Read the project file and deploy it
[byte[]] $projectFile = [System.IO.File]::ReadAllBytes($ProjectFilePath)
$folder.DeployProject($ProjectName, $projectFile)

Write-Host "Done."
```

## <a name="next-steps"></a>Étapes suivantes
- Envisagez d’autres méthodes pour déployer un package.
    - [Déployer un package SSIS avec SSMS](./ssis-quickstart-deploy-ssms.md)
    - [Déployer un package SSIS avec Transact-SQL (SSMS)](./ssis-quickstart-deploy-tsql-ssms.md)
    - [Déployer un package SSIS avec Transact-SQL (Code de Visual Studio)](ssis-quickstart-deploy-tsql-vscode.md)
    - [Déployer un package SSIS à partir de l’invite de commandes](./ssis-quickstart-deploy-cmdline.md)
    - [Déployer un package SSIS avec c#](./ssis-quickstart-deploy-dotnet.md) 
- Exécuter un package déployé. Pour exécuter un package, vous pouvez choisir à partir de plusieurs outils et langages. Pour plus d’informations, consultez les articles suivants :
    - [Exécutez un package SSIS avec SSMS](./ssis-quickstart-run-ssms.md)
    - [Exécutez un package SSIS avec Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Exécutez un package SSIS avec Transact-SQL (Code de Visual Studio)](ssis-quickstart-run-tsql-vscode.md)
    - [Exécutez un package SSIS à partir de l’invite de commandes](./ssis-quickstart-run-cmdline.md)
    - [Exécuter un package SSIS avec PowerShell](ssis-quickstart-run-powershell.md)
    - [Exécutez un package SSIS avec c#](./ssis-quickstart-run-dotnet.md) 


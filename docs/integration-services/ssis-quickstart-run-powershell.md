---
title: "Exécuter un package SSIS avec PowerShell | Documents Microsoft"
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
ms.openlocfilehash: d392ac49442ef0f04961908fff7acf553fa1aa57
ms.contentlocale: fr-fr
ms.lasthandoff: 09/22/2017

---
# <a name="run-an-ssis-package-with-powershell"></a>Exécuter un package SSIS avec PowerShell
Ce didacticiel de démarrage rapide montre comment utiliser un script PowerShell pour vous connecter à un serveur de base de données et exécutez un package SSIS.

## <a name="powershell-script"></a>Script PowerShell
Entrez les valeurs appropriées pour les variables en haut du script suivant, puis exécutez le script pour exécuter le package SSIS.

> [!NOTE]
> L’exemple suivant utilise l’authentification Windows. Pour utiliser l’authentification SQL Server, remplacez le `Integrated Security=SSPI;` argument avec `User ID=<user name>;Password=<password>;`.

```powershell
# Variables
$SSISNamespace = "Microsoft.SqlServer.Management.IntegrationServices"
$TargetServerName = "localhost"
$TargetFolderName = "Project1Folder"
$ProjectName = "Integration Services Project1"
$PackageName = "Package.dtsx"

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

# Get the folder
$folder = $catalog.Folders[$TargetFolderName]

# Get the project
$project = $folder.Projects[$ProjectName]

# Get the package
$package = $project.Packages[$PackageName]

Write-Host "Running " $PackageName "..."

$result = $package.Execute("false", $null)

Write-Host "Done."
```

## <a name="next-steps"></a>Étapes suivantes
- Envisagez d’autres méthodes pour exécuter un package.
    - [Exécutez un package SSIS avec SSMS](./ssis-quickstart-run-ssms.md)
    - [Exécutez un package SSIS avec Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Exécutez un package SSIS avec Transact-SQL (Code de Visual Studio)](ssis-quickstart-run-tsql-vscode.md)
    - [Exécutez un package SSIS à partir de l’invite de commandes](./ssis-quickstart-run-cmdline.md)
    - [Exécutez un package SSIS avec c#](./ssis-quickstart-run-dotnet.md) 


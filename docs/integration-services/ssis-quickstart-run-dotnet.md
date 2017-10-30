---
title: "Exécuter un projet SSIS avec le code .NET (c#) | Documents Microsoft"
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
ms.sourcegitcommit: 656e62f36446db4ef5b232129130a0253d2aebdf
ms.openlocfilehash: 65a8db27af80e5cd7001e9a8777dde3c59e9c55e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/22/2017

---
# <a name="run-an-ssis-package-with-c-code-in-a-net-app"></a>Exécutez un package SSIS avec le code c# dans une application .NET
Ce didacticiel de démarrage rapide montre comment écrire du code c# pour vous connecter à un serveur de base de données et exécutez un package SSIS.

Pour créer une application c#, vous pouvez utiliser Visual Studio, Visual Studio Code ou un autre outil de votre choix.

## <a name="prerequisites"></a>Conditions préalables

Avant de commencer, assurez-vous que vous avez Visual Studio ou de Code Visual Studio est installé. Télécharger l’édition Community gratuite de Visual Studio ou le libre Visual Studio Code, à partir de [téléchargements Visual Studio](https://www.visualstudio.com/downloads/).

> [!NOTE]
> Un serveur de base de données SQL Azure est à l’écoute sur le port 1433. Si vous essayez de vous connecter à un serveur de base de données SQL Azure à partir d’un pare-feu d’entreprise, ce port doit être ouvert dans le pare-feu d’entreprise pour vous connecter avec succès.

## <a name="get-the-connection-info-if-deployed-to-sql-database"></a>Obtenir les informations de connexion si déployé sur la base de données SQL

Si vos packages sont déployées sur une base de données SQL Azure, obtenir les informations de connexion que vous souhaitez vous connecter à la base de données du catalogue SSIS (SSISDB). Vous avez besoin des informations de nom et la connexion de serveur complet dans les procédures qui suivent.

1. Connectez-vous au [portail Azure](https://portal.azure.com/).
2. Sélectionnez **bases de données SQL** dans le menu de gauche, cliquez sur la base de données SSISDB sur le **bases de données SQL** page. 
3. Sur le **vue d’ensemble** pour votre base de données, vérifiez le nom du serveur complet. Pour afficher le **copie** option, pointez sur le nom du serveur. 
4. Si vous oubliez vos informations de connexion de serveur de base de données SQL Azure, accédez à la page du serveur de base de données SQL pour afficher le nom d’administrateur de serveur. Vous pouvez réinitialiser le mot de passe si nécessaire.
5. Cliquez sur **afficher les chaînes de connexion de base de données**.
6. Passez en revue le **ADO.NET** chaîne de connexion. L’exemple de code utilise un `SqlConnectionStringBuilder` pour recréer cette chaîne de connexion avec les valeurs des paramètres individuels que vous fournissez.

## <a name="create-a-new-visual-studio-project"></a>Créez un projet Visual Studio

1. Dans Visual Studio, choisissez **fichier**, **nouveau**, **projet**. 
2. Dans le **nouveau projet** boîte de dialogue, développez **Visual C#**.
3. Sélectionnez **application Console** et entrez *run_ssis_project* pour le nom du projet.
4. Cliquez sur **OK** pour créer et ouvrir le nouveau projet dans Visual Studio.

## <a name="add-references"></a>Ajouter des références
1. Dans l’Explorateur de solutions, cliquez sur le **références** et sélectionnez **ajouter une référence**. Le **Gestionnaire de références** boîte de dialogue s’ouvre.
2. Dans le **Gestionnaire de références** boîte de dialogue, développez **assemblys** et sélectionnez **Extensions**.
3. Sélectionnez les deux références suivantes à ajouter :
    -   Microsoft.SqlServer.Management.Sdk.Sfc
    -   Microsoft.SqlServer.Smo
4. Cliquez sur le **Parcourir** pour ajouter une référence à **Microsoft.SqlServer.Management.IntegrationServices**. (Cet assembly est installé uniquement dans le global assembly cache (GAC).) Le **sélectionner les fichiers à référencer** boîte de dialogue s’ouvre.
5. Dans le **sélectionner les fichiers à référencer** boîte de dialogue, accédez au dossier GAC qui contient l’assembly. En général, ce dossier est `C:\Windows\assembly\GAC_MSIL\Microsoft.SqlServer.Management.IntegrationServices\14.0.0.0__89845dcd8080cc91`.
6. Sélectionnez l’assembly (autrement dit, le fichier .dll) dans le dossier et cliquez sur **ajouter**.
7. Cliquez sur **OK** pour fermer la **Gestionnaire de références** boîte de dialogue zone et ajouter les références de trois. Pour vous assurer que les références sont, vérifiez le **références** liste dans l’Explorateur de solutions.

## <a name="add-the-c-code"></a>Ajoutez le code c# 
1. Ouvrez **Program.cs**.

2. Remplacez le contenu de **Program.cs** avec le code suivant. Ajoutez les valeurs appropriées pour votre serveur, une base de données, un utilisateur et un mot de passe.

> [!NOTE]
> L’exemple suivant utilise l’authentification Windows. Pour utiliser l’authentification SQL Server, remplacez le `Integrated Security=SSPI;` argument avec `User ID=<user name>;Password=<password>;`.


```csharp
using Microsoft.SqlServer.Management.IntegrationServices;
using System.Data.SqlClient;

namespace run_ssis_package
{
    class Program
    {
        static void Main(string[] args)
        {
            // Variables
            string targetServerName = "localhost";
            string folderName = "Project1Folder";
            string projectName = "Integration Services Project1";
            string packageName = "Package.dtsx";

            // Create a connection to the server
            string sqlConnectionString = "Data Source=" + targetServerName +
                ";Initial Catalog=master;Integrated Security=SSPI;";
            SqlConnection sqlConnection = new SqlConnection(sqlConnectionString);

            // Create the Integration Services object
            IntegrationServices integrationServices = new IntegrationServices(sqlConnection);

            // Get the Integration Services catalog
            Catalog catalog = integrationServices.Catalogs["SSISDB"];

            // Get the folder
            CatalogFolder folder = catalog.Folders[folderName];

            // Get the project
            ProjectInfo project = folder.Projects[projectName];

            // Get the package
            PackageInfo package = project.Packages[packageName];

            // Run the package
            package.Execute(false, null);

        }
    }
}
```

## <a name="run-the-code"></a>Exécutez le code

1. Pour exécuter l’application, appuyez sur **F5**.
2. Vérifier que le package exécuté comme prévu, puis fermez la fenêtre d’application.

## <a name="next-steps"></a>Étapes suivantes
- Envisagez d’autres méthodes pour exécuter un package.
    - [Exécutez un package SSIS avec SSMS](./ssis-quickstart-run-ssms.md)
    - [Exécutez un package SSIS avec Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Exécutez un package SSIS avec Transact-SQL (Code de Visual Studio)](ssis-quickstart-run-tsql-vscode.md)
    - [Exécutez un package SSIS à partir de l’invite de commandes](./ssis-quickstart-run-cmdline.md)
    - [Exécuter un package SSIS avec PowerShell](ssis-quickstart-run-powershell.md)


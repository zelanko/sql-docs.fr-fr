---
title: Exécuter un package SSIS avec Transact-SQL (SSMS) | Microsoft Docs
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: quick-start
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b72473635da4818ace7b888ee73e186f7d8ad7ed
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="run-an-ssis-package-from-ssms-with-transact-sql"></a>Exécuter un package SSIS à partir de SSMS avec Transact-SQL
Ce guide de démarrage rapide montre comment utiliser SQL Server Management Studio (SSMS) pour se connecter à la base de données du catalogue SSIS, puis utiliser des instructions Transact-SQL pour exécuter un package SSIS stocké dans le catalogue SSIS.

SQL Server Management Studio est un environnement intégré pour la gestion des infrastructures SQL, de SQL Server à SQL Database. Pour plus d’informations sur SSMS, consultez [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md).

## <a name="prerequisites"></a>Prerequisites

Avant de commencer, vérifiez que vous disposez de la dernière version de SQL Server Management Studio (SSMS). Pour télécharger SSMS, consultez [Télécharger SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="connect-to-the-ssisdb-database"></a>Se connecter à la base de données SSISDB

Utilisez SQL Server Management Studio pour établir une connexion au catalogue SSIS sur votre serveur Azure SQL Database. 

> [!NOTE]
> Un serveur Azure SQL Database écoute sur le port 1433. Si vous essayez de vous connecter à un serveur Azure SQL Database en étant derrière un pare-feu d’entreprise, ce port doit être ouvert dans le pare-feu d’entreprise pour que vous puissiez vous connecter.

1. Ouvrez SQL Server Management Studio.

2. Dans la boîte de dialogue **Se connecter au serveur**, entrez les informations suivantes :

   | Paramètre       | Valeur suggérée | En savoir plus | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Type de serveur** | Moteur de base de données | Cette valeur est requise. |
   | **Nom du serveur** | Nom complet du serveur | Si vous vous connectez à un serveur Azure SQL Database, le nom est au format suivant : `<server_name>.database.windows.net`. |
   | **Authentification** | Authentification SQL Server | Ce guide de démarrage rapide utilise l’authentification SQL. |
   | **Connexion** | Compte Administrateur du serveur | Il s’agit du compte que vous avez spécifié quand vous avez créé le serveur. |
   | **Mot de passe** | Mot de passe du compte Administrateur de votre serveur | Il s’agit du mot de passe que vous avez spécifié quand vous avez créé le serveur. |

3.  Cliquez sur **Se connecter**. La fenêtre Explorateur d’objets s’ouvre dans SSMS.

4. Dans l’Explorateur d’objets, développez **Catalogues Integration Services**, puis développez **SSISDB** pour afficher les objets de la base de données de catalogues SSIS.

## <a name="run-a-package"></a>Exécuter un package
Exécutez le code Transact-SQL suivant pour exécuter un package SSIS.

1.  Dans SSMS, ouvrez une nouvelle fenêtre de requête et collez le code suivant. (Ce code est le code généré par l’option **Script** dans la boîte de dialogue **Exécuter le package** dans SSMS.)

2.  Mettez à jour les valeurs de paramètres dans la procédure stockée `catalog.create_execution` pour votre système.

3.  Vérifiez que SSISDB est la base de données active.

4.  Exécutez le script.

5. Dans l’Explorateur d’objets, actualisez le contenu de **SSISDB** si nécessaire et vérifiez la présence du projet que vous avez déployé.

```sql
Declare @execution_id bigint
EXEC [SSISDB].[catalog].[create_execution] @package_name=N'Package.dtsx',
    @execution_id=@execution_id OUTPUT,
    @folder_name=N'Deployed Projects',
      @project_name=N'Integration Services Project1',
    @use32bitruntime=False,
      @reference_id=Null
Select @execution_id
DECLARE @var0 smallint = 1
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,
    @object_type=50,
      @parameter_name=N'LOGGING_LEVEL',
      @parameter_value=@var0
EXEC [SSISDB].[catalog].[start_execution] @execution_id
GO
```

## <a name="next-steps"></a>Étapes suivantes
- Envisagez d’autres méthodes pour exécuter un package.
    - [Exécuter un package SSIS avec SSMS](./ssis-quickstart-run-ssms.md)
    - [Exécuter un package SSIS avec Transact-SQL (VS Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Exécuter un package SSIS à partir de l’invite de commandes](./ssis-quickstart-run-cmdline.md)
    - [Exécuter un package SSIS avec PowerShell](ssis-quickstart-run-powershell.md)
    - [Exécuter un package SSIS avec C#](./ssis-quickstart-run-dotnet.md) 

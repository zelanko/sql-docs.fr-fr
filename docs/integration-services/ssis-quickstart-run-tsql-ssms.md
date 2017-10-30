---
title: "Exécutez un package SSIS avec Transact-SQL (SSMS) | Documents Microsoft"
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
ms.openlocfilehash: 1c656661f645ac9f5d1659800893290819525f39
ms.contentlocale: fr-fr
ms.lasthandoff: 09/22/2017

---
# <a name="run-an-ssis-package-from-ssms-with-transact-sql"></a>Exécutez un package SSIS à partir de SSMS avec Transact-SQL
Ce démarrage rapide montre comment utiliser SQL Server Management Studio (SSMS) pour vous connecter à la base de données du catalogue SSIS, puis utilisez les instructions Transact-SQL pour exécuter un package SSIS stocké dans le catalogue SSIS.

SQL Server Management Studio est un environnement intégré pour la gestion d’une infrastructure SQL, SQL Server vers la base de données SQL. Pour plus d’informations sur SSMS, consultez [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md).

## <a name="prerequisites"></a>Conditions préalables

Avant de commencer, assurez-vous que vous disposez de la dernière version de SQL Server Management Studio (SSMS). Pour télécharger SSMS, consultez [télécharger SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="connect-to-the-ssisdb-database"></a>Se connecter à la base de données SSISDB

Utilisez SQL Server Management Studio pour établir une connexion dans le catalogue SSIS sur votre serveur de base de données SQL Azure. 

> [!NOTE]
> Un serveur de base de données SQL Azure est à l’écoute sur le port 1433. Si vous essayez de vous connecter à un serveur de base de données SQL Azure à partir d’un pare-feu d’entreprise, ce port doit être ouvert dans le pare-feu d’entreprise pour vous connecter avec succès.

1. Ouvrez SQL Server Management Studio.

2. Dans le **se connecter au serveur** boîte de dialogue, entrez les informations suivantes :

   | Paramètre       | Valeur suggérée | En savoir plus | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Type de serveur** | Moteur de base de données | Cette valeur est requise. |
   | **Nom du serveur** | Le nom du serveur complet | Si vous vous connectez à un serveur de base de données SQL Azure, le nom est au format suivant : `<server_name>.database.windows.net`. |
   | **Authentification** | Authentification SQL Server | Ce démarrage rapide utilise l’authentification SQL. |
   | **Connexion** | Le compte d’administrateur de serveur | Il s’agit du compte que vous avez spécifié lorsque vous avez créé le serveur. |
   | **Mot de passe** | Le mot de passe pour votre compte d’administrateur de serveur | Il s’agit du mot de passe que vous avez spécifié lorsque vous avez créé le serveur. |

3.  Cliquez sur **Se connecter**. La fenêtre de l’Explorateur d’objets dans SSMS.

4. Dans l’Explorateur d’objets, développez **catalogues Integration Services** , puis **SSISDB** pour afficher les objets dans la base de données du catalogue SSIS.

## <a name="run-a-package"></a>Exécuter un package
Exécutez le code Transact-SQL suivant pour exécuter un package SSIS.

1.  Dans SSMS, ouvrez une nouvelle fenêtre de requête et collez le code suivant. (Ce code est le code généré par le **Script** option dans le **exécuter le Package** boîte de dialogue dans SSMS.)

2.  Mettre à jour les valeurs de paramètre dans le `catalog.create_execution` la procédure stockée pour votre système.

3.  Assurez-vous que SSISDB est la base de données actuelle.

4.  Exécutez le script.

5. Dans l’Explorateur d’objets, actualiser le contenu de **SSISDB** si nécessaire pour le projet que vous avez déployé.

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
    - [Exécutez un package SSIS avec SSMS](./ssis-quickstart-run-ssms.md)
    - [Exécutez un package SSIS avec Transact-SQL (Code de Visual Studio)](ssis-quickstart-run-tsql-vscode.md)
    - [Exécutez un package SSIS à partir de l’invite de commandes](./ssis-quickstart-run-cmdline.md)
    - [Exécuter un package SSIS avec PowerShell](ssis-quickstart-run-powershell.md)
    - [Exécutez un package SSIS avec c#](./ssis-quickstart-run-dotnet.md) 


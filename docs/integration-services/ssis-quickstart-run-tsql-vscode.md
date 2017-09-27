---
title: "Exécutez un package SSIS avec Transact-SQL (VS Code) | Documents Microsoft"
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
ms.openlocfilehash: a912bf7f7944d4af3d41c5596e67aa77f3214112
ms.contentlocale: fr-fr
ms.lasthandoff: 09/22/2017

---
# <a name="run-an-ssis-package-from-visual-studio-code-with-transact-sql"></a>Exécutez un package SSIS à partir de Code de Visual Studio avec Transact-SQL
Ce démarrage rapide montre comment utiliser le Code de Visual Studio pour vous connecter à la base de données du catalogue SSIS, puis utilisez les instructions Transact-SQL pour exécuter un package SSIS stocké dans le catalogue SSIS.

Code Visual Studio est un éditeur de code pour Windows, Mac OS et Linux qui prend en charge les extensions, y compris le `mssql` extension pour la connexion à Microsoft SQL Server, base de données SQL Azure ou Azure SQL Data Warehouse. Pour plus d’informations sur le Code de Visual Studio, consultez [Visual Studio Cod](https://code.visualstudio.com/).

## <a name="prerequisites"></a>Conditions préalables

Avant de commencer, assurez-vous que vous avez installé la dernière version de Visual Studio Code et charger le `mssql` extension. Pour télécharger ces outils, consultez les pages suivantes :
-   [Télécharger Visual Studio Code](https://code.visualstudio.com/Download)
-   [extension de MSSQL](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)

## <a name="set-language-mode-to-sql-in-vs-code"></a>Définir le mode de langage SQL dans le Code de Visual Studio

Pour activer `mssql` de commande et de T-SQL IntelliSense, définissez le mode de langue a la valeur **SQL** dans Visual Studio Code.

1. Ouvrez Visual Studio Code, puis ouvrez une nouvelle fenêtre. 

2. Cliquez sur **en texte brut** dans le coin inférieur droit de la barre d’état.

3. Dans le **mode langage sélectionnez** menu déroulant qui s’affiche, sélectionnez ou entrez **SQL**, puis appuyez sur **entrée** pour définir le mode de langage SQL. 

## <a name="connect-to-the-ssis-catalog-database"></a>Se connecter à la base de données du catalogue SSIS

Code Visual Studio permet d’établir une connexion dans le catalogue SSIS.

> [!IMPORTANT]
> Avant de continuer, assurez-vous que vous disposez de votre serveur, base de données et les informations de connexion prêt. Si vous modifiez le focus à partir de Visual Studio Code une fois que vous commencez à saisir les informations de profil de connexion, vous devez redémarrer la création du profil de connexion.

1. Dans le Code de Visual Studio, appuyez sur **CTRL + MAJ + P** (ou **F1**) pour ouvrir la Palette de commandes.

2. Type **sqlcon** et appuyez sur **entrée**.

3. Appuyez sur **entrée** pour sélectionner **créer un profil de connexion**. Cette étape crée un profil de connexion pour votre instance de SQL Server.

4. Suivez les invites pour spécifier les propriétés de connexion pour le profil de connexion. Après avoir spécifié de chaque valeur, appuyez sur **entrée** pour continuer. 

   | Paramètre       | Valeur suggérée | En savoir plus |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Nom du serveur** | Le nom du serveur complet | Si vous vous connectez à un serveur de base de données SQL Azure, le nom est au format suivant : `<server_name>.database.windows.net`. |
   | **Nom de la base de données** | **SSISDB** | Le nom de la base de données à laquelle se connecter. |
   | **Authentification** | Connexion SQL| Ce démarrage rapide utilise l’authentification SQL. |
   | **Nom d'utilisateur** | Le compte d’administrateur de serveur | Il s’agit du compte que vous avez spécifié lorsque vous avez créé le serveur. |
   | **Mot de passe (connexion SQL)** | Le mot de passe pour votre compte d’administrateur de serveur | Il s’agit du mot de passe que vous avez spécifié lorsque vous avez créé le serveur. |
   | **Enregistrer le mot de passe ?** | Oui ou Non | Si vous ne souhaitez pas entrer le mot de passe chaque fois, sélectionnez Oui. |
   | **Entrez un nom pour ce profil** | Nom d’un profil, tel que **mySSISServer** | Un nom de profil enregistré accélère votre connexion sur les connexions suivantes. | 

5. Appuyez sur la **ÉCHAP** touche pour fermer le message d’information qui vous informe que le profil est créé et connecté.

6. Vérifiez votre connexion dans la barre d’état.

## <a name="run-the-t-sql-code"></a>Exécutez le code T-SQL
Exécutez le code Transact-SQL suivant pour exécuter un package SSIS.

1. Dans le **éditeur** fenêtre, entrez la requête suivante dans la fenêtre de requête vide. (Ce code est le code généré par le **Script** option dans le **exécuter le Package** boîte de dialogue dans SSMS.)

2. Mettre à jour les valeurs de paramètre dans le `catalog.create_execution` la procédure stockée pour votre système.

3. Appuyez sur **CTRL + MAJ + E** pour exécuter le code et exécuter le package.

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
    - [Exécutez un package SSIS avec Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Exécutez un package SSIS à partir de l’invite de commandes](./ssis-quickstart-run-cmdline.md)
    - [Exécuter un package SSIS avec PowerShell](ssis-quickstart-run-powershell.md)
    - [Exécutez un package SSIS avec c#](./ssis-quickstart-run-dotnet.md) 


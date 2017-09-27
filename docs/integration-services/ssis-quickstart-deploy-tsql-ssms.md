---
title: "Déployer un projet SSIS avec Transact-SQL (SSMS) | Documents Microsoft"
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
ms.openlocfilehash: e97fb20f5b0ee10aa3e5de690676b7e0bb797b4c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/22/2017

---
# <a name="deploy-an-ssis-project-from-ssms-with-transact-sql"></a>Déployer un projet SSIS à partir de SSMS avec Transact-SQL

Ce démarrage rapide montre comment utiliser SQL Server Management Studio (SSMS) pour se connecter à la base de données du catalogue SSIS, puis utiliser les instructions Transact-SQL pour déployer un projet SSIS dans le catalogue SSIS. 

> [!NOTE]
> La méthode décrite dans cet article n’est pas disponible lorsque vous vous connectez à un serveur de base de données SQL Azure avec SSMS. Le `catalog.deploy_project` procédure stockée attend le chemin d’accès à la `.ispac` fichier dans le système de fichiers local (sur site).

SQL Server Management Studio est un environnement intégré pour la gestion d’une infrastructure SQL, SQL Server vers la base de données SQL. Pour plus d’informations sur SSMS, consultez [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md).

## <a name="prerequisites"></a>Conditions préalables

Avant de commencer, assurez-vous que vous disposez de la dernière version de SQL Server Management Studio. Pour télécharger SSMS, consultez [télécharger SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="connect-to-the-ssis-catalog-database"></a>Se connecter à la base de données du catalogue SSIS

Utilisez SQL Server Management Studio pour établir une connexion dans le catalogue SSIS. 

> [!NOTE]
> Un serveur de base de données SQL Azure est à l’écoute sur le port 1433. Si vous essayez de vous connecter à un serveur de base de données SQL Azure à partir d’un pare-feu d’entreprise, ce port doit être ouvert dans le pare-feu d’entreprise pour vous connecter avec succès.

1. Ouvrez SQL Server Management Studio.

2. Dans le **se connecter au serveur** boîte de dialogue, entrez les informations suivantes :

   | Paramètre       | Valeur suggérée | En savoir plus | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Type de serveur** | Moteur de base de données | Cette valeur est requise. |
   | **Nom du serveur** | Le nom du serveur complet |  |
   | **Authentification** | Authentification SQL Server | Ce démarrage rapide utilise l’authentification SQL. |
   | **Connexion** | Le compte d’administrateur de serveur | Il s’agit du compte que vous avez spécifié lorsque vous avez créé le serveur. |
   | **Mot de passe** | Le mot de passe pour votre compte d’administrateur de serveur | Il s’agit du mot de passe que vous avez spécifié lorsque vous avez créé le serveur. |

3. Cliquez sur **Se connecter**. La fenêtre de l’Explorateur d’objets dans SSMS. 

4. Dans l’Explorateur d’objets, développez **catalogues Integration Services** , puis **SSISDB** pour afficher les objets dans la base de données du catalogue SSIS.

## <a name="run-the-t-sql-code"></a>Exécutez le code T-SQL
Exécutez le code Transact-SQL suivant pour déployer un projet SSIS.

1.  Dans SSMS, ouvrez une nouvelle fenêtre de requête et collez le code suivant.

2.  Mettre à jour les valeurs de paramètre dans le `catalog.deploy_project` la procédure stockée pour votre système.

3.  Assurez-vous que SSISDB est la base de données actuelle.

4.  Exécutez le script.

5. Dans l’Explorateur d’objets, actualiser le contenu de **SSISDB** si nécessaire pour le projet que vous avez déployé.

```sql
DECLARE @ProjectBinary AS varbinary(max)
DECLARE @operation_id AS bigint
SET @ProjectBinary =
    (SELECT * FROM OPENROWSET(BULK '<project_file_path>.ispac', SINGLE_BLOB) AS BinaryData)

EXEC catalog.deploy_project @folder_name = '<target_folder>',
    @project_name = '<project_name',
    @Project_Stream = @ProjectBinary,
    @operation_id = @operation_id out
```

## <a name="next-steps"></a>Étapes suivantes
- Envisagez d’autres méthodes pour déployer un package.
    - [Déployer un package SSIS avec SSMS](./ssis-quickstart-deploy-ssms.md)
    - [Déployer un package SSIS avec Transact-SQL (Code de Visual Studio)](ssis-quickstart-deploy-tsql-vscode.md)
    - [Déployer un package SSIS à partir de l’invite de commandes](./ssis-quickstart-deploy-cmdline.md)
    - [Déployer un package SSIS avec PowerShell](ssis-quickstart-deploy-powershell.md)
    - [Déployer un package SSIS avec c#](./ssis-quickstart-deploy-dotnet.md) 
- Exécuter un package déployé. Pour exécuter un package, vous pouvez choisir à partir de plusieurs outils et langages. Pour plus d’informations, consultez les articles suivants :
    - [Exécutez un package SSIS avec SSMS](./ssis-quickstart-run-ssms.md)
    - [Exécutez un package SSIS avec Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Exécutez un package SSIS avec Transact-SQL (Code de Visual Studio)](ssis-quickstart-run-tsql-vscode.md)
    - [Exécutez un package SSIS à partir de l’invite de commandes](./ssis-quickstart-run-cmdline.md)
    - [Exécuter un package SSIS avec PowerShell](ssis-quickstart-run-powershell.md)
    - [Exécutez un package SSIS avec c#](./ssis-quickstart-run-dotnet.md) 


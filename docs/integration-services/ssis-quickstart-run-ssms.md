---
title: "Exécutez un package SSIS avec SSMS | Documents Microsoft"
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
ms.openlocfilehash: bbc17907311785ef98560493cb453b7b9b6d1556
ms.contentlocale: fr-fr
ms.lasthandoff: 09/22/2017

---
# <a name="run-an-ssis-package-with-sql-server-management-studio-ssms"></a>Exécutez un package SSIS avec SQL Server Management Studio (SSMS)
Ce démarrage rapide montre comment utiliser SQL Server Management Studio (SSMS) pour se connecter à la base de données du catalogue SSIS, puis exécutez un package SSIS stocké dans le catalogue SSIS à partir de l’Explorateur d’objets dans SSMS.

SQL Server Management Studio est un environnement intégré pour la gestion d’une infrastructure SQL, SQL Server vers la base de données SQL. Pour plus d’informations sur SSMS, consultez [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md).

## <a name="prerequisites"></a>Conditions préalables

Avant de commencer, assurez-vous que vous disposez de la dernière version de SQL Server Management Studio (SSMS). Pour télécharger SSMS, consultez [télécharger SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="connect-to-the-ssisdb-database"></a>Se connecter à la base de données SSISDB

Utilisez SQL Server Management Studio pour établir une connexion dans le catalogue SSIS. 

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

3. Cliquez sur **Se connecter**. La fenêtre de l’Explorateur d’objets dans SSMS. 

4. Dans l’Explorateur d’objets, développez **catalogues Integration Services** , puis **SSISDB** pour afficher les objets dans la base de données du catalogue SSIS.

## <a name="run-a-package"></a>Exécuter un package

1. Dans l’Explorateur d’objets, sélectionnez le package que vous souhaitez exécuter.

2. Avec le bouton droit et sélectionnez **Execute**. Le **exécuter le Package** boîte de dialogue s’ouvre.

3.  Configurer l’exécution du package en utilisant les paramètres sur le **paramètres**, **gestionnaires de connexions**, et **avancé** onglets dans la boîte de dialogue Exécuter le Package.

4.  Cliquez sur OK pour exécuter le package.

## <a name="next-steps"></a>Étapes suivantes
- Envisagez d’autres méthodes pour exécuter un package.
    - [Exécutez un package SSIS avec Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Exécutez un package SSIS avec Transact-SQL (Code de Visual Studio)](ssis-quickstart-run-tsql-vscode.md)
    - [Exécutez un package SSIS à partir de l’invite de commandes](./ssis-quickstart-run-cmdline.md)
    - [Exécuter un package SSIS avec PowerShell](ssis-quickstart-run-powershell.md)
    - [Exécutez un package SSIS avec c#](./ssis-quickstart-run-dotnet.md) 


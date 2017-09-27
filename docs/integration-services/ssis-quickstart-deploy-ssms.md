---
title: "Déployer un projet SSIS avec SSMS | Documents Microsoft"
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
ms.openlocfilehash: b9729343ab14563ee6264795d6f098f3c22e91bf
ms.contentlocale: fr-fr
ms.lasthandoff: 09/22/2017

---
# <a name="deploy-an-ssis-project-with-sql-server-management-studio-ssms"></a>Déployer un projet SSIS avec SQL Server Management Studio (SSMS)
Ce démarrage rapide montre comment utiliser SQL Server Management Studio (SSMS) pour se connecter à la base de données du catalogue SSIS, puis exécutez l’Assistant Déploiement d’Integration Services pour déployer un projet SSIS dans le catalogue SSIS. 

SQL Server Management Studio est un environnement intégré pour la gestion d’une infrastructure SQL, SQL Server vers la base de données SQL. Pour plus d’informations sur SSMS, consultez [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md).

## <a name="prerequisites"></a>Conditions préalables

Avant de commencer, assurez-vous que vous disposez de la dernière version de SQL Server Management Studio. Pour télécharger SSMS, consultez [télécharger SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

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

## <a name="start-the-integration-services-deployment-wizard"></a>Démarrer l’Assistant Déploiement d’Integration Services
1. Dans l’Explorateur d’objets, avec le **catalogues Integration Services** nœud et le **SSISDB** développé, développez un dossier de projet.

2.  Sélectionnez le **projets** nœud.

3.  Avec le bouton droit sur le **projets** nœud et sélectionnez **déployer le projet**. L’Assistant Déploiement d’Integration Services s’ouvre. Vous pouvez déployer un projet à partir du catalogue actuel ou du système de fichiers.

## <a name="deploy-a-project-with-the-wizard"></a>Déployer un projet avec l’Assistant
1. Sur le **Introduction** page de l’Assistant, examinez l’introduction. Cliquez sur **suivant** pour ouvrir le **sélectionner une Source** page.

2. Sur le **sélectionner une Source de** , sélectionnez le projet SSIS existant à déployer.
    -   Pour déployer un fichier de déploiement de projet que vous avez créé, sélectionnez **Fichier de déploiement de projet** , puis entrez le chemin d’accès du fichier .ispac.
    -   Pour déployer un projet qui réside dans un catalogue SSIS, sélectionnez **catalogue Integration Services**, puis entrez le nom du serveur et le chemin d’accès au projet dans le catalogue.
    Cliquez sur **Suivant** pour afficher la page **Sélectionner la destination** .
  
3.  Sur le **sélectionner la Destination** , sélectionnez la destination pour le projet.
    -   Entrez le nom du serveur complet. Si le serveur cible est un serveur de base de données SQL Azure, le nom est au format suivant : `<server_name>.database.windows.net`.
    -   Puis cliquez sur **Parcourir** pour sélectionner le dossier cible dans SSISDB.
    Cliquez sur **suivant** pour ouvrir le **révision** page.  
  
4.  Sur le **Examinez** page, vérifiez les paramètres que vous avez sélectionné.
    -   Vous pouvez modifier vos sélections en cliquant sur **Précédent**ou en cliquant sur l'une des étapes dans le volet gauche.
    -   Cliquez sur **Déployer** pour démarrer le processus de déploiement.
  
5.  Une fois le processus de déploiement terminé, le **résultats** ouvrir la page. Cette page indique la réussite ou l’échec de chaque action.
    -   Si l’action a échoué, cliquez sur **n’a pas pu** dans les **résultat** colonne pour afficher une explication de l’erreur.
    -   Si vous le souhaitez, cliquez sur **enregistrer le rapport... ** pour enregistrer les résultats dans un fichier XML.
    -   Cliquez sur **fermer** pour quitter l’Assistant.

## <a name="next-steps"></a>Étapes suivantes
- Envisagez d’autres méthodes pour déployer un package.
    - [Déployer un package SSIS avec Transact-SQL (SSMS)](./ssis-quickstart-deploy-tsql-ssms.md)
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


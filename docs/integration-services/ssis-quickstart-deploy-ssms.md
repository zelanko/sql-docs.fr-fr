---
title: Déployer un projet SSIS avec SSMS | Microsoft Docs
ms.date: 09/25/2017
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.component: quick-start
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 968f97ccfdb4d028554f705634dda8a12c82f580
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="deploy-an-ssis-project-with-sql-server-management-studio-ssms"></a>Déployer un projet SSIS avec SQL Server Management Studio (SSMS)
Ce guide de démarrage rapide montre comment utiliser SQL Server Management Studio (SSMS) pour se connecter à la base de données du catalogue SSIS, puis exécuter l’Assistant Déploiement d’Integration Services pour déployer un projet SSIS dans le catalogue SSIS. 

SQL Server Management Studio est un environnement intégré pour la gestion des infrastructures SQL, de SQL Server à SQL Database. Pour plus d’informations sur SSMS, consultez [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md).

## <a name="prerequisites"></a>Conditions préalables requises

Avant de commencer, vérifiez que vous disposez de la dernière version de SQL Server Management Studio. Pour télécharger SSMS, consultez [Télécharger SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="connect-to-the-ssisdb-database"></a>Se connecter à la base de données SSISDB

Utilisez SQL Server Management Studio pour établir une connexion au catalogue SSIS. 

> [!NOTE]
> Un serveur Azure SQL Database est à l’écoute sur le port 1433. Si vous essayez de vous connecter à un serveur Azure SQL Database en étant derrière un pare-feu d’entreprise, ce port doit être ouvert dans le pare-feu d’entreprise pour que vous puissiez vous connecter.

1. Ouvrez SQL Server Management Studio.

2. Dans la boîte de dialogue **Se connecter au serveur**, entrez les informations suivantes :

   | Paramètre       | Valeur suggérée | En savoir plus | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Type de serveur** | Moteur de base de données | Cette valeur est requise. |
   | **Nom du serveur** | Nom complet du serveur | Si vous vous connectez à un serveur Azure SQL Database, le nom est au format suivant : `<server_name>.database.windows.net`. |
   | **Authentification** | Authentification SQL Server | Ce guide de démarrage rapide utilise l’authentification SQL. |
   | **Connexion** | Compte Administrateur du serveur | Il s’agit du compte que vous avez spécifié quand vous avez créé le serveur. |
   | **Mot de passe** | Mot de passe du compte Administrateur de votre serveur | Il s’agit du mot de passe que vous avez spécifié quand vous avez créé le serveur. |

3. Cliquez sur **Se connecter**. La fenêtre Explorateur d’objets s’ouvre dans SSMS. 

4. Dans l’Explorateur d’objets, développez **Catalogues Integration Services**, puis développez **SSISDB** pour afficher les objets de la base de données de catalogues SSIS.

## <a name="start-the-integration-services-deployment-wizard"></a>Démarrer l’Assistant Déploiement d’Integration Services
1. Dans l’Explorateur d’objets, avec le nœud **Catalogues Integration Services** et la base de données **SSISDB** développés, développez un dossier de projet.

2.  Sélectionnez le nœud **Projets**.

3.  Cliquez avec le bouton droit sur le nœud **Projets**, puis sélectionnez **Déployer le projet**. L’Assistant Déploiement d’Integration Services s’ouvre. Vous pouvez déployer un projet à partir du catalogue actif ou du système de fichiers.

## <a name="deploy-a-project-with-the-wizard"></a>Déployer un projet avec l’Assistant
1. Dans la page **Introduction** de l’Assistant, examinez l’introduction. Cliquez sur **Suivant** pour ouvrir la page **Sélectionner la source**.

2. Dans la page **Sélectionner la source**, sélectionnez le projet SSIS existant à déployer.
    -   Pour déployer un fichier de déploiement de projet que vous avez créé, sélectionnez **Fichier de déploiement de projet** , puis entrez le chemin d’accès du fichier .ispac.
    -   Pour déployer un projet qui réside dans un catalogue SSIS, sélectionnez **Catalogue Integration Services**, puis entrez le nom du serveur et le chemin du projet au sein du catalogue.
    Cliquez sur **Suivant** pour afficher la page **Sélectionner la destination** .
  
3.  Dans la page **Sélectionner la destination**, sélectionnez la destination du projet.
    -   Entrez le nom complet du serveur. Si le serveur cible est un serveur Azure SQL Database, le nom est au format suivant : `<server_name>.database.windows.net`.
    -   Ensuite, cliquez sur **Parcourir** pour sélectionner le dossier cible dans SSISDB.
    Cliquez sur **Suivant** pour ouvrir la page **Vérifier**.  
  
4.  Dans la page **Vérifier**, vérifiez les paramètres que vous avez sélectionnés.
    -   Vous pouvez modifier vos sélections en cliquant sur **Précédent**ou en cliquant sur l'une des étapes dans le volet gauche.
    -   Cliquez sur **Déployer** pour démarrer le processus de déploiement.
  
5.  Une fois le processus de déploiement effectué, la page **Résultats** s’affiche. Cette page indique la réussite ou l’échec de chaque action.
    -   Si l’action a échoué, cliquez sur **Échec** dans la colonne **Résultat** pour afficher une explication de l’erreur.
    -   Si vous le souhaitez, cliquez sur **Enregistrer le rapport** pour enregistrer les résultats dans un fichier XML.
    -   Cliquez sur **Fermer** pour quitter l’Assistant.

## <a name="next-steps"></a>Étapes suivantes
- Envisagez d’autres méthodes pour déployer un package.
    - [Déployer un package SSIS avec Transact-SQL (SSMS)](./ssis-quickstart-deploy-tsql-ssms.md)
    - [Déployer un package SSIS avec Transact-SQL (VS Code)](ssis-quickstart-deploy-tsql-vscode.md)
    - [Déployer un package SSIS à partir de l’invite de commandes](./ssis-quickstart-deploy-cmdline.md)
    - [Déployer un package SSIS avec PowerShell](ssis-quickstart-deploy-powershell.md)
    - [Déployer un package SSIS avec C#](./ssis-quickstart-deploy-dotnet.md) 
- Exécutez un package déployé. Pour exécuter un package, vous pouvez choisir parmi plusieurs outils et langages. Pour plus d’informations, consultez les articles suivants :
    - [Exécuter un package SSIS avec SSMS](./ssis-quickstart-run-ssms.md)
    - [Exécuter un package SSIS avec Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Exécuter un package SSIS avec Transact-SQL (VS Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Exécuter un package SSIS à partir de l’invite de commandes](./ssis-quickstart-run-cmdline.md)
    - [Exécuter un package SSIS avec PowerShell](ssis-quickstart-run-powershell.md)
    - [Exécuter un package SSIS avec C#](./ssis-quickstart-run-dotnet.md) 

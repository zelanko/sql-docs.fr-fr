---
title: "Déployer un projet SSIS à partir de l’invite de commandes | Microsoft Docs"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6c3e7f7e3fa870c7aa5b30a5a4a324f0cef7f6ba
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="deploy-an-ssis-project-from-the-command-prompt-with-isdeploymentwizardexe"></a>Déployer un projet SSIS à partir de l’invite de commandes avec ISDeploymentWizard.exe
Ce didacticiel de démarrage rapide montre comment déployer un projet SSIS à partir de l’invite de commandes en exécutant l’Assistant Déploiement d’Integration Services, `ISDeploymentWizard.exe`.

Pour plus d’informations sur l’Assistant Déploiement d’Integration Services, consultez [Assistant Déploiement d’Integration Services](packages/deploy-integration-services-ssis-projects-and-packages.md#integration-services-deployment-wizard).

## <a name="start-the-integration-services-deployment-wizard"></a>Démarrer l’Assistant Déploiement d’Integration Services
1. Ouvrez une fenêtre d'invite de commandes.

2. Exécutez `ISDeploymentWizard.exe`. L’Assistant Déploiement d’Integration Services s’ouvre.

    Si le dossier qui contient `ISDeploymentWizard.exe` ne figure pas dans votre variable d’environnement `path`, vous devrez peut-être utiliser la commande `cd` pour basculer vers son répertoire. Pour SQL Server 2017, ce dossier est généralement `C:\Program Files (x86)\Microsoft SQL Server\140\DTS\Binn`.

## <a name="deploy-a-project-with-the-wizard"></a>Déployer un projet avec l’Assistant
1. Dans la page **Introduction** de l’Assistant, examinez l’introduction. Cliquez sur **Suivant** pour ouvrir la page **Sélectionner la source**.

2. Dans la page **Sélectionner la Source**, sélectionnez le projet SSIS existant à déployer.
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
  
5.  Une fois le processus de déploiement terminé, la page **Résultats** s’ouvre. Cette page indique la réussite ou l’échec de chaque action.
    -   Si l’action a échoué, cliquez sur **Échec** dans la colonne **Résultat** pour afficher une explication de l’erreur.
    -   Si vous le souhaitez, cliquez sur **Enregistrer le rapport** pour enregistrer les résultats dans un fichier XML.
    -   Cliquez sur **Fermer** pour quitter l’Assistant.

## <a name="next-steps"></a>Étapes suivantes
- Envisagez d’autres méthodes pour déployer un package.
    - [Déployer un package SSIS avec SSMS](./ssis-quickstart-deploy-ssms.md)
    - [Déployer un package SSIS avec Transact-SQL (SSMS)](./ssis-quickstart-deploy-tsql-ssms.md)
    - [Déployer un package SSIS avec Transact-SQL (VS Code)](ssis-quickstart-deploy-tsql-vscode.md)
    - [Déployer un package SSIS avec PowerShell](ssis-quickstart-deploy-powershell.md)
    - [Déployer un package SSIS avec C#](./ssis-quickstart-deploy-dotnet.md) 
- Exécutez un package déployé. Pour exécuter un package, vous pouvez choisir parmi plusieurs outils et langages. Pour plus d’informations, consultez les articles suivants :
    - [Exécuter un package SSIS avec SSMS](./ssis-quickstart-run-ssms.md)
    - [Exécuter un package SSIS avec Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Exécuter un package SSIS avec Transact-SQL (VS Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Exécuter un package SSIS à partir de l’invite de commandes](./ssis-quickstart-run-cmdline.md)
    - [Exécuter un package SSIS avec PowerShell](ssis-quickstart-run-powershell.md)
    - [Exécuter un package SSIS avec C#](./ssis-quickstart-run-dotnet.md) 

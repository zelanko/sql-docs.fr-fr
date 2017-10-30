---
title: "Déployer un projet SSIS à partir de l’invite de commandes | Documents Microsoft"
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
ms.sourcegitcommit: bc1321dd91a0fcb7ab76b207301c6302bb3a5e64
ms.openlocfilehash: 0f1c7733f0ce6b132c209961a1fd12da80cbd282
ms.contentlocale: fr-fr
ms.lasthandoff: 10/06/2017

---
# <a name="deploy-an-ssis-project-from-the-command-prompt-with-isdeploymentwizardexe"></a>Déployer un projet SSIS à partir de l’invite de commandes avec ISDeploymentWizard.exe
Ce didacticiel de démarrage rapide montre comment déployer un projet SSIS à partir de l’invite de commandes en exécutant l’Assistant Déploiement d’Integration Services, `ISDeploymentWizard.exe`.

Pour plus d’informations sur l’Assistant Déploiement d’Integration Services, consultez [Assistant Déploiement d’Integration Services](packages/deploy-integration-services-ssis-projects-and-packages.md#integration-services-deployment-wizard).

## <a name="start-the-integration-services-deployment-wizard"></a>Démarrer l’Assistant Déploiement d’Integration Services
1. Ouvrez une fenêtre d'invite de commandes.

2. Exécutez `ISDeploymentWizard.exe`. L’Assistant Déploiement d’Integration Services s’ouvre.

    Si le dossier qui contient `ISDeploymentWizard.exe` ne figure pas dans votre `path` variable d’environnement, vous devrez peut-être utiliser le `cd` commande à passer à son répertoire. Pour SQL Server 2017, ce dossier est généralement `C:\Program Files (x86)\Microsoft SQL Server\140\DTS\Binn`.

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
    -   Si vous le souhaitez, cliquez sur **enregistrer le rapport...**  pour enregistrer les résultats dans un fichier XML.
    -   Cliquez sur **fermer** pour quitter l’Assistant.

## <a name="next-steps"></a>Étapes suivantes
- Envisagez d’autres méthodes pour déployer un package.
    - [Déployer un package SSIS avec SSMS](./ssis-quickstart-deploy-ssms.md)
    - [Déployer un package SSIS avec Transact-SQL (SSMS)](./ssis-quickstart-deploy-tsql-ssms.md)
    - [Déployer un package SSIS avec Transact-SQL (Code de Visual Studio)](ssis-quickstart-deploy-tsql-vscode.md)
    - [Déployer un package SSIS avec PowerShell](ssis-quickstart-deploy-powershell.md)
    - [Déployer un package SSIS avec c#](./ssis-quickstart-deploy-dotnet.md) 
- Exécuter un package déployé. Pour exécuter un package, vous pouvez choisir à partir de plusieurs outils et langages. Pour plus d’informations, consultez les articles suivants :
    - [Exécutez un package SSIS avec SSMS](./ssis-quickstart-run-ssms.md)
    - [Exécutez un package SSIS avec Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Exécutez un package SSIS avec Transact-SQL (Code de Visual Studio)](ssis-quickstart-run-tsql-vscode.md)
    - [Exécutez un package SSIS à partir de l’invite de commandes](./ssis-quickstart-run-cmdline.md)
    - [Exécuter un package SSIS avec PowerShell](ssis-quickstart-run-powershell.md)
    - [Exécutez un package SSIS avec c#](./ssis-quickstart-run-dotnet.md) 


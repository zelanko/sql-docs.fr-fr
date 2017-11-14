---
title: "Déployer, exécuter et surveiller un package SSIS sur Azure | Documents Microsoft"
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
ms.sourcegitcommit: 560965a241b24a09f50a23faf63ce74d0049d5a7
ms.openlocfilehash: 2e16666c412870cc55024e7156752f43ddbc1800
ms.contentlocale: fr-fr
ms.lasthandoff: 10/13/2017

---
# <a name="deploy-run-and-monitor-an-ssis-package-on-azure"></a>Déployer, exécuter et surveiller un package SSIS sur Azure
Ce didacticiel vous montre comment déployer un projet SQL Server Integration Services pour la base de données de catalogue SSISDB sur une base de données SQL Azure, exécutez un package dans le Runtime d’intégration Azure-SSIS et surveiller l’exécution du package.

## <a name="prerequisites"></a>Conditions préalables

Avant de commencer, assurez-vous que vous avez 17,2 ou version ultérieure de SQL Server Management Studio. Pour télécharger la dernière version de SSMS, consultez [télécharger SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

Assurez-vous également que vous disposez de configurer la base de données SSISDB et de mise en service de l’exécution d’intégration Azure-SSIS. Pour plus d’informations sur la façon de configurer SSIS sur Azure, consultez [courbes d’élévation et MAJ des packages SQL Server Integration Services (SSIS) pour Azure](https://docs.microsoft.com/en-us/azure/data-factory/tutorial-deploy-ssis-packages-azure).

## <a name="connect-to-the-ssisdb-database"></a>Se connecter à la base de données SSISDB

Utilisez SQL Server Management Studio pour se connecter au catalogue SSIS sur votre serveur de base de données SQL Azure. Pour plus d’informations, consultez [se connecter à la base de données de catalogue SSISDB sur Azure](ssis-azure-connect-to-catalog-database.md).

> [!IMPORTANT]
> Un serveur de base de données SQL Azure est à l’écoute sur le port 1433. Si vous tentez de vous connecter à un serveur de base de données SQL Azure à partir d’un pare-feu d’entreprise, ce port doit être ouvert dans le pare-feu d’entreprise pour vous connecter avec succès.

1. Ouvrez SQL Server Management Studio.

2. **Connectez-vous au serveur**. Dans le **se connecter au serveur** boîte de dialogue, entrez les informations suivantes :

   | Paramètre       | Valeur suggérée |  Description | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Type de serveur** | Moteur de base de données | Cette valeur est requise. |
   | **Nom du serveur** | Le nom du serveur complet | Le nom doit être au format suivant : **mysqldbserver.database.windows.net**. Si vous avez besoin du nom du serveur, consultez [se connecter à la base de données de catalogue SSISDB sur Azure](ssis-azure-connect-to-catalog-database.md). |
   | **Authentification** | Authentification SQL Server | Ce démarrage rapide utilise l’authentification SQL. |
   | **Connexion** | Le compte d’administrateur de serveur | Il s’agit du compte que vous avez spécifié lorsque vous avez créé le serveur. |
   | **Mot de passe** | Le mot de passe pour votre compte d’administrateur de serveur | Il s’agit du mot de passe que vous avez spécifié lorsque vous avez créé le serveur. |

3. **Se connecter à la base de données SSISDB**. Sélectionnez **Options** pour développer le **se connecter au serveur** boîte de dialogue. Dans l’étendue **se connecter au serveur** boîte de dialogue, sélectionnez le **propriétés de connexion** onglet. Dans le **se connecter à la base de données** champ, sélectionnez ou entrez `SSISDB`.

4. Puis sélectionnez **connexion**. La fenêtre de l’Explorateur d’objets dans SSMS. 

5. Dans l’Explorateur d’objets, développez **catalogues Integration Services** , puis **SSISDB** pour afficher les objets dans la base de données du catalogue SSIS.

## <a name="deploy-a-project"></a>Déployer un projet

### <a name="start-the-integration-services-deployment-wizard"></a>Démarrer l’Assistant Déploiement d’Integration Services
1. Dans l’Explorateur d’objets dans SSMS, avec la **catalogues Integration Services** nœud et le **SSISDB** le nœud développé, développez le dossier de projet.

2.  Sélectionnez le **projets** nœud.

3.  Avec le bouton droit sur le **projets** nœud et sélectionnez **déployer le projet**. L’Assistant Déploiement d’Integration Services s’ouvre. Vous pouvez déployer un projet à partir d’une base de données du catalogue SSIS ou du système de fichiers.

### <a name="deploy-a-project-with-the-deployment-wizard"></a>Déployer un projet avec l’Assistant de déploiement
1. Sur le **Introduction** page de l’Assistant déploiement, étudiez l’introduction. Sélectionnez **suivant** pour ouvrir le **sélectionner une Source** page.

2. Sur le **sélectionner une Source de** , sélectionnez le projet SSIS existant à déployer.
    -   Pour déployer un fichier de déploiement de projet que vous avez créé, sélectionnez **Fichier de déploiement de projet** , puis entrez le chemin d’accès du fichier .ispac.
    -   Pour déployer un projet qui réside dans un catalogue SSIS, sélectionnez **catalogue Integration Services**, puis entrez le nom du serveur et le chemin d’accès au projet dans le catalogue.
    -   Sélectionnez **suivant** pour voir les **sélectionner la Destination** page.
  
3.  Sur le **sélectionner la Destination** , sélectionnez la destination pour le projet.
    -   Entrez le nom du serveur complet au format `<server_name>.database.windows.net`.
    -   Puis sélectionnez **Parcourir** pour sélectionner le dossier cible dans SSISDB.
    -   Sélectionnez **suivant** pour ouvrir le **révision** page.  
  
4.  Sur le **Examinez** page, vérifiez les paramètres que vous avez sélectionné.
    -   Vous pouvez modifier vos sélections en sélectionnant **précédent**, ou en sélectionnant une des étapes dans le volet gauche.
    -   Sélectionnez **déployer** pour démarrer le processus de déploiement.
  
5.  Une fois le processus de déploiement terminé, le **résultats** ouvrir la page. Cette page indique la réussite ou l’échec de chaque action.
    -   Si l’action a échoué, sélectionnez **n’a pas pu** dans les **résultat** colonne pour afficher une explication de l’erreur.
    -   Si vous le souhaitez, sélectionnez **enregistrer le rapport...**  pour enregistrer les résultats dans un fichier XML.
    -   Sélectionnez **fermer** pour quitter l’Assistant.

## <a name="run-a-package"></a>Exécuter un package

1. Dans l’Explorateur d’objets dans SSMS, sélectionnez le package que vous souhaitez exécuter.

2. Avec le bouton droit et sélectionnez **Execute** pour ouvrir le **exécuter le Package** boîte de dialogue.

3.  Dans le **exécuter le Package** boîte de dialogue zone, configurez l’exécution du package en utilisant les paramètres sur le **paramètres**, **gestionnaires de connexions**, et **avancé**  onglets.

4.  Sélectionnez **OK** pour exécuter le package.

## <a name="monitor-the-running-package-in-ssms"></a>Surveiller l’exécution du package dans SSMS

Pour afficher l’état des opérations Integration Services sur le serveur Integration Services, tels que le déploiement, la validation et l’exécution du package en cours d’exécution, utilisez la **opérations actives** boîte de dialogue dans SSMS. Pour ouvrir la **opérations actives** boîte de dialogue, avec le bouton droit **SSISDB**, puis sélectionnez **opérations actives**.

Vous pouvez également sélectionner un package dans l’Explorateur d’objets, avec le bouton droit et sélectionnez **rapports**, puis **rapports Standard**, puis **toutes les exécutions**.

Pour plus d’informations sur la façon de surveiller les packages en cours d’exécution dans SSMS, consultez [analyse les Packages en cours d’exécution et autres opérations](https://docs.microsoft.com/en-us/sql/integration-services/performance/monitor-running-packages-and-other-operations).

## <a name="monitor-the-azure-ssis-integration-runtime"></a>Surveiller l’exécution d’intégration Azure-SSIS

Pour obtenir des informations d’état sur l’exécution d’intégration SSIS de Azure dans lequel les packages sont en cours d’exécution, utilisez les commandes PowerShell suivantes : pour chacune des commandes, indiquez les noms de la fabrique de données, la réponse aux incidents Azure-SSIS et le groupe de ressources.

### <a name="get-metadata-about-the-azure-ssis-integration-runtime"></a>Obtenir des métadonnées sur le Runtime d’intégration Azure-SSIS

```powershell
Get-AzureRmDataFactoryV2IntegrationRuntime -DataFactoryName $DataFactoryName -Name $AzureSsisIRName -ResourceGroupName $ResourceGroupName
```

### <a name="get-the-status-of-the-azure-ssis-integration-runtime"></a>Obtenir l’état de l’exécution d’intégration Azure-SSIS

```powershell
Get-AzureRmDataFactoryV2IntegrationRuntime -Status -DataFactoryName $DataFactoryName -Name $AzureSsisIRName -ResourceGroupName $ResourceGroupName
```

## <a name="next-steps"></a>Étapes suivantes
- Découvrez comment planifier l’exécution du package. Pour plus d’informations, consultez [du package SSIS de la planification d’exécution sur Azure](ssis-azure-schedule-packages.md)


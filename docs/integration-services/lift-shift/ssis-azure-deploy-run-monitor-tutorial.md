---
title: "Déployer, exécuter et surveiller un package SSIS sur Azure | Microsoft Docs"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: lift-shift
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4bf9df198105549f481dda8472f7142533fa8f23
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="deploy-run-and-monitor-an-ssis-package-on-azure"></a>Déployer, exécuter et surveiller un package SSIS sur Azure
Ce didacticiel vous montre comment déployer un projet SQL Server Integration Services sur la base de données de catalogues SSISDB dans Azure SQL Database, comment exécuter un package dans le runtime d’intégration Azure SSIS et comment surveiller le package en cours d’exécution.

## <a name="prerequisites"></a>Conditions préalables

Avant de commencer, vérifiez que vous avez la version 17.2 ou ultérieure de SQL Server Management Studio. Pour télécharger la dernière version de SSMS, consultez [Télécharger SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

Vérifiez également que vous avez configuré la base de données SSISDB et que vous avez provisionné le runtime d’intégration Azure SSIS. Pour plus d’informations sur le provisionnement de SSIS sur Azure, consultez [Effectuer un « lift-and-shift » des packages SSIS (SQL Server Integration Services) vers Azure](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure).

## <a name="connect-to-the-ssisdb-database"></a>Se connecter à la base de données SSISDB

Utilisez SQL Server Management Studio pour vous connecter au catalogue SSIS sur votre serveur Azure SQL Database. Pour plus d’informations, consultez [Se connecter à la base de données de catalogues SSISDB sur Azure](ssis-azure-connect-to-catalog-database.md).

> [!IMPORTANT]
> Un serveur Azure SQL Database écoute sur le port 1433. Si vous tentez de vous connecter à un serveur Azure SQL Database derrière un pare-feu d’entreprise, ce port doit être ouvert dans le pare-feu d’entreprise pour que vous puissiez vous connecter correctement.

1. Ouvrez SQL Server Management Studio.

2. **Connectez-vous au serveur**. Dans la boîte de dialogue **Se connecter au serveur**, entrez les informations suivantes :

   | Paramètre       | Valeur suggérée |  Description | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Type de serveur** | Moteur de base de données | Cette valeur est requise. |
   | **Nom du serveur** | Nom complet du serveur | Le nom doit être au format suivant : **mysqldbserver.database.windows.net**. Si vous avez besoin du nom du serveur, consultez [Se connecter à la base de données de catalogues SSISDB sur Azure](ssis-azure-connect-to-catalog-database.md). |
   | **Authentification** | Authentification SQL Server | Ce guide de démarrage rapide utilise l’authentification SQL. |
   | **Connexion** | Compte Administrateur du serveur | Il s’agit du compte que vous avez spécifié quand vous avez créé le serveur. |
   | **Mot de passe** | Mot de passe du compte Administrateur de votre serveur | Il s’agit du mot de passe que vous avez spécifié quand vous avez créé le serveur. |

3. **Connectez-vous à la base de données SSISDB**. Sélectionnez **Options** pour développer la boîte de dialogue **Se connecter au serveur**. Dans la boîte de dialogue **Se connecter au serveur** développée, sélectionnez l’onglet **Propriétés de connexions**. Dans le champ **Se connecter à la base de données**, sélectionnez ou entrez `SSISDB`.

4. Sélectionnez ensuite **Se connecter**. La fenêtre Explorateur d’objets s’ouvre dans SSMS. 

5. Dans l’Explorateur d’objets, développez **Catalogues Integration Services**, puis développez **SSISDB** pour afficher les objets de la base de données de catalogues SSIS.

## <a name="deploy-a-project"></a>Déployer un projet

### <a name="start-the-integration-services-deployment-wizard"></a>Démarrer l’Assistant Déploiement d’Integration Services
1. Dans l’Explorateur d’objets de SSMS, après avoir développé le nœud **Catalogues Integration Services** et le nœud **SSISDB**, développez un dossier de projet.

2.  Sélectionnez le nœud **Projets**.

3.  Cliquez avec le bouton droit sur le nœud **Projets**, puis sélectionnez **Déployer le projet**. L’Assistant Déploiement d’Integration Services s’ouvre. Vous pouvez déployer un projet à partir d’une base de données de catalogues SSIS ou du système de fichiers.

### <a name="deploy-a-project-with-the-deployment-wizard"></a>Déployer un projet avec l’Assistant Déploiement
1. Dans la page **Introduction** de l’Assistant Déploiement, lisez l’introduction. Sélectionnez **Suivant** pour ouvrir la page **Sélectionner la source**.

2. Dans la page **Sélectionner la source**, sélectionnez le projet SSIS existant à déployer.
    -   Pour déployer un fichier de déploiement de projet que vous avez créé, sélectionnez **Fichier de déploiement de projet** , puis entrez le chemin d’accès du fichier .ispac.
    -   Pour déployer un projet qui réside dans un catalogue SSIS, sélectionnez **Catalogue Integration Services**, puis entrez le nom du serveur et le chemin du projet au sein du catalogue.
    -   Sélectionnez **Suivant** pour voir la page **Sélectionner la destination**.
  
3.  Dans la page **Sélectionner la destination**, sélectionnez la destination du projet.
    -   Entrez le nom complet du serveur au format `<server_name>.database.windows.net`.
    -   Sélectionnez ensuite **Parcourir** pour sélectionner le dossier cible dans SSISDB.
    -   Sélectionnez **Suivant** pour ouvrir la page **Vérifier**.  
  
4.  Dans la page **Vérifier**, vérifiez les paramètres que vous avez sélectionnés.
    -   Vous pouvez changer vos choix en sélectionnant **Précédent**, ou en sélectionnant l’une des étapes du volet gauche.
    -   Sélectionnez **Déployer** pour démarrer le processus de déploiement.
  
5.  Une fois le processus de déploiement effectué, la page **Résultats** s’affiche. Cette page indique la réussite ou l’échec de chaque action.
    -   En cas d’échec de l’action, sélectionnez **Échec** dans la colonne **Résultat** pour afficher une explication de l’erreur.
    -   Sélectionnez éventuellement **Enregistrer le rapport** pour enregistrer les résultats dans un fichier XML.
    -   Pour quitter l’Assistant, sélectionnez **Fermer**.

## <a name="run-a-package"></a>Exécuter un package

1. Dans l’Explorateur d’objets de SSMS, sélectionnez le package à exécuter.

2. Cliquez avec le bouton droit et sélectionnez **Exécuter** pour ouvrir la boîte de dialogue **Exécuter le package**.

3.  Dans la boîte de dialogue **Exécuter le package**, configurez l’exécution du package à l’aide des paramètres situés sous les onglets **Paramètres**, **Gestionnaires de connexions** et **Avancé**.

4.  Sélectionnez **OK** pour exécuter le package.

## <a name="monitor-the-running-package-in-ssms"></a>Surveiller l’exécution du package dans SSMS

Pour afficher l’état des opérations Integration Services en cours d’exécution sur le serveur Integration Services, par exemple le déploiement, la validation et l’exécution du package, utilisez la boîte de dialogue **Opérations actives** dans SSMS. Pour ouvrir la boîte de dialogue **Opérations actives**, cliquez avec le bouton droit sur **SSISDB**, puis sélectionnez **Opérations actives**.

Vous pouvez également sélectionner un package dans l’Explorateur d’objets, cliquer avec le bouton droit et sélectionner **Rapports**, **Rapports standard**, puis **Toutes les exécutions**.

Pour plus d’informations sur la surveillance des packages en cours d’exécution dans SSMS, consultez la section [Surveiller les packages en cours d’exécution et autres opérations](https://docs.microsoft.com/sql/integration-services/performance/monitor-running-packages-and-other-operations).

## <a name="monitor-the-azure-ssis-integration-runtime"></a>Surveiller le runtime d’intégration Azure SSIS

Pour obtenir des informations d’état sur le runtime d’intégration Azure SSIS dans lequel les packages sont en cours d’exécution, utilisez les commandes PowerShell ci-après. Pour chacune des commandes, indiquez les noms du Data Factory, du runtime d’intégration Azure SSIS et du groupe de ressources.

### <a name="get-metadata-about-the-azure-ssis-integration-runtime"></a>Obtenir des métadonnées sur le runtime d’intégration Azure SSIS

```powershell
Get-AzureRmDataFactoryV2IntegrationRuntime -DataFactoryName $DataFactoryName -Name $AzureSsisIRName -ResourceGroupName $ResourceGroupName
```

### <a name="get-the-status-of-the-azure-ssis-integration-runtime"></a>Obtenir l’état du runtime d’intégration Azure SSIS

```powershell
Get-AzureRmDataFactoryV2IntegrationRuntime -Status -DataFactoryName $DataFactoryName -Name $AzureSsisIRName -ResourceGroupName $ResourceGroupName
```

## <a name="next-steps"></a>Étapes suivantes
- Apprenez à planifier l’exécution du package. Pour plus d’informations, consultez [Planifier l’exécution d’un package SSIS sur Azure](ssis-azure-schedule-packages.md)

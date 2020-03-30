---
title: 'Étape 4 : Déployer le package de la leçon 6 | Microsoft Docs'
ms.custom: ''
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: b613cef7-7993-4d89-a429-a8251d74d435
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2a16cd38eef12584f8d876e610bfda5d602c3076
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "71283012"
---
# <a name="lesson-6-4-deploy-the-lesson-6-package"></a>Leçon 6-4 : Déployer le package de la leçon 6

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Pour déployer le package, vous devez l’ajouter au catalogue SSISDB dans [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur une instance de SQL Server. Dans cette leçon, vous ajoutez le package de la leçon 6 au catalogue SSISDB, vous définissez le nouveau paramètre, puis vous exécutez le package. Dans le cadre de cette leçon, vous utilisez SQL Server Management Studio pour ajouter le package de la leçon 6 au catalogue SSISDB et vous déployez le package. Une fois le package déployé, vous modifiez le paramètre afin qu’il pointe vers un nouvel emplacement, puis vous exécutez le package.   
Dans cette tâche, vous effectuez les opérations suivantes :  

1. ajouter le package au catalogue SSISDB dans le nœud SSIS dans SQL Server ;  
  
2. déployer le package ;  
  
3. définir la valeur de paramètre du package ;  

4. exécuter le package dans SSMS.  
  
## <a name="locate-or-add-the-ssisdb-catalog"></a>Rechercher ou ajouter le catalogue SSISDB  
  
1.  Sélectionnez **Démarrer** > **Tous les programmes** > **Microsoft SQL Server 2017**, puis **SQL Management Studio**.  
  
2.  Dans la boîte de dialogue **Se connecter au serveur**, vérifiez les paramètres par défaut, puis sélectionnez **Se connecter**. Pour vous connecter, le nom du **Serveur** doit être le nom de l’ordinateur sur lequel SQL Server est installé. Si le **moteur de base de données** est une instance nommée, le nom du **Serveur** doit être le nom de l’instance au format *\<nom_ordinateur>\\\<nom_instance>* . 
  
3.  Dans l’**Explorateur d’objets**, développez **Catalogues Integration Services**.  
  
4.  Si aucun catalogue ne figure sous **Catalogues Integration Services**, ajoutez le catalogue SSISDB.  
  
5.  Pour ajouter le catalogue SSISDB, cliquez avec le bouton droit sur **Catalogues Integration Services**, puis sélectionnez **Créer un catalogue**.  
  
6.  Dans la boîte de dialogue **Créer un catalogue**, sélectionnez **Activer l’intégration du CLR**.  
  
7.  Dans la zone **Mot de passe**, entrez un mot de passe, puis entrez-le une nouvelle fois dans la zone **Retapez le mot de passe**. 
  
8.  Sélectionnez **OK** pour ajouter le catalogue SSISDB.  
  
## <a name="add-the-package-to-the-ssisdb-catalog"></a>Ajouter le package au catalogue SSISDB  
  
1.  Dans l’**Explorateur d’objets**, cliquez avec le bouton droit sur **SSISDB**, puis sélectionnez **Créer un dossier**.  
  
2.  Dans la boîte de dialogue **Créer un dossier**, entrez SSIS Tutorial dans la zone Nom du dossier, puis sélectionnez **OK**.  
  
3.  Développez le dossier **SSIS Tutorial**, cliquez avec le bouton droit sur **Projets**, puis sélectionnez **Importer les packages**.  
  
4.  Dans la page **Introduction** **de l’Assistant Conversion de projet Integration Services**, sélectionnez **Suivant**.  
  
5.  Dans la page **Localiser les packages**, vérifiez que l’option **Système de fichiers** est sélectionnée dans la liste **Source**, puis sélectionnez **Parcourir**.  
  
6.  Dans la boîte de dialogue **Rechercher un dossier**, accédez au dossier contenant ce projet SSIS Tutorial, puis sélectionnez **OK**.  
  
7.  Sélectionnez **Suivant**.  
  
8.  Dans la page Sélectionner les packages, les six packages du SSIS Tutorial doivent s’afficher. Dans la liste **Packages**, sélectionnez **Lesson 6.dtsx**, puis **Suivant**.  
  
9. Dans la page **Sélectionner la destination**, entrez **SSIS Tutorial Deployment** dans la zone **Nom du projet**, puis sélectionnez **Suivant**.

10. Sélectionnez **Suivant** dans chacune des pages restantes de l’Assistant jusqu’à ce que vous arriviez à la page **Vérifier**.  
  
11. Dans la page **Vérifier**, sélectionnez **Convertir**.  
  
12. Une fois la conversion terminée, sélectionnez **Fermer**.  
  
Quand vous fermez l'Assistant Conversion de projet Integration Services, SSIS affiche l'Assistant Déploiement d'Integration Services. Vous utilisez à présent cet Assistant pour déployer le package de la leçon 6.  
  
1.  Dans la page **Introduction** **de l’Assistant Déploiement d’Integration Services**, passez en revue les étapes à suivre pour déployer le projet, puis sélectionnez **Suivant**.  
  
2.  Dans la page **Sélectionner la destination**, vérifiez que le nom du serveur est l’instance de SQL Server contenant le catalogue SSISDB et que le chemin indique **SSIS Tutorial Deployment**, puis sélectionnez **Suivant**.  
  
3.  Dans la page **Vérifier**, passez en revue le **Résumé**, puis sélectionnez **Déployer**.  
  
4.  Une fois le déploiement terminé, sélectionnez **Fermer**.  
  
5.  Dans l’**Explorateur d’objets**, cliquez avec le bouton droit sur **Catalogues Integration Services**, puis sélectionnez **Actualiser**.  
  
6.  Développez **Catalogues Integration Services**, puis **SSISDB**. Continuez à développer l’arborescence sous **SSIS Tutorial** jusqu’à ce que le projet soit entièrement développé. **Lesson 6.dtsx** doit s’afficher sous le nœud **Packages** du nœud **SSIS Tutorial Deployment**.  
  
7.  Pour vérifier que le package est complet, cliquez avec le bouton droit sur **Lesson 6.dtsx**, puis sélectionnez **Configurer**. Dans la boîte de dialogue **Configurer**, sélectionnez **Paramètres**, puis vérifiez la présence des entrées suivantes : **Lesson 6.dtsx** en tant que **Conteneur**, **VarFolderName** en tant que **Nom** et le chemin de **New Sample Data** comme valeur, puis sélectionnez **Fermer**.  
  
## <a name="create-and-populate-a-new-sample-data-folder"></a>Créer et remplir un nouveau dossier d’exemples de données  
  
1.  Dans l’**Explorateur Windows**, au niveau racine de votre lecteur (par exemple, **C:\\** ), créez un dossier appelé **Sample Data Two**.  
  
2.  Ouvrez le dossier **Exemples de données** mentionné dans les [prérequis de la leçon 1](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md#prerequisites), puis copiez les trois exemples de fichiers.  
  
3.  Accédez au dossier **Sample Data Two**, puis collez les fichiers copiés.  
  
## <a name="change-the-package-parameter-to-point-to-the-new-sample-data"></a>Changer le paramètre de package pour le faire pointer vers les nouveaux exemples de données  
  
1.  Dans l’**Explorateur d’objets**, cliquez avec le bouton droit sur **Lesson 6.dtsx**, puis sélectionnez **Configurer**.  
  
2.  Dans la boîte de dialogue **Configurer**, remplacez la valeur du paramètre par le chemin de **Sample Data Two** ; par exemple, **C:\\Sample Data Two**.  
  
3.  Sélectionnez **OK** pour fermer la boîte de dialogue **Configurer**.  
  
## <a name="test-the-lesson-6-package-deployment"></a>Tester le déploiement du package de la leçon 6  
  
1.  Dans l’**Explorateur d’objets**, cliquez avec le bouton droit sur **Lesson 6.dtsx**, puis sélectionnez **Exécuter**.  
  
2.  Dans la boîte de dialogue **Exécuter le package**, sélectionnez **OK**.  
  
3.  Dans la zone de message, sélectionnez **Oui** pour ouvrir le **rapport Vue d’ensemble**.  
  
Le **rapport Vue d’ensemble** du package affiche le nom du package et une synthèse d’état. La section **Vue d’ensemble de l’exécution** indique le résultat de chaque tâche dans le package. La section **Paramètres utilisés** indique les noms et les valeurs de tous les paramètres utilisés dans l’exécution du package, notamment**VarFolderName**.  
  

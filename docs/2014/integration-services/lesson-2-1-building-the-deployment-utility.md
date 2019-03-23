---
title: 'Étape 1 : Génération de l’utilitaire de déploiement | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1ff4dcff-89b3-4b99-a725-5f7963e98abf
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b788f82fc28ee39e7d65ae484da49313eea7c610
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58381197"
---
# <a name="step-1-building-the-deployment-utility"></a>Étape 1 : Génération de l'utilitaire de déploiement
  Au cours de cette tâche, vous allez configurer et générer un utilitaire de déploiement pour le projet Didacticiel de déploiement.  
  
 Avant de générer l'utilitaire de déploiement, vous devez modifier les propriétés du projet Didacticiel de déploiement. La boîte de dialogue **Pages de propriétés du didacticiel de déploiement** vous permet de configurer ces propriétés. Dans cette boîte de dialogue, vous devez activer la possibilité de mettre à jour des configurations au cours du déploiement et spécifier que le processus de création génère un utilitaire de déploiement. Après avoir défini les propriétés, vous allez générer le projet.  
  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] fournit un jeu de fenêtres que vous pouvez utiliser pour déboguer les packages. Vous pouvez afficher les messages d'erreur, d'information et d'avertissement, effectuer le suivi du statut des packages lors de l'exécution ou afficher la progression et les résultats des processus de génération. Pour cette leçon, vous allez utiliser la fenêtre de sortie pour afficher la progression et les résultats de la génération de l'utilitaire de déploiement.  
  
### <a name="to-set-the-deployment-utility-properties"></a>Pour définir les propriétés de l'utilitaire de déploiement  
  
1.  Si [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] n’est pas déjà ouvert, dans le menu **Démarrer**, pointez sur **Tous les programmes**, puis sur **Microsoft SQL Server**et cliquez sur **Business Intelligence Development Studio**.  
  
2.  Dans le menu **Fichier** , cliquez successivement sur **Ouvrir**, sur **Projet/Solution**, sur le dossier **Didacticiel de déploiement** et sur **Ouvrir**, puis double-cliquez sur **Deployment Tutorial.sln**.  
  
3.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur Didacticiel de déploiement, puis cliquez sur **Propriétés**.  
  
4.  Dans la boîte de dialogue **Pages de propriétés du didacticiel de déploiement** , développez Propriétés de configuration et cliquez sur Utilitaire de déploiement.  
  
5.  Dans le volet droit de la **Pages de propriétés de didacticiel de déploiement** boîte de dialogue, vérifiez que `AllowConfigurationChanges` a la valeur `true`, affectez la valeur `CreateDeploymentUtility` à `true`et éventuellement mettre à jour la valeur par défaut `DeploymentOutputPath`.  
  
6.  Cliquez sur **OK**.  
  
### <a name="to-build-the-deployment-utility"></a>Pour générer l'utilitaire de déploiement  
  
1.  Dans l’Explorateur de solutions, cliquez sur **Didacticiel de déploiement**.  
  
2.  Dans le menu **Affichage** , cliquez sur **Sortie**. Par défaut, la fenêtre de sortie se trouve dans le coin inférieur gauche de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
3.  Dans le menu **Générer** , cliquez sur **Générer le didacticiel de déploiement**.  
  
4.  Dans la fenêtre de sortie, vérifiez les informations suivantes :  
  
     Création démarrée : projet SQL Integration Services : incrémentiel ...  
  
     Création de l'utilitaire de déploiement...  
  
     Utilitaire de déploiement créé.  
  
     Fin de la génération -- 0 erreur, 0 avertissement  
  
     ========== Génération : 0 réussi, 0 échoué, 1 mis à jour, 0 ignoré ==========  
  
5.  Dans le menu **Fichier** , cliquez sur **Quitter**. Si vous êtes invité à enregistrer les modifications apportées aux éléments du didacticiel de déploiement, cliquez sur **Oui**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Étape 2 : Vérification du Bundle de déploiement](../integration-services/lesson-2-2-verifying-the-deployment-bundle.md)  
  
![Icône Integration Services (petite)](media/dts-16.gif "icône Integration Services (petite)")**rester jusqu'à la Date avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un utilitaire de déploiement](../../2014/integration-services/create-a-deployment-utility.md)  
  
  

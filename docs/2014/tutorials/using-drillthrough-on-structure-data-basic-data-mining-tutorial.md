---
title: Utilisation de l’extraction des données de Structure (didacticiel d’exploration de données de base de données) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a693979c-0564-4d6d-b35d-cbbc8f350469
caps.latest.revision: 19
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 71a8fa3ac449c8d9427ea138206fbd0c1ea8f1ef
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312457"
---
# <a name="using-drillthrough-on-structure-data-basic-data-mining-tutorial"></a>Utilisation de l'extraction sur les données de structure (Didacticiel sur l'exploration de données de base)
  Dans le cadre de leur campagne de publicité, [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] envoie un courrier électronique aux clients potentiels dans l’âge 34-40 démographiques. Le service marketing a décidé qu’ils souhaitent également adresser ce courrier aux clients ayant acheté des vélos dans [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] il y a plus de cinq ans. Dans cette leçon vous allez identifier les clients ayant des vélos anciens et extraire leurs informations de contact. Ces informations ne sont pas incluses dans le modèle, mais sont incluses dans la structure. Pour extraire les informations de contact, vous allez d'abord vérifier que l'extraction est activée pour la structure puis vous utiliserez l'extraction pour extraire les noms et adresses des clients ciblés.  
  
### <a name="to-enable-drillthrough-on-a-mining-model"></a>Pour activer l'extraction sur un modèle d'exploration de données  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], dans le **des modèles d’exploration de données** onglet du Concepteur d’exploration de données, cliquez sur le **TM_Decision_Tree** de modèle, puis sélectionnez **propriétés**.  
  
2.  Dans les fenêtres Propriétés, cliquez sur **AllowDrillthrough**et sélectionnez **True**.  
  
3.  Sous l'onglet Modèles d'exploration de données, cliquez avec le bouton droit sur le modèle et sélectionnez **Traiter le modèle**.  
  
 Pour plus d’informations, consultez [requêtes d’extraction &#40;d’exploration de données&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)  
  
### <a name="to-view-drillthrough-data-from-a-mining-model"></a>Pour afficher des données d'extraction à partir d'un modèle d'exploration de données  
  
1.  Dans le Concepteur d'exploration de données, cliquez sur l'onglet **Visionneuse de modèle d'exploration de données** .  
  
2.  Sélectionnez le modèle **TM_Decision_Tree** dans la liste **Modèle d'exploration de données** .  
  
3.  Modifier la **arrière-plan** valeur `1`. Ce faisant, vous affichez uniquement la partie du modèle qui est associée au client qui a acheté des vélos.  
  
4.  Sélectionnez la Visionneuse d'arborescences Microsoft dans la liste **Visionneuse** . Cela force la visionneuse à actualiser avec les nouvelles conditions de filtre. Ensuite, localisez le **âge > = 34 et < 41** nœud et avec le bouton du nœud.  
  
5.  Sélectionnez **Extraire**, puis sélectionnez **Colonnes de structure et de modèle** pour ouvrir la fenêtre **Extraire** .  
  
6.  Faites défiler jusqu'à la colonne **Structure.Date First Purchase** pour consulter les dates d'achat pour les vélos anciens.  
  
7.  Pour copier les données vers le Presse-papiers, cliquez avec le bouton droit sur une ligne quelconque dans la table et sélectionnez **Copier tout**.  
  
 Félicitations, vous avez terminé le didacticiel sur l'exploration de données de base. Maintenant que vous maîtrisez les outils d'exploration de données, nous vous recommandons de compléter également le didacticiel intermédiaire sur l'exploration de données qui montre comment créer des modèles pour la prévision, l'analyse du panier d'achat et Sequence Clustering.  
  
## <a name="previous-task-in-lesson"></a>Tâche précédente de la leçon  
 [Création de prédictions &#40;didacticiel d’exploration de données de base de données&#41;](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une requête de prédiction à l’aide du Générateur de requêtes de prédiction](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
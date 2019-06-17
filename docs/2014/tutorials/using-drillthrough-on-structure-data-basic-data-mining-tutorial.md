---
title: Utilisation de l’extraction de données de Structure (didacticiel d’exploration de données de base) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a693979c-0564-4d6d-b35d-cbbc8f350469
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 68d5d29a4aed7380bd7a53c65d140aac24912392
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62745540"
---
# <a name="using-drillthrough-on-structure-data-basic-data-mining-tutorial"></a>Utilisation de l'extraction sur les données de structure (Didacticiel sur l'exploration de données de base)
  Dans le cadre de leur campagne de publicité, [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] envoie un courrier de publipostage à des clients potentiels dans la tranche d'âge 34-40 ans. Le service marketing souhaite également adresser ce courrier aux clients ayant acheté des vélos dans [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] il y a plus de cinq ans. Dans cette leçon vous allez identifier les clients ayant des vélos anciens et extraire leurs informations de contact. Ces informations ne sont pas incluses dans le modèle, mais sont incluses dans la structure. Pour extraire les informations de contact, vous allez d'abord vérifier que l'extraction est activée pour la structure puis vous utiliserez l'extraction pour extraire les noms et adresses des clients ciblés.  
  
### <a name="to-enable-drillthrough-on-a-mining-model"></a>Pour activer l'extraction sur un modèle d'exploration de données  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], dans l'onglet **Modèles d'exploration de données** du Concepteur d'exploration de données, cliquez avec le bouton droit sur le modèle **TM_Decision_Tree** , et sélectionnez **Propriétés**.  
  
2.  Dans les fenêtres Propriétés, cliquez sur **AllowDrillthrough**et sélectionnez **True**.  
  
3.  Sous l'onglet Modèles d'exploration de données, cliquez avec le bouton droit sur le modèle et sélectionnez **Traiter le modèle**.  
  
 Pour plus d’informations, consultez [requêtes d’extraction &#40;d’exploration de données&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)  
  
### <a name="to-view-drillthrough-data-from-a-mining-model"></a>Pour afficher des données d'extraction à partir d'un modèle d'exploration de données  
  
1.  Dans le Concepteur d'exploration de données, cliquez sur l'onglet **Visionneuse de modèle d'exploration de données** .  
  
2.  Sélectionnez le modèle **TM_Decision_Tree** dans la liste **Modèle d'exploration de données** .  
  
3.  Modifier le **arrière-plan** valeur `1`. Ce faisant, vous affichez uniquement la partie du modèle qui est associée au client qui a acheté des vélos.  
  
4.  Sélectionnez la Visionneuse d'arborescences Microsoft dans la liste **Visionneuse** . Cela force la visionneuse à actualiser avec les nouvelles conditions de filtre. Ensuite, localisez le **âge > = 34 et < 41** nœud et le nœud de clic droit.  
  
5.  Sélectionnez **Extraire**, puis sélectionnez **Colonnes de structure et de modèle** pour ouvrir la fenêtre **Extraire** .  
  
6.  Faites défiler jusqu'à la colonne **Structure.Date First Purchase** pour consulter les dates d'achat pour les vélos anciens.  
  
7.  Pour copier les données vers le Presse-papiers, cliquez avec le bouton droit sur une ligne quelconque dans la table et sélectionnez **Copier tout**.  
  
 Félicitations, vous avez terminé le didacticiel sur l'exploration de données de base. Maintenant que vous maîtrisez les outils d'exploration de données, nous vous recommandons de compléter également le didacticiel intermédiaire sur l'exploration de données qui montre comment créer des modèles pour la prévision, l'analyse du panier d'achat et Sequence Clustering.  
  
## <a name="previous-task-in-lesson"></a>Tâche précédente de la leçon  
 [Création de prédictions &#40;Didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une requête de prédiction à l’aide du Générateur de requêtes de prédiction](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  

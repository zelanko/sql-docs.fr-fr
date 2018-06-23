---
title: Exploration du modèle Naive Bayes (didacticiel d’exploration de données de base de données) | Documents Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b06708d5-4477-4a51-bf8d-0b1e3c1f9ebb
caps.latest.revision: 25
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ce01a9d352513e4b69bb4a9e735f30cc657a9c97
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36311857"
---
# <a name="exploring-the-naive-bayes-model-basic-data-mining-tutorial"></a>Exploration du modèle Naive Bayes (Didacticiel sur l'exploration de données de base)
  Le [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithme Naive Bayes fournit plusieurs méthodes pour l’affichage de l’interaction entre les attributs d’entrée et de vélos.  
  
 Le [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes Viewer fournit les onglets suivants pour Explorer les modèles d’exploration de données Naive Bayes :  
  
 
  
##  <a name="DependencyNetwork"></a> Réseau de dépendances  
 Le **réseau de dépendances** onglet fonctionne de la même façon que les **réseau de dépendances** pour l’onglet du [!INCLUDE[msCoName](../includes/msconame-md.md)] visionneuse de l’arborescence. Chaque nœud dans la visionneuse représente un attribut et les lignes entre les nœuds représentent des relations. Dans la visionneuse, vous pouvez voir tous les attributs qui ont une incidence sur l'état de l'attribut prédictible Bike Buyer.  
  
#### <a name="to-explore-the-model-in-the-dependency-network-tab"></a>Pour explorer le modèle sous l'onglet Réseau de dépendances  
  
1.  Utilisez le **modèle d’exploration de données** liste en haut de la **visionneuse de modèle d’exploration de données** tab pour passer à la `TM_NaiveBayes` modèle.  
  
2.  Utilisez le **visionneuse** liste pour passer à **Microsoft Naive Bayes visionneuse**.  
  
3.  Cliquez sur le `Bike Buyer` nœud pour identifier ses dépendances.  
  
     L'ombrage rose indique que tous les attributs ont des répercussions sur l'achat de vélos.  
  
4.  Ajustez le curseur pour identifier l'attribut le plus influent.  
  
     Si vous faites glisser le curseur vers le bas, seuls les attributs qui ont la plus grande incidence sur la colonne [Bike Buyer] restent affichés. En ajustant le curseur, vous pouvez constater que les attributs les plus influents sont : le nombre de voitures possédées, la distance domicile-travail, et le nombre total d'enfants.  
 
  
##  <a name="AttributeProfiles"></a> Profils d’attribut  
 Le **profils d’attribut** onglet décrit comment les différents États des attributs d’entrée affectent le résultat de l’attribut prédictible.  
  
#### <a name="to-explore-the-model-in-the-attribute-profiles-tab"></a>Pour explorer le modèle sous l'onglet Profils d'attribut  
  
1.  Dans le **prédictible** , vérifier que `Bike Buyer` est sélectionné.  
  
2.  Si le **légende d’exploration de données** bloque l’affichage de la **profils d’attribut**, déplacez-la à l’écart.  
  
3.  Dans le **histogramme** zone barres, sélectionnez **5**.  
  
     Dans notre modèle, 5 est le nombre maximal d'états pour toute variable.  
  
     Les attributs qui affectent l'état de cet attribut prédictible sont présentés avec les valeurs de chaque état des attributs d'entrée et avec leurs distributions dans chaque état de l'attribut prédictible.  
  
4.  Dans le **attributs** colonne, recherchez **Number Cars Owned**.  Remarquez les différences dans les histogrammes pour les acheteurs de vélo (colonne intitulée 1) et les non-acheteurs (colonne intitulée 0). Une personne avec zéro ou une voiture est beaucoup plus susceptible d'acheter un vélo.  
  
5.  Double-cliquez sur le **Number Cars Owned** cellule de l’acheteur de vélo (colonne intitulée 1) de colonnes.  
  
     Le **légende d’exploration de données** affiche une vue plus détaillée.  
  
  
##  <a name="AttributeCharacteristics"></a> Caractéristiques d’attribut  
 Avec la **caractéristiques d’attribut** onglet, vous pouvez sélectionner un attribut et une valeur à la fréquence à laquelle les valeurs des autres attributs s’affiche dans les cas de la valeur sélectionnée.  
  
#### <a name="to-explore-the-model-in-the-attribute-characteristics-tab"></a>Pour explorer le modèle sous l'onglet Caractéristiques d'attribut  
  
1.  Dans le **attribut** liste, vérifiez que `Bike Buyer` est sélectionné.  
  
2.  Définir le **valeur** à **1**.  
  
     Dans la visionneuse, vous constaterez que les clients qui n'ont pas d'enfants, font des trajets courts entre leur domicile et bureau, et habitent dans la région North America sont plus susceptibles d'acheter un vélo.  
  
  
##  <a name="AttributeDiscrimination"></a> Discrimination d’attribut  
 Avec la **Discrimination d’attribut** onglet, vous pouvez examiner la relation entre deux valeurs discrètes de vélos et d’autres valeurs d’attribut. Étant donné que le `TM_NaiveBayes` modèle a seulement deux États, 1 et 0, il est inutile d’apporter des modifications à la visionneuse.  
  
 Dans la visionneuse, vous constatez que les personnes qui ne sont pas propriétaires de voitures achètent généralement des vélos et que les personnes propriétaires de deux voitures n'en achètent généralement pas.  
  
## <a name="related-tasks"></a>Related Tasks  
 Voir les rubriques qui suivent pour explorer les autres modèles d'exploration de données.  
  
-   [Exploration du modèle Decision Tree &#40;didacticiel d’exploration de données de base de données&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [Exploration du modèle de Clustering &#40;didacticiel d’exploration de données de base de données&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 5 : Test des modèles &#40;didacticiel d’exploration de données de base de données&#41;](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>Tâche précédente de la leçon  
 [Exploration du modèle de Clustering &#40;didacticiel d’exploration de données de base de données&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Parcourir un modèle à l’aide de l’Observateur de Microsoft Naive Bayes](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)   
 [Onglet Discrimination d’attribut &#40;visionneuse de modèle d’exploration de données&#41;](../../2014/analysis-services/attribute-discrimination-tab-mining-model-viewer.md)   
 [Attribut profils onglet &#40;visionneuse de modèle d’exploration de données&#41;](../../2014/analysis-services/attribute-profiles-tab-mining-model-viewer.md)   
 [Onglet caractéristiques d’attribut &#40;visionneuse de modèle d’exploration de données&#41;](../../2014/analysis-services/attribute-characteristics-tab-mining-model-viewer.md)   
 [Onglet réseau de dépendances &#40;visionneuse de modèle d’exploration de données&#41;](../../2014/analysis-services/dependency-network-tab-mining-model-viewer.md)  
  
  
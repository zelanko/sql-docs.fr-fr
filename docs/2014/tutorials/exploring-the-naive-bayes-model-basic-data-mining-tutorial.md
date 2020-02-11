---
title: Exploration du modèle Naive Bayes (didacticiel sur l’exploration de données de base) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b06708d5-4477-4a51-bf8d-0b1e3c1f9ebb
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: eb35c829b798335a27a37629711acf299ac2c7c9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62472883"
---
# <a name="exploring-the-naive-bayes-model-basic-data-mining-tutorial"></a>Exploration du modèle Naive Bayes (Didacticiel sur l'exploration de données de base)
  L' [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithme Naive Bayes fournit plusieurs méthodes pour afficher l’interaction entre l’achat de vélo et les attributs d’entrée.  
  
 La [!INCLUDE[msCoName](../includes/msconame-md.md)] visionneuse Naive Bayes fournit les onglets suivants pour l’exploration des modèles d’exploration de données Naive Bayes :  
  
 
  
##  <a name="DependencyNetwork"></a>Réseau de dépendances  
 L’onglet **réseau de dépendances** fonctionne de la même façon que l’onglet réseau de [!INCLUDE[msCoName](../includes/msconame-md.md)] **dépendances** de la visionneuse de l’arborescence. Chaque nœud dans la visionneuse représente un attribut et les lignes entre les nœuds représentent des relations. Dans la visionneuse, vous pouvez voir tous les attributs qui ont une incidence sur l'état de l'attribut prédictible Bike Buyer.  
  
#### <a name="to-explore-the-model-in-the-dependency-network-tab"></a>Pour explorer le modèle sous l'onglet Réseau de dépendances  
  
1.  Utilisez la liste **modèle d’exploration de données** en haut de l’onglet **visionneuse de modèle** d' `TM_NaiveBayes` exploration de données pour basculer vers le modèle.  
  
2.  Utilisez la liste **visionneuse** pour basculer vers la **visionneuse Microsoft Naive Bayes**.  
  
3.  Cliquez sur `Bike Buyer` le nœud pour identifier ses dépendances.  
  
     L'ombrage rose indique que tous les attributs ont des répercussions sur l'achat de vélos.  
  
4.  Ajustez le curseur pour identifier l'attribut le plus influent.  
  
     Si vous faites glisser le curseur vers le bas, seuls les attributs qui ont la plus grande incidence sur la colonne [Bike Buyer] restent affichés. En ajustant le curseur, vous pouvez constater que les attributs les plus influents sont : le nombre de voitures possédées, la distance domicile-travail, et le nombre total d'enfants.  
 
  
##  <a name="AttributeProfiles"></a>Profils d’attribut  
 L’onglet **profils d’attribut** décrit comment les différents États des attributs d’entrée affectent le résultat de l’attribut prévisible.  
  
#### <a name="to-explore-the-model-in-the-attribute-profiles-tab"></a>Pour explorer le modèle sous l'onglet Profils d'attribut  
  
1.  Dans la zone **prévisible** , vérifiez que `Bike Buyer` est sélectionné.  
  
2.  Si la **légende d’exploration de données** bloque l’affichage des **profils d’attribut**, déplacez-le hors de la voie.  
  
3.  Dans la zone barres de l' **histogramme** , sélectionnez **5**.  
  
     Dans notre modèle, 5 est le nombre maximal d'états pour toute variable.  
  
     Les attributs qui affectent l'état de cet attribut prédictible sont présentés avec les valeurs de chaque état des attributs d'entrée et avec leurs distributions dans chaque état de l'attribut prédictible.  
  
4.  Dans la colonne **attributs** , recherchez **Number Cars possédé**.  Remarquez les différences dans les histogrammes pour les acheteurs de vélo (colonne intitulée 1) et les non-acheteurs (colonne intitulée 0). Une personne avec zéro ou une voiture est beaucoup plus susceptible d'acheter un vélo.  
  
5.  Double-cliquez sur la cellule **Number Cars possédé** de la colonne Bike Buyer (colonne intitulée 1).  
  
     La **légende d’exploration de données** affiche une vue plus détaillée.  
  
  
##  <a name="AttributeCharacteristics"></a>Caractéristiques d’attribut  
 Avec l’onglet **caractéristiques d’attribut** , vous pouvez sélectionner un attribut et une valeur pour voir la fréquence à laquelle les valeurs d’autres attributs apparaissent dans les cas de valeur sélectionnés.  
  
#### <a name="to-explore-the-model-in-the-attribute-characteristics-tab"></a>Pour explorer le modèle sous l'onglet Caractéristiques d'attribut  
  
1.  Dans la liste **attribut** , vérifiez que `Bike Buyer` est sélectionné.  
  
2.  Définissez la **valeur** sur **1**.  
  
     Dans la visionneuse, vous constaterez que les clients qui n'ont pas d'enfants, font des trajets courts entre leur domicile et bureau, et habitent dans la région North America sont plus susceptibles d'acheter un vélo.  
  
  
##  <a name="AttributeDiscrimination"></a>Discrimination d’attribut  
 Avec l’onglet **discrimination d’attribut** , vous pouvez examiner la relation entre deux valeurs discrètes de l’achat de vélos et d’autres valeurs d’attribut. Étant donné `TM_NaiveBayes` que le modèle n’a que deux États, 1 et 0, il n’est pas nécessaire d’apporter des modifications à la visionneuse.  
  
 Dans la visionneuse, vous constatez que les personnes qui ne sont pas propriétaires de voitures achètent généralement des vélos et que les personnes propriétaires de deux voitures n'en achètent généralement pas.  
  
## <a name="related-tasks"></a>Tâches associées  
 Voir les rubriques qui suivent pour explorer les autres modèles d'exploration de données.  
  
-   [Exploration du modèle d’arbre de décision &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [Exploration du modèle de clustering &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 5 : tester les modèles &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>Tâche précédente de la leçon  
 [Exploration du modèle de clustering &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Parcourir un modèle à l’aide de Microsoft Naive Bayes Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)   
 [Onglet discrimination d’attribut &#40;la visionneuse de modèle d’exploration de données&#41;](../../2014/analysis-services/attribute-discrimination-tab-mining-model-viewer.md)   
 [Onglet Profils d’attribut &#40;visionneuse de modèle d’exploration de données&#41;](../../2014/analysis-services/attribute-profiles-tab-mining-model-viewer.md)   
 [Onglet caractéristiques d’attribut &#40;visionneuse de modèle d’exploration de données&#41;](../../2014/analysis-services/attribute-characteristics-tab-mining-model-viewer.md)   
 [Onglet réseau de dépendances &#40;la visionneuse de modèle d’exploration de données&#41;](../../2014/analysis-services/dependency-network-tab-mining-model-viewer.md)  
  
  

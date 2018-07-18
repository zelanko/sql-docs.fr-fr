---
title: La décision de l’onglet arbre (visionneuse de modèle d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.decisiontree.f1
ms.assetid: dc88606f-ba7c-4f8d-af65-bfa17ec16e2b
caps.latest.revision: 22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 86c229c4adc57200a2d1867c167aa3d998498765
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37276335"
---
# <a name="decision-tree-tab-mining-model-viewer"></a>Onglet Arbre de décision (Visionneuse de modèle d'exploration de données)
  Le volet **Arbre de décision** affiche une représentation visuelle des règles de décision créées dans un modèle d’arbre de décision. Les règles de décision décrivent les chemins d'accès vers certains résultats.  
  
 **Pour plus d’informations :** [Algorithme MDT (Microsoft Decision Trees)](data-mining/microsoft-decision-trees-algorithm.md), [Explorer un modèle à l’aide de la Visionneuse d’arborescences Microsoft](data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)  
  
## <a name="options"></a>Options  
 **Actualiser le contenu de l’Observateur**  
 Recharge le modèle d'exploration de données dans la visionneuse.  
  
 **Modèle d'exploration de données**  
 Choisissez un modèle d'exploration de données parmi ceux de la structure d'exploration de données active. Le modèle d'exploration de données s'ouvre dans sa visionneuse associée.  
  
 **Visionneuse**  
 Choisissez la visionneuse à utiliser pour explorer le modèle d'exploration de données sélectionné. Vous pouvez utiliser la visionneuse personnalisée ou la visionneuse de contenu d’exploration de données ( [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer). Vous pouvez également utiliser les visionneuses de plug-in, le cas échéant.  
  
 **Zoom avant**  
 Effectuez un zoom avant pour obtenir une vue plus détaillée des nœuds et des branches dans l'arbre de décision. Dans un modèle complexe, les arbres de décision peuvent avoir un grand nombre de niveaux de branchement.  
  
 **Effectuer un zoom arrière**  
 Effectuez un zoom arrière pour obtenir une vue d'ensemble de la structure arborescente.  
  
 **Copier la vue du graphique**  
 Copie la partie visible du diagramme dans le Presse-papiers.  
  
 **Copier le graphique entier**  
 Copie la totalité du diagramme dans le Presse-papiers.  
  
 **Diagramme de mise à l’échelle à la fenêtre**  
 Réduit la taille du diagramme jusqu'à ce que l'intégralité de la structure arborescente soit ajustée à la taille de l'écran.  
  
 **Histogrammes**  
 Sélectionnez le nombre d'états pouvant être affichés dans l'histogramme pour chaque nœud. Si le nombre d'états dans le modèle est inférieur à la valeur que vous sélectionnez, aucune barre supplémentaire n'est affichée.  
  
 **Arborescence**  
 Choisissez un arbre à afficher dans la visionneuse. Si vous créez un modèle qui comporte plusieurs attributs prédictibles, l'algorithme crée une arborescence distincte pour chaque attribut prédictible.  
  
 **Arrière-plan**  
 Choisissez une valeur de l'attribut prédictible à utiliser pour représenter la couleur d'arrière-plan de chaque nœud. Dans les exemples de modèles AdventureWorks, si **Arrière-plan** est défini à la valeur 1 ([Bike Buyer] = Yes), les nœuds sont plus foncés s’ils ont une proportion supérieure d’acquéreurs de vélo. Cette option fournit un indice visuel supplémentaire concernant la signification des branches et des nœuds dans l'arborescence.  
  
 **Expansion par défaut**  
 Choisissez une valeur dans la liste afin de définir la valeur par défaut pour le nombre de niveaux affichés dans le graphique de l'arborescence.  
  
 **Afficher le niveau**  
 Déplacez la barre de curseur vers la gauche ou la droite afin d'ajuster le nombre de niveaux affichés dans le graphique de l'arborescence. Pour voir tous les nœuds du modèle, faites glisser la barre complètement à droite.  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visionneuses de modèle d’exploration de données &#40;Concepteur de modèle d’exploration de données&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visionneuses de modèle d’exploration de données](data-mining/data-mining-model-viewers.md)  
  
  

---
title: Exploration des visionneuses de modèle (Concepteur de modèle d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.viewers.f1
ms.assetid: 4ba391d5-c97b-4848-ba7c-7d096fa4b7dd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 67cd89f4cf857f11f08f69769ff54a22fd83760f
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66077739"
---
# <a name="mining-model-viewers-data-mining-model-designer"></a>Visionneuses de modèle d'exploration de données (Concepteur de modèle d'exploration de données)
  Utilisez l’onglet **Visionneuse de modèle d’exploration de données** pour explorer les modèles d’exploration de données d’une structure associée.  
  
 Vous devez sélectionner le modèle d'exploration de données, puis sélectionner une visionneuse. Chaque modèle comporte toujours deux visionneuses disponibles : une visionneuse personnalisée, qui peut inclure plusieurs onglets, et la visionneuse générique.  
  
 Pour connaître la procédure pas à pas d’utilisation de chaque visionneuse, consultez [Visionneuses de modèle d’exploration de données](data-mining/data-mining-model-viewers.md).  
  
## <a name="common-options"></a>Options courantes  
 **Actualiser le contenu de l’Observateur**  
 Recharge le modèle d'exploration de données dans la visionneuse.  
  
 **Modèle d'exploration de données**  
 Choisissez un modèle d'exploration de données pour afficher le contenu de la structure d'exploration actuelle. Le modèle d'exploration de données s'ouvre tout d'abord dans sa visionneuse personnalisée associée.  
  
 **Visionneuse**  
 Choisissez la visionneuse à utiliser pour explorer le modèle d'exploration de données sélectionné. Cette liste contient les visionneuses fournies par [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] pour chaque modèle d’exploration de données, [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer et les visionneuses de plug-in.  
  
 Le diagramme suivant représente une visionneuse personnalisée et la visionneuse générique pour le même modèle.  
  
-   Le diagramme supérieur affiche la visionneuse pour un modèle d'exploration de données basé sur l'algorithme MTS (Microsoft Time Series). Cette visionneuse personnalisée particulière crée automatiquement un graphique de la série chronologique et fournit cinq prédictions.  
  
-   Le diagramme inférieur représente le même modèle affiché avec la **visionneuse de l’arborescence de contenu générique Microsoft**. Cette visionneuse présente le contenu du modèle d'exploration de données selon un schéma standardisé. Pour plus d’informations, consultez [Visionneuse de l’arborescence de contenu générique Microsoft &#40;exploration de données&#41;](microsoft-generic-content-tree-viewer-data-mining.md).  
  
 ![Vue d’ensemble du Concepteur de modèles d’exploration de données](media/generic-mining-model-tab1.gif "vue d’ensemble du Concepteur de modèles d’exploration de données")  
  
## <a name="viewers-and-their-components"></a>Visionneuses et leurs composants  
 Selon le modèle que vous sélectionnez, vous verrez une visionneuse personnalisée différente, adaptée à l'algorithme que vous avez utilisé pour créer le modèle d'exploration de données sélectionné. Chaque visionneuse personnalisée comporte divers outils et boîtes de dialogue qui vous permettent d'explorer les statistiques et les modèles dans le modèle.  
  
 La liste suivante décrit les options dans chacune des visionneuses personnalisées.  
  
### <a name="microsoft-association-rules-algorithm"></a>Algorithme MAR (Microsoft Association Rules)  
  
-   [Explorer un modèle à l’aide de la visionneuse de l’algorithme MAR (Microsoft Association Rules)](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)  
  
    -   [Onglet jeux d’éléments &#40;visionneuse de modèle d’exploration de données&#41;](itemsets-tab-mining-model-viewer.md)  
  
    -   [Onglet règles &#40;visionneuse de modèle d’exploration de données&#41;](rules-tab-mining-model-viewer.md)  
  
    -   [Onglet réseau de dépendances &#40;visionneuse de modèle d’exploration de données&#41;](dependency-network-tab-mining-model-viewer.md)  
  
### <a name="microsoft-clustering-algorithm"></a>Algorithme de clustering Microsoft  
  
-   [Explorer un modèle à l’aide de Microsoft Cluster Viewer](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)  
  
    -   [Onglet Diagramme de cluster &#40;visionneuse de modèle d’exploration de données&#41;](cluster-diagram-tab-mining-model-viewer.md)  
  
    -   [Onglet Profils de cluster &#40;visionneuse de modèle d’exploration de données&#41;](cluster-profiles-tab-mining-model-viewer.md)  
  
    -   [Onglet caractéristiques du cluster &#40;visionneuse de modèle d’exploration de données&#41;](cluster-characteristics-tab-mining-model-viewer.md)  
  
    -   [Onglet Discrimination de cluster &#40;visionneuse de modèle d’exploration de données&#41;](cluster-discrimination-tab-mining-model-viewer.md)  
  
    -   [Boîte de dialogue Légende d’exploration de données &#40;visionneuse de modèle d’exploration de données&#41;](mining-legend-dialog-box-mining-model-viewer.md)  
  
### <a name="microsoft-decision-tree-algorithm"></a>Algorithme MDT (Microsoft Decision Trees)  
  
-   [Explorer un modèle à l’aide de la visionneuse d’arborescences Microsoft](data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)  
  
    -   [Onglet arbre de décision &#40;visionneuse de modèle d’exploration de données&#41;](decision-tree-tab-mining-model-viewer.md)  
  
    -   [Onglet réseau de dépendances &#40;visionneuse de modèle d’exploration de données&#41;](dependency-network-tab-mining-model-viewer.md)  
  
    -   [Boîte de dialogue Légende d’exploration de données &#40;visionneuse de modèle d’exploration de données&#41;](mining-legend-dialog-box-mining-model-viewer.md)  
  
### <a name="microsoft-linear-regression-algorithm"></a>Algorithme MLR (Microsoft Linear Regression)  
  
-   [Explorer un modèle à l’aide de la visionneuse de l’algorithme MNN (Microsoft Neural Network)](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)  
  
    -   [Onglet arbre de décision &#40;visionneuse de modèle d’exploration de données&#41;](decision-tree-tab-mining-model-viewer.md)  
  
    -   [Onglet réseau de dépendances &#40;visionneuse de modèle d’exploration de données&#41;](dependency-network-tab-mining-model-viewer.md)  
  
    -   [Boîte de dialogue Légende d’exploration de données &#40;visionneuse de modèle d’exploration de données&#41;](mining-legend-dialog-box-mining-model-viewer.md)  
  
### <a name="microsoft-logistic-regression-algorithm"></a>Algorithme MLR (Microsoft Logistic Regression)  
  
-   [Explorer un modèle à l’aide de la visionneuse de l’algorithme MNN (Microsoft Neural Network)](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)  
  
### <a name="microsoft-nave-bayes-algorithm"></a>Algorithme MNB (Microsoft Naïve Bayes)  
  
-   [Explorer un modèle à l’aide de la visionneuse de l’algorithme MNB (Microsoft Naive Bayes)](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
  
    -   [Onglet réseau de dépendances &#40;visionneuse de modèle d’exploration de données&#41;](dependency-network-tab-mining-model-viewer.md)  
  
    -   [Attribut profils onglet &#40;visionneuse de modèle d’exploration de données&#41;](attribute-profiles-tab-mining-model-viewer.md)  
  
    -   [Onglet caractéristiques d’attribut &#40;visionneuse de modèle d’exploration de données&#41;](attribute-characteristics-tab-mining-model-viewer.md)  
  
    -   [Onglet Discrimination d’attribut &#40;visionneuse de modèle d’exploration de données&#41;](attribute-discrimination-tab-mining-model-viewer.md)  
  
### <a name="microsoft-neural-network-algorithm"></a>Microsoft Neural Network Algorithm  
  
-   [Explorer un modèle à l’aide de la visionneuse de l’algorithme MNN (Microsoft Neural Network)](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)  
  
    -   [Onglet réseau de dépendances &#40;visionneuse de modèle d’exploration de données&#41;](dependency-network-tab-mining-model-viewer.md)  
  
    -   [Réseau neuronal &#40;visionneuse de modèle d’exploration de données&#41;](neural-network-mining-model-viewer.md)  
  
    -   [Boîte de dialogue de nœud rechercher &#40;visionneuse de modèle d’exploration de données&#41;](find-node-dialog-box-mining-model-viewer.md)  
  
### <a name="microsoft-sequence-clustering-algorithm"></a>Algorithme MSC (Microsoft Sequence Clustering)  
  
-   [Explorer un modèle à l’aide de la visionneuse de l’algorithme MSC (Microsoft Sequence Cluster)](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
    -   [Sequence Clustering onglet Diagramme de Cluster &#40;visionneuse de modèle d’exploration de données](sequence-clustering-cluster-diagram-tab-mining-model-viewer.md)  
  
    -   [Onglet Profils de Sequence Clustering Cluster &#40;visionneuse de modèle d’exploration de données](sequence-clustering-cluster-profiles-tab-mining-model-viewer.md)  
  
    -   [Onglet caractéristiques du Cluster de Clustering de séquence &#40;visionneuse de modèle d’exploration de données&#41;](sequence-clustering-cluster-characteristics-tab-mining-model-viewer.md)  
  
    -   [Onglet Discrimination de Cluster de Clustering de séquence &#40;visionneuse de modèle d’exploration de données&#41;](sequence-clustering-cluster-discrimination-tab-mining-model-viewer.md)  
  
    -   [Sequence Clustering onglet transition d’état &#40;visionneuse de modèle d’exploration de données&#41;](sequence-clustering-cluster-transition-tab-mining-model-viewer.md)  
  
### <a name="microsoft-time-series-algorithm"></a>Algorithme MTS (Microsoft Time Series)  
  
-   [Explorer un modèle à l’aide de la visionneuse de l’algorithme MTS (Microsoft Time Series)](data-mining/browse-a-model-using-the-microsoft-time-series-viewer.md)  
  
    -   [Onglet de modèle &#40;visionneuses de modèle d’exploration de données&#41;](model-tab-mining-model-viewers.md)  
  
    -   [Onglet graphique &#40;visionneuses de modèle d’exploration de données&#41;](chart-tab-mining-model-viewers.md)  
  
    -   [Boîte de dialogue Légende d’exploration de données &#40;visionneuse de modèle d’exploration de données&#41;](mining-legend-dialog-box-mining-model-viewer.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue modèles d’exploration de données &#40;Concepteur de modèle d’exploration de données&#41;](mining-models-view-data-mining-model-designer.md)   
 [Vue de Structure d’exploration de données &#40;Concepteur de modèle d’exploration de données&#41;](mining-structure-view-data-mining-model-designer.md)   
 [Concepteur graphique d’analyse de précision d’exploration de données &#40;exploration de données&#41;](mining-accuracy-chart-designer-data-mining.md)   
 [Générateur de requêtes de prédiction &#40;exploration de données&#41;](prediction-query-builder-data-mining.md)  
  
  

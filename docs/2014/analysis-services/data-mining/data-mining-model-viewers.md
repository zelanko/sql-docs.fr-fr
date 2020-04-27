---
title: Visionneuses de modèles d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- displaying data mining models
- mining models [Analysis Services], viewing
- data mining [Analysis Services], models
- viewing data mining models
- mining model content
- support [data mining]
- exploring data mining models [Analysis Services]
ms.assetid: 14c8e656-f63c-4e8a-a3af-1d580e823d28
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 659b8c0afd91a60389a2cacf9a3063ff65164dd1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66085044"
---
# <a name="data-mining-model-viewers"></a>Visionneuses de modèle d’exploration de données
  Après l’apprentissage d’un modèle d’exploration [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]de données dans, vous pouvez explorer le modèle pour rechercher des tendances intéressantes. Étant donné que les résultats des modèles d'exploration de données sont complexes et peuvent être difficiles à comprendre dans un format brut, l'examen visuel des données constitue souvent le moyen le plus simple pour comprendre les règles et les relations que les algorithmes découvrent au sein des données.  
  
 Chacun des algorithmes que vous utilisez pour la construction d'un modèle renvoie un type différent de résultats. Par conséquent, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fournit une visionneuse spécifique pour chaque algorithme. Quand vous explorez un modèle d’exploration de données dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], le modèle s’affiche sous l’onglet **Visionneuse de modèle d’exploration de données** du Concepteur d’exploration de données, à l’aide de la visionneuse appropriée pour ce modèle.  
  
## <a name="how-to-use-the-model-viewers"></a>Utilisation des visionneuses de modèle  
 Vous devez sélectionner le modèle d'exploration de données, puis sélectionner une visionneuse. Chaque modèle comporte toujours deux visionneuses disponibles : une visionneuse personnalisée, qui peut inclure plusieurs onglets, et la visionneuse générique.  
  
 Selon le type du modèle sélectionné, vous verrez des options très différentes pour l'exploration du modèle. Les visionneuses personnalisées associées à chaque type de modèle sont adaptées à l'algorithme que vous avez utilisé pour créer le modèle d'exploration de données sélectionné. Chaque visionneuse personnalisée comporte divers outils et boîtes de dialogue qui vous permettent d'explorer les statistiques et modèles, de consulter les graphiques, d'utiliser en mode interactif des seuils de probabilité ou de filtrer des éléments par nom.  
  
 Le diagramme suivant illustre la différence entre une visionneuse personnalisée et la visionneuse générique pour le même modèle.  
  
1.  Tout d'abord, vous pouvez voir la visionneuse personnalisée qui apparaît lorsque vous sélectionnez un modèle d'exploration de données basé sur l'algorithme MTS (Microsoft Time Series).  
  
     Cette visionneuse personnalisée particulière crée automatiquement un graphique de la série chronologique et fournit cinq prédictions.  
  
2.  Ensuite, vous pouvez voir le même modèle, affiché à l’aide de la **Visionneuse de l’arborescence de contenu générique Microsoft**.  
  
     À gauche, la visionneuse générique affiche une liste des nœuds du modèle. Vous pouvez cliquer sur un nœud pour afficher son contenu dans le volet droit.  
  
 ![Vue d'ensemble d'un concepteur de modèle d'exploration de données](../media/generic-mining-model-tab1.gif "Vue d'ensemble d'un concepteur de modèle d'exploration de données")  
  
## <a name="more-about-the-microsoft-generic-content-tree-viewer"></a>En savoir plus sur la visionneuse de l'arborescence de contenu générique Microsoft  
 Chaque modèle peut également être affiché à l’aide de la [Visionneuse de l’arborescence de contenu générique Microsoft &#40;exploration de données&#41;](../microsoft-generic-content-tree-viewer-data-mining.md). Cette visionneuse affiche le contenu du modèle d'exploration de données en respectant un format de table HTML standard. Toutefois, la disposition des nœuds et le contenu de chaque nœud diffèrent considérablement selon l'algorithme utilisé pour générer les résultats.  
  
 Alors que les visionneuses personnalisées sont conçues pour explorer et comprendre le modèle, la visionneuse générique est plus adaptée lorsque vous comprenez déjà le modèle et souhaitez extraire d'un nœud spécifique des statistiques ou des règles. Par exemple, vous pouvez utiliser la visionneuse générique quand vous voulez afficher des informations détaillées sur les modèles et les statistiques capturés par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pendant l’analyse, notamment la probabilité d’un nœud, ou une formule de régression.  
  
 Vous pouvez également écrire des *requêtes de contenu* à l’aide de DMX pour obtenir toutes les informations présentées dans cette visionneuse. Pour plus d’informations, consultez [Requêtes de contenu &#40;Exploration de données&#41;](content-queries-data-mining.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 Les rubriques suivantes décrivent plus en détail chacune des visionneuses, et expliquent comment interpréter les informations qu'elles contiennent.  
  
 [Explorer un modèle à l'aide de la visionneuse d'arborescences Microsoft](browse-a-model-using-the-microsoft-tree-viewer.md)  
 Décrit la Visionneuse d'arborescences [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Cette visionneuse affiche les modèles d'exploration de données qui sont générés avec l'algorithme MDT ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees) et l'algorithme MLR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression).  
  
 [Explorer un modèle à l’aide de Microsoft Sequence Cluster](browse-a-model-using-the-microsoft-cluster-viewer.md)  
 Décrit le composant [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer. Cette visionneuse affiche les modèles d’exploration de données qui sont générés avec l’algorithme MC ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering).  
  
 [Explorer un modèle à l'aide de la visionneuse de l'algorithme MTS (Microsoft Time Series)](browse-a-model-using-the-microsoft-time-series-viewer.md)  
 Décrit la Visionneuse de l’algorithme MTS ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series). Cette visionneuse affiche les modèles d’exploration de données qui sont générés avec l’algorithme MTS ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series).  
  
 [Explorer un modèle à l'aide de la visionneuse de l'algorithme MNB (Microsoft Naive Bayes)](browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
 Décrit la Visionneuse de l’algorithme MNB ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes). Cette visionneuse affiche les modèles d'exploration de données qui sont générés avec l'algorithme MNB ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes).  
  
 [Explorer un modèle à l'aide de la visionneuse de l'algorithme MSC (Microsoft Sequence Cluster)](browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
 Décrit la Visionneuse de l'algorithme MSC ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering). Cette visionneuse affiche les modèles d’exploration de données qui sont générés avec l’algorithme MSC ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering).  
  
 [Explorer un modèle à l'aide de la visionneuse de l'algorithme MAR (Microsoft Association Rules)](browse-a-model-using-the-microsoft-association-rules-viewer.md)  
 Décrit la Visionneuse de l’algorithme MAR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules). Cette visionneuse affiche les modèles d'exploration de données qui sont générés avec l'algorithme MAR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules).  
  
 [Explorer un modèle à l'aide de la visionneuse de l'algorithme MNN (Microsoft Neural Network)](browse-a-model-using-the-microsoft-neural-network-viewer.md)  
 Décrit la Visionneuse de l'algorithme MNN ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network). Cette visionneuse affiche les modèles d'exploration de données qui sont générés avec l'algorithme MNN ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network), y compris les modèles qui utilisent l'algorithme MLR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression).  
  
 [Explorer un modèle à l'aide de la visionneuse de l'arborescence de contenu générique Microsoft](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)  
 Décrit les informations détaillées qui sont disponibles dans la visionneuse générique pour tous les modèles d'exploration de données et fournit des exemples sur l'interprétation des informations pour chaque algorithme.  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services d’exploration de données&#41;](data-mining-algorithms-analysis-services-data-mining.md)   
 [Concepteur d’exploration de données](data-mining-designer.md)  
  
  

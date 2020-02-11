---
title: Afficher la formule d’un modèle de série chronologique (exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- ARTXP
- time series algorithms [Analysis Services]
- ARIMA
- time series [Analysis Services]
- Time Series Viewer [Analysis Services]
ms.assetid: 825ef719-2f44-4979-be01-5a81f54e1a53
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 43382b5dd8a20de1454bfc3d6a16aa68c99e34a5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66082597"
---
# <a name="view-the-formula-for-a-time-series-model-data-mining"></a>Afficher la formule d'un modèle de série chronologique (exploration de données)
  Le [!INCLUDE[msCoName](../../includes/msconame-md.md)] concepteur d’exploration de données de la visionneuse de série chronologique fournit le moyen le plus simple d’afficher les détails de l’équation de régression utilisée dans un modèle de série chronologique.  
  
 Vous pouvez extraire la formule de régression d'un modèle de série chronologique en interrogeant le contenu du modèle. Toutefois, pour afficher la formule complète ARTXP ou ARIMA, nous vous recommandons d’utiliser la **légende d’exploration de données** de la [visionneuse MTS (Microsoft Time Series](browse-a-model-using-the-microsoft-time-series-viewer.md)), qui présente toutes les constantes dans un format lisible.  
  
 Si vous créez un modèle mixte, les analyses ARIMA et ARTXP sont créées dans des arborescences séparées, jointes au nœud racine qui représente le modèle. Les structures des arbres ARIMA et ARTXP sont très différentes. Par exemple, l'arbre ARTXP est en fait une arborescence, comme un arbre de décision, alors que l'arbre ARIMA représente une série de moyennes mobiles. Par conséquent, bien que les deux représentations soient présentées dans un seul modèle pour des raisons de commodité, elles doivent être considérées comme deux modèles indépendants. Les équations sont également complètement différentes et ne peuvent pas être associées ou comparées.  
  
 Vous pouvez également afficher des modèles de série chronologique à l’aide de la [visionneuse de l’arborescence de contenu générique Microsoft](../microsoft-generic-content-tree-viewer-data-mining.md). Pour plus d’informations sur le contenu d’un modèle de série chronologique, consultez [contenu du modèle d’exploration de données pour les modèles de série chronologique &#40;Analysis Services d’exploration de données&#41;](mining-model-content-for-time-series-models-analysis-services-data-mining.md).  
  
### <a name="to-view-the-artxp-regression-formula-for-a-time-series-model"></a>Pour consulter la formule de régression ARTXP d'un modèle de série chronologique  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], sélectionnez le modèle de série chronologique à afficher, puis cliquez sur **Parcourir**.  
  
     \- ou -  
  
     Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], sélectionnez le modèle de série chronologique, puis cliquez sur l’onglet **Visionneuse de modèle d’exploration de données** .  
  
2.  Cliquez sur l’onglet **Modéliser** .  
  
3.  Si le modèle contient plusieurs arborescences, sélectionnez une arborescence unique dans la liste déroulante **Arborescence** .  
  
    > [!NOTE]  
    >  Un modèle aura toujours plusieurs arborescences si vous avez plusieurs séries de données. Toutefois, vous ne verrez pas autant d’arborescences dans la **visionneuse de l’algorithme MTS** que dans la [Visionneuse de l’arborescence de contenu générique Microsoft](../microsoft-generic-content-tree-viewer-data-mining.md). Cela s'explique par le fait que la visionneuse de l'algorithme MTS associe les informations ARIMA et ARTXP de chaque série de données dans une représentation unique.  
  
4.  Cliquez sur n'importe quel nœud terminal de l'arborescence.  
  
     Les nœuds étiquetés comme **Série de données** sont toujours des nœuds terminaux et peuvent contenir une équation. Si un nœud **(Tout)** n’a pas de nœuds enfants, il peut également contenir une équation.  
  
5.  Si la **Légende d’exploration de données** n’est pas disponible, cliquez avec le bouton droit sur le nœud, puis sélectionnez **Afficher la légende**.  
  
     La formule ARTXP est affichée dans la première moitié de la **Légende d’exploration de données**, comme **l’équation du nœud d’arbre**.  
  
### <a name="to-view-the-arima-formula-for-a-time-series-model"></a>Pour consulter la formule ARIMA d'un modèle de série chronologique  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], sélectionnez le modèle de série chronologique à afficher, puis cliquez sur **Parcourir**.  
  
     \- ou -  
  
     Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], sélectionnez le modèle de série chronologique, puis cliquez sur l’onglet **Visionneuse de modèle d’exploration de données** .  
  
2.  Cliquez sur l’onglet **Modéliser** .  
  
3.  Si le modèle contient plusieurs arborescences, sélectionnez une arborescence unique dans la liste déroulante **Arborescence** .  
  
    > [!NOTE]  
    >  Le modèle aura toujours plusieurs arborescences si vous incluez plusieurs séries de données.  
  
4.  Cliquez sur n'importe quel nœud de l'arborescence.  
  
     La formule ARIMA est affichée dans la seconde moitié de la **Légende d’exploration de données**, comme **Équation ARIMA**.  
  
5.  Si la **Légende d’exploration de données** n’est pas disponible, cliquez avec le bouton droit sur le nœud, puis sélectionnez **Afficher la légende**.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de la visionneuse de modèle d’exploration de données et procédures](mining-model-viewer-tasks-and-how-tos.md)   
 [Parcourir un modèle à l’aide de la visionneuse MTS (Microsoft Time Series)](browse-a-model-using-the-microsoft-time-series-viewer.md)   
 [Time Series Model Query Examples](time-series-model-query-examples.md)  
  
  

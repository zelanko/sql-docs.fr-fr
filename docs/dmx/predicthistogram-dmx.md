---
title: PredictHistogram (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f7e7129985eac09d741ea9d00c551a9507ee92c9
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37985358"
---
# <a name="predicthistogram-dmx"></a>PredictHistogram (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne une table qui représente un histogramme de la prévision d'une colonne donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
PredictHistogram(<scalar column reference> | <cluster column reference>)  
```  
  
## <a name="applies-to"></a>S'applique à  
 Référence de colonne scalaire ou référence de colonne de cluster. Peut être utilisée avec tous les types d'algorithmes, à l'exception de l'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Association.  
  
## <a name="return-type"></a>Type de retour  
 Table.  
  
## <a name="remarks"></a>Notes  
 Un histogramme génère des colonnes statistiques. La structure de colonne de l’histogramme retourné dépend du type de référence de colonne qui est utilisé avec le **PredictHistogram** (fonction).  
  
## <a name="scalar-columns"></a>Colonnes scalaires  
 Pour un \<référence de colonne scalaire >, l’histogramme qui le **PredictHistogram** retours de fonction se compose des colonnes suivantes :  
  
-   La valeur actuellement en cours de prévision  
  
-   **$Support**  
  
-   **$Probability**  
  
-   **$ProbabilityVariance**  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithmes d’exploration de données ne gèrent pas **$ProbabilityVariance**. Cette colonne contient toujours 0 pour les algorithmes [!INCLUDE[msCoName](../includes/msconame-md.md)].  
  
-   **$ProbabilityStdev**  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithmes d’exploration de données ne gèrent pas **$ProbabilityStdev**. Cette colonne contient toujours 0 pour les algorithmes [!INCLUDE[msCoName](../includes/msconame-md.md)].  
  
-   **$AdjustedProbability**  
  
     Le **$AdjustedProbability** colonne est un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] extension pour le [!INCLUDE[msCoName](../includes/msconame-md.md)] OLE DB pour la spécification d’exploration de données.  
  
## <a name="cluster-columns"></a>Colonnes de cluster  
 L’histogramme qui le **PredictHistogram** fonction retourne pour un \<référence de colonne de cluster > se compose des colonnes suivantes :  
  
-   **$Cluster** (représente le nom du cluster)  
  
-   **$Distance**  
  
-   **$Probability**  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne l'état prévisible de la colonne Bike Buyer (Acheteur de bicyclette) dans une requête singleton. La requête retourne également les États les plus probables de l’attribut Bike Buyer, selon la probabilité ajustée obtenue à l’aide de deux premiers le **PredictHistogram** (fonction).  
  
```  
SELECT  
  [TM Decision Tree].[Bike Buyer],  
  TopCount(PredictHistogram([Bike Buyer]),$AdjustedProbability,3)  
From  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Cluster &#40;DMX&#41;](../dmx/cluster-dmx.md)   
 [ClusterProbability &#40;DMX&#41;](../dmx/clusterprobability-dmx.md)   
 [PredictAdjustedProbability &#40;DMX&#41;](../dmx/predictadjustedprobability-dmx.md)   
 [PredictProbability &#40;DMX&#41;](../dmx/predictprobability-dmx.md)   
 [PredictStdev &#40;DMX&#41;](../dmx/predictstdev-dmx.md)   
 [PredictSupport &#40;DMX&#41;](../dmx/predictsupport-dmx.md)   
 [PredictVariance &#40;DMX&#41;](../dmx/predictvariance-dmx.md)   
 [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Data Mining Extensions &#40;DMX&#41; référence de fonction](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Fonctions &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

---
title: Cluster (DMX) | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Cluster
dev_langs:
- DMX
helpviewer_keywords:
- Cluster function
ms.assetid: 14b2942a-6dec-4dfa-98a6-697a3c89036a
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: cec73e5b3c182073cfad14c3605183fe72732d72
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="cluster-dmx"></a>Cluster (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne le cluster qui est le plus susceptible de contenir le cas d'entrée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Cluster()  
```  
  
## <a name="applies-to"></a>S'applique à  
 Cette fonction ne peut être utilisée que si le modèle d'exploration de données sous-jacent prend en charge le clustering.  
  
## <a name="return-type"></a>Type de retour  
 Le **Cluster** fonction ne nécessite pas de paramètres.  
  
 Le **Cluster** fonction retourne une valeur scalaire d’un nom de cluster. Toutefois, si vous utilisez cette fonction en tant qu’argument d’une autre fonction, vous devez la considérer comme un \<référence de colonne de cluster >.  
  
## <a name="remarks"></a>Notes   
 **Cluster** peut également être utilisé comme un `<`référence de colonne de cluster`>` pour un **PredictHistogram** (fonction).  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant utilise une requête singleton avec les [PredictHistogram &#40; DMX &#41;](../dmx/predicthistogram-dmx.md) et fonctions pour retourner la distance séparant le cas individuel à partir de chaque cluster du modèle d’exploration de données TM Clustering et de la probabilité que le cas individuel existe dans chaque cluster du Cluster.  
  
```  
SELECT  
  PredictHistogram(Cluster())  
FROM  
  [TM Clustering]  
  NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ClusterProbability &#40; DMX &#41;](../dmx/clusterprobability-dmx.md)   
 [Les Extensions d’exploration de données &#40; DMX &#41; Référence de fonction](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Fonctions &#40; DMX &#41;](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

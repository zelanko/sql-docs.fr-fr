---
title: ClusterProbability (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9beac713ec9a8b5a549602809d3612e4e29e67c6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68071954"
---
# <a name="clusterprobability-dmx"></a>ClusterProbability (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne la probabilité que le cas d'entrée appartient au cluster spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ClusterProbability([<Node_Caption>])  
```  
  
## <a name="applies-to"></a>S'applique à  
 Cette fonction ne peut être utilisée que si le modèle d'exploration de données sous-jacent prend en charge le clustering.  
  
## <a name="return-type"></a>Type de retour  
 Une valeur scalaire.  
  
## <a name="remarks"></a>Notes  
 La syntaxe suivante utilise l'ensemble de lignes du schéma Content du modèle d'exploration de données pour retourner les légendes de nœud existant au sein du modèle.  
  
```  
SELECT NODE_CAPTION FROM <model>.CONTENT  
```  
  
 Pour plus d’informations sur l’utilisation de cette syntaxe, consultez [SELECT FROM &#60;modèle&#62;. CONTENU &#40;DMX&#41;](../dmx/select-from-model-content-dmx.md). Pour plus d’informations sur l’ensemble de lignes du schéma de contenu du modèle d’exploration de données, consultez [de lignes DMSCHEMA_MINING_MODEL_CONTENT](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset).  
  
 Si un \<légende du nœud > n’est pas spécifié, la fonction retourne la probabilité que les cas d’entrée appartiennent au cluster plus probable. Utilisez le **Cluster** fonction pour retourner le cluster le plus probable.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne la probabilité que le cas spécifié existe dans le cluster nommé Cluster 2.  
  
```  
SELECT  
  ClusterProbability('Cluster 2')  
From  
  [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Cluster &#40;DMX&#41;](../dmx/cluster-dmx.md)   
 [Data Mining Extensions &#40;DMX&#41; référence de fonction](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Functions &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Fonctions de prédiction générales &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

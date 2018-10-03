---
title: Élément AlgorithmParameters (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AlgorithmParameters Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AlgorithmParameters
helpviewer_keywords:
- AlgorithmParameters element
ms.assetid: 240cbb60-7fa3-46ef-b5be-cd14c9ec10de
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c15cfd9be773af74c195860f7b0b16989b8c4355
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048889"
---
# <a name="algorithmparameters-element-assl"></a>Élément AlgorithmParameters (ASSL)
  Contient la collection de paramètres pour l’algorithme utilisé par un [MiningModel](../objects/miningmodel-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MiningModel>  
   ...  
   <AlgorithmParameters>  
      <AlgorithmParameter>...</AlgorithmParameter>  
   </AlgorithmParameters>  
   ...  
</MiningModel>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucun (collection)|  
|Valeur par défaut|Aucun (collection)|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[MiningModel](../objects/miningmodel-element-assl.md)|  
|Éléments enfants|[AlgorithmParameter](../objects/algorithmparameter-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 La collection `AlgorithmParameters` contient un jeu extensible de paramètres représentés sous forme de paires nom/valeur pour un algorithme de modèle d'exploration de données. Le jeu de paramètres applicables dépend de l'algorithme. Pour plus d'informations sur les paramètres d'un algorithme spécifique, consultez la documentation relative à ce dernier.  
  
 Les paramètres d'algorithme disponibles, notamment les informations de validation et d'affichage, peuvent être récupérés de l'ensemble de lignes de schéma DMSCHEMA_MINING_SERVICE_PARAMETERS.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.AlgorithmParameterCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Algorithm &#40;ASSL&#41;](../properties/algorithm-element-assl.md)   
 [Ensemble de lignes DMSCHEMA_MINING_SERVICE_PARAMETERS](../../schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md)   
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  

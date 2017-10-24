---
title: "Élément AlgorithmParameters (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- AlgorithmParameters Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AlgorithmParameters
helpviewer_keywords:
- AlgorithmParameters element
ms.assetid: 240cbb60-7fa3-46ef-b5be-cd14c9ec10de
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4865e23f02c681586f9025737dd2acc21ccd93bf
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="algorithmparameters-element-assl"></a>Élément AlgorithmParameters (ASSL)
  Contient la collection de paramètres pour l’algorithme utilisé par un [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) élément.  
  
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
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)|  
|Éléments enfants|[AlgorithmParameter](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 La collection **AlgorithmParameters** contient un jeu extensible de paramètres représentés sous forme de paires nom/valeur pour un algorithme de modèle d'exploration de données. Le jeu de paramètres applicables dépend de l'algorithme. Pour plus d'informations sur les paramètres d'un algorithme spécifique, consultez la documentation relative à ce dernier.  
  
 Les paramètres d'algorithme disponibles, notamment les informations de validation et d'affichage, peuvent être récupérés de l'ensemble de lignes de schéma DMSCHEMA_MINING_SERVICE_PARAMETERS.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.AlgorithmParameterCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Algorithm &#40; ASSL &#41;](../../../analysis-services/scripting/properties/algorithm-element-assl.md)   
 [Ensemble de lignes DMSCHEMA_MINING_SERVICE_PARAMETERS](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md)   
 [Collections de &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  


---
title: "Élément AlgorithmParameter (ASSL) | Documents Microsoft"
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
- AlgorithmParameter Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AlgorithmParameter
helpviewer_keywords:
- AlgorithmParameter element
ms.assetid: 73211495-065c-43c6-a486-be6044617263
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 33ef60da325d605250b5a429bc3fac14e8da01d7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="algorithmparameter-element-assl"></a>Élément AlgorithmParameter (ASSL)
  Définit un paramètre pour l’algorithme utilisé par un [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AlgorithmParameters>  
   <AlgorithmParameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </AlgorithmParameter>  
</AlgorithmParameters>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[AlgorithmParameters](../../../analysis-services/scripting/collections/algorithmparameters-element-assl.md)|  
|Éléments enfants|[Nom](../../../analysis-services/scripting/properties/name-element-assl.md), [Valeur](../../../analysis-services/scripting/properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Un **AlgorithmParameter** est un paramètre destiné à un algorithme de modèle d'exploration de données. **AlgorithmParameter** représente ce paramètre sous la forme d'une paire nom/valeur. Le jeu de paramètres applicables qu'un **AlgorithmParameter** peut représenter dépend d'un algorithme. Pour plus d'informations sur les paramètres d'un algorithme spécifique, consultez la documentation relative à ce dernier.  
  
 Paramètres d’algorithme disponibles, y compris les informations de validation et d’affichage peuvent être récupérés à partir de la [DMSCHEMA_MINING_SERVICE_PARAMETERS](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md) de lignes du schéma.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.AlgorithmParameter>.  
  
## <a name="see-also"></a>Voir aussi  
 [MiningModel, élément &#40; ASSL &#41;](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)   
 [Élément Algorithm &#40; ASSL &#41;](../../../analysis-services/scripting/properties/algorithm-element-assl.md)   
 [Objets &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  


---
title: Élément KeyColumns (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- KeyColumns Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- KeyColumns
helpviewer_keywords:
- KeyColumns element
ms.assetid: 03f3ad21-25cb-4afd-9287-cbf942ac1ad9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a5c699f95d91cdb48d780875d8f9190114d4b7a5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48152631"
---
# <a name="keycolumns-element-assl"></a>Élément KeyColumns (ASSL)
  Contient la collection de [KeyColumn](../objects/column-element-assl.md) définitions d’éléments pour un objet parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DimensionAttribute> <!-- or AggregationInstanceAttribute, AggregationInstanceCubeDimension, MeasureGroupAttribute, ScalarMiningStructureColumn -->  
   ...  
   <KeyColumns>  
      <KeyColumn xsi:type="DataItem"...</KeyColumn>  
   </KeyColumns>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|1-n : élément requis pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[AggregationInstanceAttribute](../data-type/aggregationinstanceattribute-data-type-assl.md), [AggregationInstanceCubeDimension](../data-type/dimension-data-type-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [MeasureGroupAttribute](../data-type/measuregroupattribute-data-type-assl.md), [ ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|Éléments enfants|[KeyColumn](../objects/column-element-assl.md) de type [DataItem](../data-type/dataitem-data-type-assl.md)|  
  
## <a name="remarks"></a>Notes  
 La collection `KeyColumns` peut contenir plusieurs éléments `KeyColumn` qui représentent une clé en plusieurs parties pour une colonne d'attribut ou de structure d'exploration de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  

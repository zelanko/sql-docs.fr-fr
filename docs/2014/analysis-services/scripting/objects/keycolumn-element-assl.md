---
title: Élément KeyColumn (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- KeyColumn Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- KeyColumn
helpviewer_keywords:
- KeyColumn element
ms.assetid: 7b03eeb3-d478-4c38-822e-8cdfcc485039
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 7594a92eb8c2eb4cdb423c7298bc3929dc49dc32
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042994"
---
# <a name="keycolumn-element-assl"></a>Élément KeyColumn (ASSL)
  Contient la définition d'une colonne qui est la clé d'un attribut ou en fait partie.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<KeyColumns>  
   <KeyColumn xsi:type="DataItem">...</KeyColumn>  
<KeyColumns>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Valeur par défaut|None|  
|Cardinalité|1-n : élément requis pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[KeyColumns](../collections/columns-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la `DataItem` type, y compris un tableau d’objets d’Analysis Services Scripting Language (ASSL) et les propriétés de la `DataItem` de type, consultez [Type de données DataItem &#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md).  
  
 Les éléments qui correspondent aux parents de la collection `KeyColumns` dans le modèle objet AMO (Analysis Management Objects) sont <xref:Microsoft.AnalysisServices.AggregationInstanceAttribute>, <xref:Microsoft.AnalysisServices.DimensionAttribute>, <xref:Microsoft.AnalysisServices.MeasureGroupAttribute> et <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données AggregationInstanceAttribute &#40;ASSL&#41;](../data-type/aggregationinstanceattribute-data-type-assl.md)   
 [Type de données AggregationInstanceCubeDimension &#40;ASSL&#41;](../data-type/dimension-data-type-assl.md)   
 [Type de données DimensionAttribute &#40;ASSL&#41;](../data-type/dimensionattribute-data-type-assl.md)   
 [Type de données MeasureGroupAttribute &#40;ASSL&#41;](../data-type/measuregroupattribute-data-type-assl.md)   
 [Type de données ScalarMiningStructureColumn &#40;ASSL&#41;](../data-type/miningstructurecolumn-data-type-assl.md)   
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  
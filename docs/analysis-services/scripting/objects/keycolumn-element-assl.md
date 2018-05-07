---
title: Élément KeyColumn (ASSL) | Documents Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e22b3b5872ce75f7b93ce334df2d4214df176eb0
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="keycolumn-element-assl"></a>Élément KeyColumn (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|Type de données et longueur|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-n : élément requis pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la **DataItem** type, y compris un tableau d’objets d’Analysis Services Scripting Language (ASSL) et les propriétés de la **DataItem** de type, consultez [Type de données DataItem & #40 ; ASSL & #41 ; ](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
 Les éléments qui correspondent aux parents de la **KeyColumns** collection dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.AggregationInstanceAttribute>, <xref:Microsoft.AnalysisServices.DimensionAttribute>, <xref:Microsoft.AnalysisServices.MeasureGroupAttribute>, et <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données AggregationInstanceAttribute &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/aggregationinstanceattribute-data-type-assl.md)   
 [Type de données AggregationInstanceCubeDimension &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/aggregationinstancecubedimension-data-type-assl.md)   
 [Type de données DimensionAttribute &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)   
 [Type de données MeasureGroupAttribute &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/measuregroupattribute-data-type-assl.md)   
 [Type de données ScalarMiningStructureColumn &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)   
 [Objets & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  

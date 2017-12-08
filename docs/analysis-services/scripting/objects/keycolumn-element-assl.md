---
title: "Élément KeyColumn (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: KeyColumn Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: KeyColumn
helpviewer_keywords: KeyColumn element
ms.assetid: 7b03eeb3-d478-4c38-822e-8cdfcc485039
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 87333935a62f8aa056278ec50f01f8a45a968b91
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
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
|Type de données et longueur|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-n : élément requis pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la **DataItem** type, y compris un tableau d’objets d’Analysis Services Scripting Language (ASSL) et les propriétés de la **DataItem** de type, consultez [Type de données DataItem &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
 Les éléments qui correspondent aux parents de la **KeyColumns** collection dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.AggregationInstanceAttribute>, <xref:Microsoft.AnalysisServices.DimensionAttribute>, <xref:Microsoft.AnalysisServices.MeasureGroupAttribute>, et <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données AggregationInstanceAttribute &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/aggregationinstanceattribute-data-type-assl.md)   
 [Type de données AggregationInstanceCubeDimension &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/aggregationinstancecubedimension-data-type-assl.md)   
 [Type de données DimensionAttribute &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)   
 [Type de données MeasureGroupAttribute &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/measuregroupattribute-data-type-assl.md)   
 [Type de données ScalarMiningStructureColumn &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)   
 [Objets &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  

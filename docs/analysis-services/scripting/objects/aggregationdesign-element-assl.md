---
title: "Élément AggregationDesign (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
apiname: AggregationDesign Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: AggregationDesign
helpviewer_keywords: AggregationDesign element
ms.assetid: 80ad98d8-73a8-4353-b5ad-d2a9ac3bc531
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 81d1fbd4f314b713e0177af58ef27b3caed4f28a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="aggregationdesign-element-assl"></a>Élément AggregationDesign (ASSL)
  Définit un ensemble de définitions d'agrégation qu'il est possible de partager sur plusieurs partitions dans une base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AggregationDesigns>  
   <AggregationDesign>  
      <ID>...</ID>  
      <Name>...</Name>  
            <Description>...</Description>  
      <EstimatedRows>...</EstimatedRows>  
      <Dimensions>...</Dimensions>  
            <Aggregations>...</Aggregation>  
      <EstimatedPerformanceGain>...</EstimatedPerformanceGain>  
      <Annotations>...</Annotations>  
   </AggregationDesign>  
</AggregationDesigns>  
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
|Éléments parents|[AggregationDesigns](../../../analysis-services/scripting/collections/aggregationdesigns-element-assl.md)|  
|Éléments enfants|[Agrégations](../../../analysis-services/scripting/collections/aggregations-element-assl.md), [Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md), [Description](../../../analysis-services/scripting/properties/description-element-assl.md), [Dimensions](../../../analysis-services/scripting/collections/dimensions-element-assl.md), [EstimatedPerformanceGain](../../../analysis-services/scripting/properties/estimatedperformancegain-element-assl.md), [EstimatedRows](../../../analysis-services/scripting/properties/estimatedrows-element-assl.md), [ID](../../../analysis-services/scripting/properties/id-element-assl.md), [nom](../../../analysis-services/scripting/properties/name-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.AggregationDesign>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément partition &#40; ASSL &#41;](../../../analysis-services/scripting/objects/partition-element-assl.md)   
 [Élément Aggregation &#40; ASSL &#41;](../../../analysis-services/scripting/objects/aggregation-element-assl.md)   
 [Élément Aggregations &#40; ASSL &#41;](../../../analysis-services/scripting/collections/aggregations-element-assl.md)   
 [Objets &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  

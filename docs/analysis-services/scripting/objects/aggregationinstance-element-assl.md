---
title: "Élément AggregationInstance (ASSL) | Documents Microsoft"
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
apiname: AggregationInstance Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: AggregationInstance element
ms.assetid: 2e77e9e1-9f2c-4df4-9aa6-5b7b911016a3
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9627febfef1a7fba543c86dd8fdb34ed9935f48f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="aggregationinstance-element-assl"></a>Élément AggregationInstance (ASSL)
  Définit une instance d'agrégation pour une partition.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AggregationInstances>  
   <AggregationInstance>  
      <AggregationType>...</AggregationType>  
      <AggregationID>...</AggregationID>  
      <Source>...</Source>  
      <Dimensions>...</Dimensions>  
      <Measures>...</Measures>  
      <Annotations>...</Annotations>  
   </AggregationInstance>  
</AggregationInstances>  
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
|Éléments parents|[AggregationInstances](../../../analysis-services/scripting/collections/aggregationinstances-element-assl.md)|  
|Éléments enfants|[AggregationID](../../../analysis-services/scripting/properties/aggregationid-element-assl.md), [AggregationType](../../../analysis-services/scripting/properties/aggregationtype-element-assl.md), [Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md), [Dimensions](../../../analysis-services/scripting/collections/dimensions-element-assl.md), [Measures](../../../analysis-services/scripting/collections/measures-element-assl.md), [Source](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Lorsqu'un élément [Partition](../../../analysis-services/scripting/objects/partition-element-assl.md) utilise un élément [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md) pour générer des agrégations pour cette partition, chaque élément [Aggregation](../../../analysis-services/scripting/objects/aggregation-element-assl.md) dans l'élément **AggregationDesign** est instancié pour cette partition. Plusieurs partitions peuvent utiliser la même conception d'agrégation pour générer plusieurs instances d'une agrégation définie. L'élément **AggregationInstance** représente une instance d'une agrégation définie.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.AggregationInstance>.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  

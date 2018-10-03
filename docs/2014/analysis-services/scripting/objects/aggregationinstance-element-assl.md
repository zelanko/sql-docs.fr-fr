---
title: Élément AggregationInstance (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AggregationInstance Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- AggregationInstance element
ms.assetid: 2e77e9e1-9f2c-4df4-9aa6-5b7b911016a3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: aef7afde2cf93d18ad0a567f5a5e1071b7e42ebf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48177899"
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
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[AggregationInstances](../collections/aggregationinstances-element-assl.md)|  
|Éléments enfants|[AggregationID](../properties/id-element-assl.md), [AggregationType](../properties/aggregationtype-element-assl.md), [Annotations](../collections/annotations-element-assl.md), [Dimensions](../collections/dimensions-element-assl.md), [Measures](../collections/measures-element-assl.md), [Source](../properties/source-element-binding-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Quand un [Partition](partition-element-assl.md) élément utilise un [AggregationDesign](aggregationdesign-element-assl.md) élément à générer des agrégations pour cette partition, chaque [agrégation](aggregation-element-assl.md) dans le `AggregationDesign` est instancié pour cette partition. Plusieurs partitions peuvent utiliser la même conception d'agrégation pour générer plusieurs instances d'une agrégation définie. L'élément `AggregationInstance` représente une instance d'une agrégation définie.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.AggregationInstance>.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  

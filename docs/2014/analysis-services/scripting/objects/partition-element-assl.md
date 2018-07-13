---
title: Élément (ASSL) de partition | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Partition Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- PARTITION
helpviewer_keywords:
- Partition element
ms.assetid: 40020840-1bb7-478f-9017-1a30342ac4c6
caps.latest.revision: 39
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c298ec80f1bb1f17d97e36f2ce93b6efbf924508
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37209969"
---
# <a name="partition-element-assl"></a>Élément Partition (ASSL)
  Définit une partition d’un [MeasureGroup](group-element-assl.md) élément ou une liaison de partition dans une sortie de ligne [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-out-of-line-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Partitions>  
      <Partition> <!-- ancestor: MeasureGroup -->  
      <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <Description>...</Description>  
      <Source>...</Source>  
      <ProcessingPriority>...</ProcessingPriority>  
      <AggregationPrefix>...</AggregationPrefix>  
      <StorageMode>...</StorageMode>  
      <ProcessingMode>...</ProcessingMode>  
      <ErrorConfiguration>...</ErrorConfiguration>  
      <StorageLocation>...</StorageLocation>  
      <RemoteDatasourceID>...</RemoteDatasourceID>  
      <Slice>...</Slice>  
      <ProactiveCaching>...</ProactiveCaching>  
      <Type>...</Type>  
      <EstimatedSize>...</EstimatedSize>  
      <EstimatedRows>...</EstimatedRows>  
      <CurrentStorageMode>...</CurrentStorageMode>  
      <AggregationDesignID>...</AggregationDesignID>  
      <AggregationInstances>...</AggregationInstances>  
      <AggregationInstanceSource>...</AggregationInstanceSource>  
      <LastProcessed>...</LastProcessed>  
      <State>...</State>  
      <Annotations>.../Annotations>  
   </Partition>  
   <!-- or -->  
   <Partition xsi:type="PartitionBinding"> <!-- ancestor: MeasureGroupBinding -->  
   </Partition>  
</Partitions>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
|Ancêtre ou parent|Type de données|  
|------------------------|---------------|  
|[Groupe de mesures](group-element-assl.md)|None|  
|[MeasureGroupBinding](../data-type/binding-data-type-assl.md)|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Partitions](../collections/partitions-element-assl.md)|  
  
|Ancêtre ou parent|Éléments enfants|  
|------------------------|--------------------|  
|[MeasureGroup](../properties/id-element-assl.md), [AggregationInstances](../collections/aggregationinstances-element-assl.md), [AggregationInstanceSource](../properties/aggregationinstancesource-element-assl.md), [AggregationPrefix](../properties/aggregationprefix-element-assl.md), [Annotations](../collections/annotations-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [CurrentStorageMode](../properties/storagemode-element-assl.md), [Description](../properties/description-element-assl.md), [ErrorConfiguration](errorconfiguration-element-assl.md), [EstimatedRows](../properties/estimatedrows-element-assl.md), [EstimatedSize](../properties/estimatedsize-element-assl.md), [ID](../properties/id-element-assl.md), [LastProcessed](../properties/lastprocessed-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [Nom](../properties/name-element-assl.md), [ProactiveCaching](proactivecaching-element-assl.md), [ProcessingMode](../properties/processingmode-element-assl.md), [ProcessingPriority](../properties/processingpriority-element-assl.md), [ RemoteDatasourceID](../properties/datasourceid-element-assl.md), [tranche](../properties/slice-element-assl.md), [Source](../properties/source-element-binding-assl.md), [état](../properties/state-element-assl.md), [StorageLocation](../properties/storagelocation-element-assl.md), [ StorageMode](../properties/storagemode-element-assl.md), [Type](../properties/type-element-partition-assl.md)|  
|[MeasureGroupBinding](../data-type/measuregroupbinding-data-type-out-of-line-assl.md)|None|  
  
## <a name="remarks"></a>Notes  
 Cet élément a les validations suivantes sous la valeur 2 de DeploymentMode (mode de serveur tabulaire) :  
  
-   Les éléments enfants suivants ne sont pas pris en charge et ne doivent pas être utilisés :  
  
    -   [ProcessingPriority](../properties/processingpriority-element-assl.md)  
  
    -   [AggregationPrefix](../properties/aggregationprefix-element-assl.md)  
  
    -   [Emplacement de stockage](../properties/storagelocation-element-assl.md)  
  
    -   [ProcessingMode](../properties/processingmode-element-assl.md)  
  
    -   [ErrorConfiguration](errorconfiguration-element-assl.md)  
  
    -   [Emplacement de stockage](../properties/storagelocation-element-assl.md)  
  
    -   [RemoteDatasourceID](../properties/datasourceid-element-assl.md)  
  
    -   [Tranche](../properties/slice-element-assl.md)  
  
    -   [ProactiveCaching](proactivecaching-element-assl.md)  
  
    -   [Type](../properties/type-element-partition-assl.md)  
  
    -   [CurrentStorageMode](../properties/storagemode-element-assl.md)  
  
    -   [AggregationDesignID](../properties/aggregationdesignid-element-assl.md)  
  
    -   [AggregationInstances](../collections/aggregationinstances-element-assl.md)  
  
    -   [AggregationInstanceSource](../properties/aggregationinstancesource-element-assl.md)  
  
     Une erreur peut être générée si l'un des éléments précédents est utilisé.  
  
-   Le [Source](../properties/source-element-binding-assl.md) accepte uniquement les élément **requête** liaison.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  

---
title: Élément (Binding) (ASSL) source | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Source Element (Binding)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Source
helpviewer_keywords:
- Source element
ms.assetid: 1032558c-7546-4ca7-888d-8139df23cb62
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a2600803402d87e880ad479be660de98ff5d32f3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48061329"
---
# <a name="source-element-binding-assl"></a>Élément Source (Binding) (ASSL)
  Identifie la source de données à laquelle l'élément parent est lié.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AggregationInstance> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Source>...</Source>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Tableau de types de données voir ci-dessous|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
 **Type de données et longueur**  
  
|||  
|-|-|  
|Ancêtre ou parent|Type de données|  
|[AggregationInstance](../data-type/binding-data-type-assl.md)|  
|[AggregationInstanceMeasure](../data-type/columnbinding-data-type-assl.md)|  
|[Cube](../data-type/datasourceviewbinding-data-type-assl.md)|  
|[DataItem](../data-type/dataitem-data-type-assl.md)|N’importe quel type de données dérivé [liaison](../data-type/binding-data-type-assl.md), selon le parent de `DataItem`. Pour plus d'informations, consultez la section Notes.|  
|[Dimension](../data-type/dimensionbinding-data-type-assl.md), [DataSourceViewBinding](../data-type/datasourceviewbinding-data-type-assl.md), [DimensionBinding](../data-type/dimensionbinding-data-type-assl.md), [TimeBinding](../data-type/timebinding-data-type-assl.md)|  
|[DimensionAttribute](../data-type/attributebinding-data-type-assl.md), [UserDefinedGroupBinding](../data-type/userdefinedgroupbinding-data-type-assl.md)|  
|[Groupe de mesures](../data-type/measuregroupbinding-data-type-assl.md)|  
|[MeasureGroupDimension](../data-type/measuregroupdimensionbinding-data-type-assl.md)|  
|[MiningStructure](../objects/miningstructure-element-assl.md)|[CubeDimensionBinding](../data-type/cubedimensionbinding-data-type-assl.md), [DataSourceViewBinding](../data-type/datasourceviewbinding-data-type-assl.md), [DimensionBinding](../data-type/dimensionbinding-data-type-assl.md)|  
|[Partition](../data-type/tabularbinding-data-type-assl.md)|  
|[ProactiveCaching](../objects/proactivecaching-element-assl.md)|N’importe quel type de données dérivé [ProactiveCachingBinding](../data-type/proactivecachingbinding-data-type-assl.md), selon les options de traitement et de notification utilisées par le parent de la `ProactiveCaching` élément.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[AggregationInstance](../objects/aggregationinstance-element-assl.md), [AggregationInstanceMeasure](../data-type/aggregationinstancemeasure-data-type-assl.md), [Cube](../objects/cube-element-assl.md), [DataItem](../data-type/dataitem-data-type-assl.md), [Dimension](../objects/dimension-element-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [MeasureGroup](../objects/group-element-assl.md), [MeasureGroupDimension](../data-type/dimension-data-type-assl.md), [MiningStructure](../objects/miningstructure-element-assl.md), [Partition ](../objects/partition-element-assl.md), [ProactiveCaching](../objects/proactivecaching-element-assl.md).|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Dans l'élément `Source`, les types de données `Binding` dérivés autorisés dans l'élément `DataItem` dépendent du parent de l'élément `DataItem`.  
  
|Parent DataItem|Types de données autorisés|  
|---------------------|------------------------|  
|[DimensionAttribute](../data-type/attributebinding-data-type-assl.md), [ColumnBinding](../data-type/columnbinding-data-type-assl.md), [TimeAttributeBinding](../data-type/timeattributebinding-data-type-assl.md) (uniquement pour [KeyColumns](../collections/columns-element-assl.md)).|  
|[MeasureGroupAttribute](../data-type/measuregroupattribute-data-type-assl.md)|[AttributeBinding](../data-type/attributebinding-data-type-assl.md), [ColumnBinding](../data-type/columnbinding-data-type-assl.md), [InheritedBinding](../data-type/inheritedbinding-data-type-assl.md).|  
|[ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|[ColumnBinding](../data-type/columnbinding-data-type-assl.md)|  
  
 Pour plus d’informations sur la `Binding` type, y compris les tableaux des objets Analysis Services Scripting Language (ASSL) de la `Binding` type et la hiérarchie d’héritage de `Binding` types, consultez [Type de données de liaison &#40;ASSL &#41;](../data-type/binding-data-type-assl.md).  
  
 Pour plus d’informations sur les liaisons de données dans ASSL, consultez [des Sources de données et des liaisons &#40;multidimensionnels SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

---
title: Type de données (ASSL) Binding | Microsoft Docs
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
- Binding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- BINDING
helpviewer_keywords:
- Binding data type
ms.assetid: 0a777219-b885-4961-ac66-b76faeb520db
caps.latest.revision: 39
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a34209ea08d1cdfd0100bd5e2402edc0f592f066
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169540"
---
# <a name="binding-data-type-assl"></a>Type de données Binding (ASSL)
  Définit un type de données primitif abstrait qui représente une relation de dépendance entre deux objets dans laquelle les données ou les métadonnées d'un objet dépendent des données ou des métadonnées d'un objet lié.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Binding>...</Binding>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|None|  
|Types de données dérivés|[AttributeBinding](binding-data-type-assl.md), [ColumnBinding](columnbinding-data-type-assl.md), [CubeAttributeBinding](cubeattributebinding-data-type-assl.md), [CubeDimensionBinding](dimensionbinding-data-type-assl.md), [DataSourceViewBinding](datasourceviewbinding-data-type-assl.md), [DimensionBinding](dimensionbinding-data-type-assl.md), [InheritedBinding](inheritedbinding-data-type-assl.md), [MeasureBinding](measurebinding-data-type-assl.md), [MeasureGroupBinding](measuregroupbinding-data-type-assl.md), [ MeasureGroupDimensionBinding](measuregroupdimensionbinding-data-type-assl.md), [ProactiveCachingBinding](proactivecachingbinding-data-type-assl.md), [RowBinding](rowbinding-data-type-assl.md), [TabularBinding](tabularbinding-data-type-assl.md), [ TimeAttributeBinding](timeattributebinding-data-type-assl.md), [TimeBinding](timebinding-data-type-assl.md), [UserDefinedGroupBinding](userdefinedgroupbinding-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|None|  
|Éléments dérivés|None|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.Binding>.  
  
 Pour plus d’informations sur la liaison de données, consultez [des Sources de données et des liaisons &#40;multidimensionnels SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="elements-of-type-binding"></a>Éléments de type Binding  
 Le tableau suivant répertorie les éléments de type `Binding`.  
  
|Élément parent|Élément de type `Binding`|Commentaires|  
|--------------------|---------------------------------|--------------|  
|[AttributeTranslation](../properties/source-element-binding-assl.md) de [CaptionColumn](../objects/column-element-assl.md) (de type [DataItem](dataitem-data-type-assl.md))|Type de la `Binding` doit être [AttributeBinding](binding-data-type-assl.md) ou [ColumnBinding](columnbinding-data-type-assl.md)|  
|[Cube](../objects/cube-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|Type de la `Binding` doit être [DataSourceViewBinding](datasourceviewbinding-data-type-assl.md)|  
|[CubeBinding (hors ligne)](../objects/group-element-assl.md)|Type de la `Binding` doit être [MeasureGroupBinding](measuregroupbinding-data-type-assl.md)|  
|[DataItem](dataitem-data-type-assl.md)|[Source](../properties/source-element-binding-assl.md)|`Binding` peut être de n'importe quel type|  
|[Dimension](../objects/dimension-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|Type de la `Binding` doit être [CubeDimensionBinding](dimensionbinding-data-type-assl.md), [DataSourceViewBinding](datasourceviewbinding-data-type-assl.md), [DimensionBinding](dimensionbinding-data-type-assl.md), ou [TimeBinding](timebinding-data-type-assl.md)|  
|[DimensionAttribute](dimensionattribute-data-type-assl.md)|[Source](../properties/source-element-binding-assl.md)|Type de la `Binding` doit être [AttributeBinding](binding-data-type-assl.md) ou [UserDefinedGroupBinding](userdefinedgroupbinding-data-type-assl.md)|  
|[DrillThroughAction](action-data-type-assl.md)|[Colonne](../objects/column-element-assl.md)|Type de la `Binding` doit être [CubeAttributeBinding](cubeattributebinding-data-type-assl.md) ou [MeasureBinding](measurebinding-data-type-assl.md)|  
|[Mesure](../objects/measure-element-assl.md)|[Source](../properties/source-element-binding-assl.md) (de type [DataItem](dataitem-data-type-assl.md))|Type de la `Binding` doit être [ColumnBinding](columnbinding-data-type-assl.md), [CubeDimensionBinding](dimensionbinding-data-type-assl.md), [MeasureBinding](measurebinding-data-type-assl.md), ou [RowBinding](rowbinding-data-type-assl.md)|  
|[Groupe de mesures](../objects/measuregroup-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|Type de la `Binding` doit être [MeasureGroupBinding](measuregroupbinding-data-type-assl.md)|  
|[MeasureGroupAttribute](measuregroupattribute-data-type-assl.md)|[Source](../properties/source-element-binding-assl.md) de [KeyColumn](../objects/keycolumn-element-assl.md) (de type [DataItem](dataitem-data-type-assl.md))|Type de la `Binding` doit être [AttributeBinding](binding-data-type-assl.md) ou [ColumnBinding](columnbinding-data-type-assl.md), ou [InheritedBinding](inheritedbinding-data-type-assl.md)|  
|[MeasureGroupBinding (hors ligne)](measuregroupbinding-data-type-out-of-line-assl.md)|[Dimension](../objects/dimension-element-assl.md)|Type de la `Binding` doit être [MeasureGroupDimensionBinding](measuregroupdimensionbinding-data-type-assl.md)|  
|[MeasureGroupBinding (hors ligne)](measuregroupbinding-data-type-out-of-line-assl.md)|[Mesure](../objects/measure-element-assl.md)|Type de la `Binding` doit être [MeasureBinding](measurebinding-data-type-assl.md)|  
|[MeasureGroupBinding (hors ligne)](../objects/partition-element-assl.md)|Type de la `Binding` doit être [PartitionBinding](partitionbinding-data-type-assl.md)|  
|[MeasureGroupBinding (hors ligne)](measuregroupbinding-data-type-out-of-line-assl.md)|[Source](../properties/source-element-binding-assl.md)|Type de la `Binding` doit être [TableBinding](tablebinding-data-type-assl.md)|  
|[MeasureGroupDimension](dimension-data-type-assl.md)|[Source](../properties/source-element-binding-assl.md)|Type de la `Binding` doit être [MeasureGroupDimensionBinding](measuregroupdimensionbinding-data-type-assl.md)|  
|[MiningStructure](../objects/miningstructure-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|Type de la `Binding` doit être [CubeDimensionBinding](dimensionbinding-data-type-assl.md), [DataSourceViewBinding](datasourceviewbinding-data-type-assl.md), ou [DimensionBinding](dimensionbinding-data-type-assl.md)|  
|[Partition](../objects/partition-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|Type de la `Binding` doit être [TabularBinding](tabularbinding-data-type-assl.md)|  
|[ProactiveCaching](../objects/proactivecaching-element-assl.md)|[Source](../properties/source-element-binding-assl.md)|Type de la `Binding` doit être [ProactiveCachingBinding](proactivecachingbinding-data-type-assl.md)|  
|[ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md)|[Source](../properties/source-element-binding-assl.md)|Type de la `Binding` doit être [AttributeBinding](binding-data-type-assl.md), [Type de données CubeAttributeBinding &#40;ASSL&#41;](cubeattributebinding-data-type-assl.md), ou [Type de données MeasureBinding &#40;ASSL&#41;](measurebinding-data-type-assl.md)|  
|[TableMiningStructureColumn](../objects/sourcemeasuregroup-element-assl.md)|Type de la `Binding` doit être [MeasureGroupBinding](measuregroupbinding-data-type-assl.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Types Analysis Services Scripting Language XML données &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

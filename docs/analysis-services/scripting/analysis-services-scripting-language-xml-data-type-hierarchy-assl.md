---
title: Hiérarchie (ASSL) de Type de données XML de langage de script Analysis Services | Documents Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 06fa9bd245671c84b8d973ab54410d6cbef61b82
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="analysis-services-scripting-language-xml-data-type-hierarchy-assl"></a>Hiérarchie des types de données XML ASSL (Analysis Services Scripting Language)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Le tableau suivant présente la hiérarchie d'héritage des types de données dans ASSL (Analysis Services Scripting Language).  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
Action  
      DrillThroughAction  
      ReportAction  
      StandardAction  
AggregationAttribute  
AggregationDesignAttribute  
AggregationDesignDimension  
AggregationDimension  
Assembly  
      ClrAssembly  
      ComAssembly  
AttributeTranslation  
Binding  
      AttributeBinding  
      ColumnBinding  
      CubeAttributeBinding  
      CubeDimensionBinding  
      DataSourceViewBinding  
      DimensionBinding  
      InheritedBinding  
      MeasureBinding  
      MeasureGroupBinding  
      MeasureGroupDimensionBinding  
      PartitionBinding  
      ProactiveCachingBinding  
            ProactiveCachingIncrementalProcessingBinding  
            ProactiveCachingObjectNotificationBinding  
                  ProactiveCachingInheritedBinding  
                  ProactiveCachingTablesBinding  
            ProactiveCachingQueryBinding  
      RowBinding  
      TabularBinding  
            DSVTableBinding  
            QueryBinding  
            TableBinding  
      TimeAttributeBinding  
      TimeBinding  
      UserDefinedGroupBinding  
ClrAssemblyFile  
CubeAttribute  
CubeBinding (out-of-line)  
CubeDimension  
CubeDimensionPermission  
CubeHierarchy  
DataBlock  
DataItem  
DataMiningMeasureGroupDimension  
DegenerateMeasureGroupDimension  
DimensionAttribute  
EventColumn  
ManyToManyMeasureGroupDimension  
MeasureGroupAttribute  
MeasureGroupBinding (out-of-line)  
MeasureGroupDimension  
MeasureGroupHierarchy  
MiningModelColumn  
MiningModelingFlag  
MiningStructureColumn  
OlapDataSource  
Permission  
PerspectiveAction  
PerspectiveAttribute  
PerspectiveCalculation  
PerspectiveDimension  
PerspectiveHierarchy  
PerspectiveKpi  
PerspectiveMeasure  
PerspectiveMeasureGroup  
PushedDataSource  
ReferenceMeasureGroupDimension  
RegularMeasureGroupDimension  
RelationalDataSource  
ScalarMiningStructureColumn  
TableMiningStructureColumn  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services script des Types de données XML Language & #40 ; ASSL & #41 ;](../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)   
 [Analysis Services Scripting Language hiérarchie des éléments XML & #40 ; ASSL & #41 ;](../../analysis-services/scripting/analysis-services-scripting-language-xml-element-hierarchy-assl.md)   
 [Analysis Services Scripting Language &#40;ASSL de XMLA&#41;](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)  
  
  

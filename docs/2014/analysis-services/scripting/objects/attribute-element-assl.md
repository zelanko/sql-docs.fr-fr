---
title: Attribut d’élément (ASSL) | Documents Microsoft
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
- Attribute Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Attribute
helpviewer_keywords:
- Attribute element
ms.assetid: 079ec9f8-a314-4e3c-821a-b42c65cc7363
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 8a9dfd4e3db4b84df6a64e8c0fe6de80bca19ca3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043228"
---
# <a name="attribute-element-assl"></a>Élément Attribute (ASSL)
  Contient la description d'un attribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Attributes>  
   <Attribute xsi:type="AggregationAttribute">...</Attribute> <!-- ancestor: AggregationDimension -->  
   <!-- or -->  
   <Attribute xsi:type="AggregationDesignAttribute">...</Attribute> <!-- ancestor: AggregationDesignDimension -->  
   <!-- or -->  
   <Attribute xsi:type="AggregationInstanceAttribute">...</Attribute> <!-- ancestor: AggregationInstanceCubeDimension -->  
   <!-- or -->  
   <Attribute xsi:type="CubeAttribute">...</Attribute> <!--ancestor:  CubeDimension -->  
   <!-- or -->  
   <Attribute xsi:type="DimensionAttribute">...</Attribute> <!-- ancestor: Dimension -->  
   <!-- or -->  
   <Attribute xsi:type="MeasureGroupAttribute">...</Attribute> <!-- ancestor: RegularMeasureGroupDimension -->  
   <!-- or -->  
   <Attribute xsi:type="PerspectiveAttribute">...</Attribute> <!-- ancestor: PerspectiveDimension -->  
   <!-- or -->  
   <Attribute>  
      <AttributeID>...</AttributeID>  
   </Attribute> <!-- ancestor: RelationshipEnd -->  
</Attributes>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
 Valeur par défaut : Aucun  
  
 Cardinalité : 0-1 : élément facultatif qui peut se produire qu’une seule fois et une seule fois.  
  
|Ancêtre ou parent|Type de données|  
|------------------------|---------------|  
|[AggregationDesignDimension](../data-type/aggregationdesignattribute-data-type-assl.md)|  
|[AggregationDimension](../data-type/aggregationattribute-data-type-assl.md)|  
|[AggregationInstanceCubeDimension](../data-type/aggregationinstanceattribute-data-type-assl.md)|  
|[CubeDimension](../data-type/cubeattribute-data-type-assl.md)|  
|[Dimension](../data-type/dimensionattribute-data-type-assl.md)|  
|[RegularMeasureGroupDimension](../data-type/measuregroupattribute-data-type-assl.md)|  
|[PerspectiveDimension](../data-type/perspectiveattribute-data-type-assl.md)|  
|[RelationshipEnd](../data-type/relationshipend-data-type-assl.md)|\<Attribut ><br />      \<[AttributeID](../properties/id-element-assl.md)>... \</AttributeID > \< /attribut >|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Attributs](../collections/attributes-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Les éléments correspondants dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.AggregationDesignAttribute>, <xref:Microsoft.AnalysisServices.AggregationAttribute>, <xref:Microsoft.AnalysisServices.CubeAttribute>, <xref:Microsoft.AnalysisServices.DimensionAttribute>, <xref:Microsoft.AnalysisServices.MeasureGroupAttribute>, et <xref:Microsoft.AnalysisServices.PerspectiveAttribute>.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  
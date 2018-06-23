---
title: Élément MeasureGroupID (ASSL) | Documents Microsoft
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
- MeasureGroupID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MeasureGroupID
helpviewer_keywords:
- MeasureGroupID element
ms.assetid: 3b075f86-dbbc-4285-8d2d-61fa722181c7
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 7a6ab3a46de67deb375f74b30a0e802680a9d7ab
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152699"
---
# <a name="measuregroupid-element-assl"></a>Élément MeasureGroupID (ASSL)
  Associe un [MeasureGroup](../objects/group-element-assl.md) avec l’élément parent, une liaison ou une liaison hors ligne.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ManyToManyMeasureGroupDimension> <!-- or MeasureGroupAttributeBinding, MeasureGroupBinding, PerspectiveMeasureGroup -->  
   ...  
   <MeasureGroupID>...</MeasureGroupID>  
   ...  
</ManyToManyMeasureGroupDimension>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité||  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[ManyToManyMeasureGroupDimension](../data-type/dimension-data-type-assl.md), [MeasureGroupAttributeBinding](../data-type/measuregroupattributebinding-data-type-out-of-line-assl.md), [MeasureGroupBinding](../data-type/binding-data-type-assl.md), [PerspectiveMeasureGroup](../data-type/perspectivemeasuregroup-data-type-assl.md)|  
  
|Éléments enfants - ancêtre ou Parent|Cardinalité|  
|------------------------------------------|-----------------|  
|[ManyToManyMeasureGroupDimension](../data-type/dimension-data-type-assl.md)|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
|[MeasureGroupAttributeBinding](../data-type/measuregroupattributebinding-data-type-out-of-line-assl.md), [MeasureGroupBinding](../data-type/binding-data-type-assl.md) et [PerspectiveMeasureGroup](../data-type/perspectivemeasuregroup-data-type-assl.md)|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="remarks"></a>Notes  
 Les éléments qui correspondent aux parents de `MeasureGroupID` dans le modèle objet AMO (Analysis Management Objects) sont <xref:Microsoft.AnalysisServices.ManyToManyMeasureGroupDimension>, <xref:Microsoft.AnalysisServices.MeasureGroupBinding> et <xref:Microsoft.AnalysisServices.PerspectiveMeasureGroup>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
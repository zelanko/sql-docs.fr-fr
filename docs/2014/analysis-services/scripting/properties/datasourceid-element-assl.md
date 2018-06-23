---
title: Élément DataSourceID (ASSL) | Documents Microsoft
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
- DataSourceID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DataSourceID
helpviewer_keywords:
- DataSourceID element
ms.assetid: 2d71ba53-1684-4da0-8da4-fb75033c971b
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 69cdda7c02c2bea92f1fb631b955e223427f3b85
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140828"
---
# <a name="datasourceid-element-assl"></a>Élément DataSourceID (ASSL)
  Identifie la [DataSource](../objects/datasource-element-assl.md) élément associé à l’élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CubeBinding> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <DataSourceID>...</DataSourceID>  
   ...  
</CubeBinding>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|Dépend du contexte|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[CubeBinding](../data-type/cubebinding-data-type-out-of-line-assl.md), [CubeDimensionBinding](../data-type/binding-data-type-assl.md), [DimensionBinding](../data-type/dimensionbinding-data-type-assl.md), [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-assl.md), [QueryBinding](../data-type/querybinding-data-type-assl.md), [DataSourceView](../objects/datasourceview-element-assl.md), [TableBinding](../data-type/tablebinding-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Les éléments qui correspondent aux parents de `DataSourceID` dans le modèle objet AMO (Analysis Management Objects) sont <xref:Microsoft.AnalysisServices.CubeDimensionBinding>, <xref:Microsoft.AnalysisServices.DimensionBinding>, <xref:Microsoft.AnalysisServices.MeasureGroupBinding>, <xref:Microsoft.AnalysisServices.QueryBinding>, <xref:Microsoft.AnalysisServices.DataSourceView> et <xref:Microsoft.AnalysisServices.TableBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [ID d’élément &#40;ASSL&#41;](id-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
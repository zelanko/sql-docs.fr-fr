---
title: Élément Filter (Binding) (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Filter Element (Binding)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- filter
helpviewer_keywords:
- Filter element
ms.assetid: 3d4cd169-2903-4266-8541-540ece424b7b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0fe300ea7c88924fd463968cae680ded50ebb610
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48209949"
---
# <a name="filter-element-binding-assl"></a>Élément Filter (Binding) (ASSL)
  Contient une expression MDX (Multidimensional Expressions) qui filtre le contenu de l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CubeDimensionBinding> <!-- or MeasureGroupBinding -->  
   ...  
   <Filter>...</Filter>  
   ...  
</CubeDimensionBinding>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[CubeDimensionBinding](../data-type/binding-data-type-assl.md), [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la `Binding` type, y compris les tables de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] (objets ASSL Scripting Language) de la `Binding` type et la hiérarchie d’héritage de `Binding` types, consultez [Type de données de liaison &#40;ASSL &#41;](../data-type/binding-data-type-assl.md).  
  
 Pour une vue d’ensemble des liaisons de données dans ASSL, consultez [des Sources de données et des liaisons &#40;multidimensionnels SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 Les éléments qui correspondent aux parents de `Filter` dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.CubeDimensionBinding> et <xref:Microsoft.AnalysisServices.MeasureGroupBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données de liaison &#40;ASSL&#41;](../data-type/binding-data-type-assl.md)   
 [Sources de données et liaisons &#40;SSAS multidimensionnel&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

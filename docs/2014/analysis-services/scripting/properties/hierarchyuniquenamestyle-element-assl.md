---
title: Élément HierarchyUniqueNameStyle (ASSL) | Documents Microsoft
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
- HierarchyUniqueNameStyle Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- HierarchyUniqueNameStyle element
ms.assetid: 2ac57825-e9e5-4ec4-9856-fa2326d2c43f
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a4948cc104e39c6d7aec7e2822594e891c52b112
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052298"
---
# <a name="hierarchyuniquenamestyle-element-assl"></a>Élément HierarchyUniqueNameStyle (ASSL)
  Détermine comment des noms uniques sont générés pour les hiérarchies qui sont contenus dans le [CubeDimension](../data-type/dimension-data-type-assl.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CubeDimension>  
   ...  
   <HierarchyUniqueNameStyle>...</HierarchyUniqueNameStyle>  
   ...  
</CubeDimension>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*IncludeDimensionName*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[CubeDimension](../data-type/dimension-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*IncludeDimensionName*|Le nom de la dimension est inclus dans le nom de la hiérarchie.|  
|*ExcludeDimensionName*|Le nom de la dimension n'est pas inclus dans le nom de la hiérarchie.|  
  
 L’élément qui correspond au parent de `HierarchyUniqueNameStyle` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.CubeDimension>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément de cube &#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [Élément de dimension &#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
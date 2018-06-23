---
title: Élément AttributeHierarchyOptimizedState (ASSL) | Documents Microsoft
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
- AttributeHierarchyOptimizedState Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributeHierarchyOptimizedState
helpviewer_keywords:
- AttributeHierarchyOptimizedState element
ms.assetid: d87148c8-2011-45ae-94c3-851f48babc5f
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 027bd8713038fd1b090697d8891f93eaabc11f9f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038186"
---
# <a name="attributehierarchyoptimizedstate-element-assl"></a>Élément AttributeHierarchyOptimizedState (ASSL)
  Détermine le niveau d'optimisation appliqué à la hiérarchie d'attribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DimensionAttribute> <!-- or CubeAttribute -->  
   ...  
   <AttributeHierarchyOptimizedState>...  
   </AttributeHierarchyOptimizedState>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*FullyOptimized*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[CubeAttribute](../data-type/cubeattribute-data-type-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*FullyOptimized*|L'instance construit des index pour la hiérarchie d'attribut afin d'augmenter les performances des requêtes.|  
|*NotOptimized*|Aucun index supplémentaire n'est construit par l'instance.|  
  
 L'énumération qui correspond aux valeurs autorisées de l'élément `AttributeHierarchyOptimizedState` dans le modèle objet AMO (Analysis Management Objects) est <xref:Microsoft.AnalysisServices.OptimizationType>. Les éléments qui correspondent aux parents de `AttributeHierarchyOptimizedState` dans le modèle objet AMO sont <xref:Microsoft.AnalysisServices.CubeAttribute> et <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
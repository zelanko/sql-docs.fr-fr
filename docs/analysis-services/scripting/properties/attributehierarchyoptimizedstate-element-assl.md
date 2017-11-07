---
title: "Élément AttributeHierarchyOptimizedState (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- AttributeHierarchyOptimizedState Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AttributeHierarchyOptimizedState
helpviewer_keywords:
- AttributeHierarchyOptimizedState element
ms.assetid: d87148c8-2011-45ae-94c3-851f48babc5f
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 79b7f84f96c9921a0d1fafce4bc0c8604b5fd582
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

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
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[CubeAttribute](../../../analysis-services/scripting/data-type/cubeattribute-data-type-assl.md), [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*FullyOptimized*|L'instance construit des index pour la hiérarchie d'attribut afin d'augmenter les performances des requêtes.|  
|*NotOptimized*|Aucun index supplémentaire n'est construit par l'instance.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **AttributeHierarchyOptimizedState** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.OptimizationType>. Les éléments qui correspondent aux parents de **AttributeHierarchyOptimizedState** dans le modèle objet AMO sont <xref:Microsoft.AnalysisServices.CubeAttribute> et <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  


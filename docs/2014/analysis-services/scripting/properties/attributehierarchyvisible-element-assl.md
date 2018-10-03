---
title: Élément AttributeHierarchyVisible (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AttributeHierarchyVisible Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributeHierarchyVisible
helpviewer_keywords:
- AttributeHierarchyVisible element
ms.assetid: a3289a9a-dbd6-43e8-a7ca-ee8a1da92a32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ac33cb91014a32f3795b10ef822ab6c85528ac0b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48099269"
---
# <a name="attributehierarchyvisible-element-assl"></a>Élément AttributeHierarchyVisible (ASSL)
  Détermine si la hiérarchie d'attribut est visible par des applications clientes.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DimensionAttribute> <!-- or CubeAttribute or PerspectiveAttribute -->  
   ...  
   <AttributeHierarchyVisible>...</AttributeHierarchyVisible>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Booléen|  
|Valeur par défaut|`True`|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[CubeAttribute](../data-type/cubeattribute-data-type-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [PerspectiveAttribute](../data-type/perspectiveattribute-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L'élément `AttributeHierarchyVisible` détermine si la hiérarchie d'attribut associée à l'attribut est visible par les applications clientes. Si cet élément possède la valeur `False`, la hiérarchie d'attribut peut encore être utilisée pour créer des hiérarchies définies par l'utilisateur et peut être référencée par des instructions MDX (Multidimensional Expressions).  
  
 Les éléments qui correspondent aux parents de `AttributeHierarchyVisible` dans le modèle objet AMO (Analysis Management Objects) sont <xref:Microsoft.AnalysisServices.CubeAttribute>, <xref:Microsoft.AnalysisServices.DimensionAttribute> et <xref:Microsoft.AnalysisServices.PerspectiveAttribute>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément AttributeHierarchyEnabled &#40;ASSL&#41;](enabled-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

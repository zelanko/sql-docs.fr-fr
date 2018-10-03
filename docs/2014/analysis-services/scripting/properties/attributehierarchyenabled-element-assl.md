---
title: Élément AttributeHierarchyEnabled (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AttributeHierarchyEnabled Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributeHierarchyEnabled
helpviewer_keywords:
- AttributeHierarchyEnabled element
ms.assetid: 1e95307f-530e-4e98-a0e1-2b0462d330a3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: adcb11beda15b6ab4fc27357cb52134cb53b501b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48079329"
---
# <a name="attributehierarchyenabled-element-assl"></a>Élément AttributeHierarchyEnabled (ASSL)
  Détermine si une hiérarchie d'attribut est activée pour l'attribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DimensionAttribute><!-- or CubeAttribute -->  
   ...  
   <AttributeHierarchyEnabled>...</AttributeHierarchyEnabled>  
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
|Élément parent|[CubeAttribute](../data-type/cubeattribute-data-type-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Le `AttributeHierarchyEnabled` élément détermine si une hiérarchie d’attribut est générée par [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] pour l’attribut. Si la hiérarchie d'attribut n'est pas activée, l'attribut ne peut pas être utilisé dans une hiérarchie définie par l'utilisateur, et la hiérarchie d'attribut ne peut pas être référencée dans des instructions MDX (Multidimensional Expressions).  
  
 Les éléments qui correspondent aux parents de `AttributeHierarchyEnabled` dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.CubeAttribute> et <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément AttributeHierarchyVisible &#40;ASSL&#41;](visible-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

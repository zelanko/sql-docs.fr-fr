---
title: Élément DefaultMember (ASSL) | Microsoft Docs
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
- DefaultMember Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DefaultMember
helpviewer_keywords:
- DefaultMember element
ms.assetid: db4eea9f-f7cf-40de-abd0-b62014e7ec2d
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fd074ab38264bf45ad70a96c37a22bc3c3185d4a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37229679"
---
# <a name="defaultmember-element-assl"></a>Élément DefaultMember (ASSL)
  Contient une expression MDX (Multidimensional Expressions) qui identifie le membre par défaut de l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AttributePermission> <!-- or DimensionAttribute, ManyToManyMeasureGroupDimension, PerspectiveAttribute -->  
      ...  
   <DefaultMember>...</DefaultMember>  
      ...  
</AttributePermission>  
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
|Élément parent|[AttributePermission](../objects/attributepermission-element-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [ManyToManyMeasureGroupDimension](../data-type/dimension-data-type-assl.md), [PerspectiveAttribute](../data-type/perspectiveattribute-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L'élément `DefaultMember` définit le membre par défaut de l'élément parent. Si `DefaultMember` n’est pas spécifié ou est défini sur une chaîne vide, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] choisit un membre à utiliser en tant que le membre par défaut.  
  
 Pour les éléments `ManyToManyMeasureGroupDimension`, l'élément `DefaultMember` contient une expression MDX qui spécifie un membre dans la dimension identifiée dans l'élément `CubeDimensionID` de `ManyToManyMeasureGroupDimension`. L’expression MDX est semblable à la [StrToMember](/sql/mdx/strtomember-mdx) fonction MDX avec le mot clé CONSTRAINED, dans la mesure où il ne peut pas inclure de fonctions MDX ou définies par l’utilisateur.  
  
 Pour plus d’informations sur les membres par défaut, consultez [Définir un membre par défaut](../../multidimensional-models/attribute-properties-define-a-default-member.md).  
  
 Les éléments qui correspondent aux parents de `DefaultMember` dans le modèle objet AMO (Analysis Management Objects) sont <xref:Microsoft.AnalysisServices.AttributePermission>, <xref:Microsoft.AnalysisServices.DimensionAttribute> et <xref:Microsoft.AnalysisServices.PerspectiveAttribute>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

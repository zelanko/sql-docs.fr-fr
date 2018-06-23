---
title: Élément AttributePermission (ASSL) | Documents Microsoft
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
- AttributePermission Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributePermission
helpviewer_keywords:
- AttributePermission element
ms.assetid: efc8aa63-3959-4b2e-98f8-2a9c424298c2
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5ee5d846cdf849959bc1a916dd82fd95de60e6e8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051152"
---
# <a name="attributepermission-element-assl"></a>Élément AttributePermission (ASSL)
  Définit les autorisations que les membres d’un [rôle](role-element-assl.md) élément avoir sur les attributs d’une dimension individuelle dans un [Cube](cube-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AttributePermissions>  
   <AttributePermission>  
      <AttributeID>...</AttributeID>  
      <Description>...</Description>  
      <DefaultMember>...</DefaultMember>  
            <VisualTotals>...</VisualTotals>  
      <AllowedSet>...</AllowedSet>  
            <DeniedSet>...</DeniedSet>  
      <Annotations>...</Annotations>  
   </AttributePermission>  
</AttributePermissions>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[AttributePermissions](../collections/attributepermissions-element-assl.md)|  
|Éléments enfants|[AllowedSet](../properties/allowedset-element-assl.md), [Annotations](../collections/annotations-element-assl.md), [AttributeID](../properties/id-element-assl.md), [DefaultMember](member-element-assl.md), [DeniedSet](../properties/deniedset-element-assl.md), [Description ](../properties/description-element-assl.md), [VisualTotals](../properties/visualtotals-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.AttributePermission>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données CubeDimensionPermission &#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  
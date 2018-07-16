---
title: Élément AllowedSet (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- AllowedSet Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AllowedSet
helpviewer_keywords:
- AllowedSet element
ms.assetid: 4aff2e03-6e1f-4f1a-b99d-d86bba25ab9b
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 57282fc21a17c8b83c91712598781399617d3979
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37323059"
---
# <a name="allowedset-element-assl"></a>Élément AllowedSet (ASSL)
  Contient une expression d’ensemble qui définit le jeu d’autorisations permises pour un [rôle](../objects/role-element-assl.md) élément sur un attribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AttributePermission>  
      ...  
   <AllowedSet>...</AllowedSet>  
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
|Éléments parents|[AttributePermission](../objects/attributepermission-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de `AllowedSet` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.AttributePermission>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

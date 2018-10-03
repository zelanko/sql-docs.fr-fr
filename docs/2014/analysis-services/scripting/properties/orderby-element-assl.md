---
title: OrderBy, élément (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- OrderBy Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- OrderBy
helpviewer_keywords:
- OrderBy element
ms.assetid: d7a0564b-430e-44eb-913a-fe1f98917d0f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 95ed1ce8e5b9df8340b41b8ec24e713dae9739ab
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168729"
---
# <a name="orderby-element-assl"></a>Élément OrderBy (ASSL)
  Décrit comment classer les membres contenus dans l'attribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DimensionAttribute>  
   ...  
      <OrderBy>...</OrderBy>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Nom*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Nom*|Classement d'après le nom de membre.|  
|*Clé*|Classement d'après la clé de membre.|  
|*AttributeKey*|Trier par la clé de membre de l’attribut spécifié dans le [OrderByAttributeID](id-element-assl.md) élément de `DimensionAttribute`.|  
|*AttributeName*|Classement d'après le nom de membre de l'attribut spécifié dans l'élément `OrderByAttributeID` de `DimensionAttribute`.|  
  
 L’énumération qui correspond aux valeurs autorisées pour `OrderBy` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.OrderBy>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

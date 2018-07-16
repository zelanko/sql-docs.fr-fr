---
title: Allowedrowsexpression, élément (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ec24b11d-d11e-4369-a619-7e41a3c46159
caps.latest.revision: 7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7f335861084f86fa509b8c2bc3f977332d5e1da7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37291325"
---
# <a name="allowedrowsexpression-element-assl"></a>AllowedRowsExpression, élément (ASSL)
  Contient une expression DAX (Data Analysis), du type booléen, qui définit le contenu de l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CellPermission> <!-- or StandardAction -->  
   ...  
   <Expression>...</Expression>  
   ...  
</CellPermission>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[CellPermission](../objects/cellpermission-element-assl.md), [StandardAction](../data-type/action-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Pour le `CellPermission` élément, le `Expression` élément contient une expression MDX logique qui identifie les cellules applicables aux droits indiqués par le [accès](access-element-assl.md) élément de la `CellPermission` élément. Si la valeur d'un élément `Expression` pour un élément `CellPermission` est vide, l'élément `CellPermission` est ignoré.  
  
 Dans le cas de l'élément `StandardAction`, l'élément `Expression` contient une expression MDX qui représente le contenu de l'action. Si la valeur d'un élément `Expression` pour un élément `StandardAction` est vide, l'élément `StandardAction` est ignoré.  
  
 Les éléments qui correspondent aux parents dans le modèle objet AMO (Analysis Management Objects) sont <xref:Microsoft.AnalysisServices.CellPermission> et <xref:Microsoft.AnalysisServices.StandardAction>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

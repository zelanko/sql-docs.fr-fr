---
title: Members, élément (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Members Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Members
helpviewer_keywords:
- Members element
ms.assetid: 4bf585a3-b681-486d-852b-1244c5658a04
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b7d2be7834c48c5a65877ae6fd480f2a7d6ea459
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48191059"
---
# <a name="members-element-assl"></a>Élément Members (ASSL)
  Contient la collection d'éléments [Member](../objects/member-element-assl.md) de l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Group> <!-- or Role --<  
   ...  
   <Members>  
      <Member>...</Member>  
   </Members>  
   ...  
</Group>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Group](../objects/group-element-assl.md), [Role](../objects/role-element-assl.md)|  
|Éléments enfants|[Membre](../objects/member-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Les éléments qui correspondent aux parents de `Members` dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.Group> et <xref:Microsoft.AnalysisServices.Role>.  
  
## <a name="see-also"></a>Voir aussi  
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  

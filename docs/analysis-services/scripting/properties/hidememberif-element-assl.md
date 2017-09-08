---
title: "Élément HideMemberIf (ASSL) | Documents Microsoft"
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
- HideMemberIf Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- HideMemberIf
helpviewer_keywords:
- HideMemberIf element
ms.assetid: ff0e6b19-6216-43ac-ba76-1628da8c333b
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 63e9386cbeb679bef13c87857df9b95a10863099
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="hidememberif-element-assl"></a>Élément HideMemberIf (ASSL)
  Indique si et quand un membre d'un niveau doit être masqué par rapport aux applications clientes.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Level>  
   ...  
   <HideMemberIf>...</HideMemberIf>  
   ...  
</Level>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Jamais*|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Level](../../../analysis-services/scripting/objects/level-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Jamais*|Les membres ne sont jamais masqués.|  
|*OnlyChildWithNoName*|Le membre est masqué s'il est le seul enfant de son parent et si son nom est vide.|  
|*OnlyChildWithParentName*|Un membre est masqué lorsqu'il est le seul enfant de son parent et porte le même nom que ce dernier.|  
|*NoName*|Un membre est masqué lorsque son nom est vide.|  
|*ParentName*|Un membre est masqué lorsque son nom est identique à celui de son parent.|  
  
## <a name="remarks"></a>Notes  
 L’énumération qui correspond aux valeurs autorisées pour **HideMemberIf** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.HideIfValue>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

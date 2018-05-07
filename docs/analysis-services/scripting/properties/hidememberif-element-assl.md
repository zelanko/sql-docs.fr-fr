---
title: Élément HideMemberIf (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
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
manager: kfile
ms.openlocfilehash: 8633089920469efd8745805d67f3d97e20a41f2b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="hidememberif-element-assl"></a>Élément HideMemberIf (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Valeur| Description|  
|-----------|-----------------|  
|*Jamais*|Les membres ne sont jamais masqués.|  
|*OnlyChildWithNoName*|Le membre est masqué s'il est le seul enfant de son parent et si son nom est vide.|  
|*OnlyChildWithParentName*|Un membre est masqué lorsqu'il est le seul enfant de son parent et porte le même nom que ce dernier.|  
|*NoName*|Un membre est masqué lorsque son nom est vide.|  
|*ParentName*|Un membre est masqué lorsque son nom est identique à celui de son parent.|  
  
## <a name="remarks"></a>Notes  
 L’énumération qui correspond aux valeurs autorisées pour **HideMemberIf** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.HideIfValue>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

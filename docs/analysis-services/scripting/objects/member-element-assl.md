---
title: "Élément Member (ASSL) | Documents Microsoft"
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
- Member Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Member
helpviewer_keywords:
- Member element
ms.assetid: 03b4cfcb-ce87-452f-9e25-8745c0423f56
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fbb9e95ecb65dd5d065bdfa8ca30b26ddb906df2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="member-element-assl"></a>Élément Member (ASSL)
  Contient le nom d'un membre d'un élément [Group](../../../analysis-services/scripting/objects/group-element-assl.md) ou d'un élément [Role](../../../analysis-services/scripting/objects/role-element-assl.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Members>  
   <Member>  
      <Name>...</Name>  
   </Member>  
</Members>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Membres](../../../analysis-services/scripting/collections/members-element-assl.md)|  
|Éléments enfants|[Nom](../../../analysis-services/scripting/properties/name-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Les éléments qui correspondent aux parents de **membre** dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.Group> et <xref:Microsoft.AnalysisServices.Role>.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  

---
title: Élément Member (XMLA) | Documents Microsoft
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
- Member Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Member
- microsoft.xml.analysis.member
- http://schemas.microsoft.com/analysisservices/2003/engine#Member
helpviewer_keywords:
- Member element
ms.assetid: 5cc33a1f-192e-4821-a4ef-9a5f2bb7a9f0
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: f612e2cff38d71a956a9f273feba54cb8a867ffd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044278"
---
# <a name="member-element-xmla"></a>Élément Member (XMLA)
  Représente un membre unique dans un élément [Members](members-element-xmla.md) ou [Tuple](tuple-element-xmla.md) parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Members>  
   ...  
   <Member>  
      <UName>...</UName>  
      <Caption>...</Caption>  
      <LName>...</LName>  
      <LNum>...</LNum>  
      <DisplayInfo>...</DisplayInfo>  
   </Member>  
   ...  
</Members>  
<!-- or -->  
<Tuple>  
   ...  
   <Member Hierarchy="string">  
      <UName>...</UName>  
      <Caption>...</Caption>  
      <LName>...</LName>  
      <LNum>...</LNum>  
      <DisplayInfo>...</DisplayInfo>  
   </Member>  
   ...  
</Tuple>  
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
|Éléments parents|[Members](members-element-xmla.md), [Tuple](tuple-element-xmla.md)|  
|Éléments enfants|[Caption](caption-element-xmla.md), [DisplayInfo](displayinfo-element-xmla.md), [LName](name-element-xmla.md), [LNum](lnum-element-xmla.md), [UName](uname-element-xmla.md)|  
  
## <a name="attributes"></a>Attributs  
  
|Attribute|Description|  
|---------------|-----------------|  
|Hierarchy|Attribut `String` requis (pour les éléments `Tuple` parents uniquement). Nom de la hiérarchie dont font partie les membres représentés par l'élément `Member`.|  
  
## <a name="remarks"></a>Notes  
 L'élément `Member` contient les informations nécessaires pour identifier et afficher un membre dans une hiérarchie donnée. Pour les éléments `Members` parents, la hiérarchie est déjà spécifiée par l'attribut `Hierarchy` de l'élément parent. Pour les éléments `Tuple` parents, la hiérarchie est spécifiée à l'aide de l'attribut `Hierarchy` de l'élément `Member`.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
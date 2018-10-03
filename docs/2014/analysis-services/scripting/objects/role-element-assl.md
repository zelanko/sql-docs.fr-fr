---
title: Role, élément (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Role Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ROLE
helpviewer_keywords:
- Role element
ms.assetid: 56f52462-a7fd-4b51-a7fb-4311134439e9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 720eb01952d52e7c1b9a1ec73bae272694b1597a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48084031"
---
# <a name="role-element-assl"></a>Élément Role (ASSL)
  Contient des informations à propos d'un rôle de sécurité.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Roles>  
      <Role>  
      <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</CreateTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <Description>...</Description>  
      <Members>...</Members>  
      <Annotations>...</Annotations>  
   </Role>  
</Roles>  
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
|Éléments parents|[Roles](../collections/roles-element-assl.md)|  
|Éléments enfants|[Annotations](../collections/annotations-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [Description](../properties/description-element-assl.md), [ID](../properties/id-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [membres ](../collections/members-element-assl.md), [Nom](../properties/name-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 La définition du rôle contient les utilisateurs qui sont membres de ce rôle.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.Role>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément de base de données &#40;ASSL&#41;](database-element-assl.md)   
 [Élément de serveur &#40;ASSL&#41;](server-element-assl.md)   
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  

---
title: Niveau élément (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Level Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- LEVEL
helpviewer_keywords:
- Level element
ms.assetid: 66ee2c16-d6b8-4dd3-879f-1f2b6923bc43
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b057f53f04003755fecf4f297012559d48c6f09d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048244"
---
# <a name="level-element-assl"></a>Élément Level (ASSL)
  Définit un niveau dans un [hiérarchie](hierarchy-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Levels>  
      <Level>  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</Description>  
      <SourceAttributeID>...</SourceAttributeID>  
      <HideMemberIf>...</HideMemberIf>  
      <Translations>...</Translations>  
      <Annotations>...</Annotations>  
   </Level>  
</Levels>  
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
|Élément parent|[Levels](../collections/levels-element-assl.md)|  
|Éléments enfants|[Annotations](../collections/annotations-element-assl.md), [Description](../properties/description-element-assl.md), [HideMemberIf](../properties/hidememberif-element-assl.md), [ID](../properties/id-element-assl.md), [nom](../properties/name-element-assl.md), [SourceAttributeID](../properties/attributeid-element-assl.md), [Traductions](../collections/translations-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Ce type de données n'a pas de restrictions quel que soit le mode de déploiement (1 - Multidimensionnel et d'exploration de données, 2 - SharePoint et 3 - Tabulaire).  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.Level>.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  

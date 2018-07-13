---
title: Type de données Hierarchy (ASSL) | Microsoft Docs
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
- Hierarchy Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Hierarchy data type
ms.assetid: 2e05917e-7e5d-4dd1-817b-4ff5647747ff
caps.latest.revision: 17
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b20bed156e97c33a1c9f9df02677ef403767e472
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37230009"
---
# <a name="hierarchy-data-type-assl"></a>Type de données Hierarchy (ASSL)
  Définit un type de données primitif représentant une hiérarchie dans une dimension.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Hierarchy>  
   <Name>...</Name>  
   <ID>...</ID>  
   <Description>...</Description>  
   <DisplayFolder>...</DisplayFolder>  
   <Translations>...</Translations>  
   <AllMemberName>...</AllMemberName>  
   <AllMemberTranslations>...</AllMemberTranslation>  
   <MemberNamesUnique>...</MemberNamesUnique>  
   <AllowDuplicateNames>...</AllowDuplicateNames>  
   <Levels>...</Levels>  
   <Annotations>...</Annotation>  
</Hierarchy>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|None|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[AllMemberName](../properties/name-element-assl.md), [AllMemberTranslations](../collections/translations-element-assl.md), [AllowDuplicateNames](../properties/allowduplicatenames-element-assl.md), [Annotations](../collections/annotations-element-assl.md), [Description](../properties/description-element-assl.md), [ DisplayFolder](../properties/displayfolder-element-assl.md), [ID](../properties/id-element-assl.md), [niveaux](../collections/levels-element-assl.md), [MemberNamesUnique](../properties/membernamesunique-element-assl.md), [nom](../properties/name-element-assl.md), [ Traductions](../collections/translations-element-assl.md)|  
|Éléments dérivés|[Hierarchy](../objects/hierarchy-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L'élément *MemberNamesUnique* n'est pas pris en charge en mode DevelopmentMode 1 ou 2 pour SharePoint ou en mode de serveur tabulaire, respectivement.  
  
 L'élément *MemberKeysUnique* n'est pas pris en charge en mode DevelopmentMode 1 ou 2 pour SharePoint ou en mode de serveur tabulaire, respectivement.  
  
 L'élément *AllowDuplicateNames* n'est pas pris en charge en mode DevelopmentMode 1 ou 2 pour SharePoint ou en mode de serveur tabulaire, respectivement.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.Hierarchy>.  
  
## <a name="see-also"></a>Voir aussi  
 [Types Analysis Services Scripting Language XML données &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

---
title: "Type de données Hierarchy (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Hierarchy Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: Hierarchy data type
ms.assetid: 2e05917e-7e5d-4dd1-817b-4ff5647747ff
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5f1c0cf7c3a9048cdaeae72482e1f3c693764f48
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
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
|Types de données de base|Aucune|  
|Types de données dérivés|Aucune|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|Aucune|  
|Éléments enfants|[AllMemberName](../../../analysis-services/scripting/properties/allmembername-element-assl.md), [AllMemberTranslations](../../../analysis-services/scripting/collections/allmembertranslations-element-assl.md), [AllowDuplicateNames](../../../analysis-services/scripting/properties/allowduplicatenames-element-assl.md), [Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md), [Description](../../../analysis-services/scripting/properties/description-element-assl.md), [DisplayFolder](../../../analysis-services/scripting/properties/displayfolder-element-assl.md), [ID](../../../analysis-services/scripting/properties/id-element-assl.md), [niveaux](../../../analysis-services/scripting/collections/levels-element-assl.md), [MemberNamesUnique](../../../analysis-services/scripting/properties/membernamesunique-element-assl.md), [nom](../../../analysis-services/scripting/properties/name-element-assl.md), [traductions](../../../analysis-services/scripting/collections/translations-element-assl.md)|  
|Éléments dérivés|[Hierarchy](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L'élément *MemberNamesUnique* n'est pas pris en charge en mode DevelopmentMode 1 ou 2 pour SharePoint ou en mode de serveur tabulaire, respectivement.  
  
 L'élément *MemberKeysUnique* n'est pas pris en charge en mode DevelopmentMode 1 ou 2 pour SharePoint ou en mode de serveur tabulaire, respectivement.  
  
 L'élément *AllowDuplicateNames* n'est pas pris en charge en mode DevelopmentMode 1 ou 2 pour SharePoint ou en mode de serveur tabulaire, respectivement.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.Hierarchy>.  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services script des Types de données XML Language &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

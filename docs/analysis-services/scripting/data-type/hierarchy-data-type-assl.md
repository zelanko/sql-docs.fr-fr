---
title: "Type de données Hierarchy (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
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
ms.openlocfilehash: 9d11b630027d0109f6fbaeacb4847065151b1d42
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="hierarchy-data-type-assl"></a>Type de données Hierarchy (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Définit un type de données primitif qui représente une hiérarchie dans une dimension.  
  
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
|Éléments enfants|[AllMemberName](../../../analysis-services/scripting/properties/allmembername-element-assl.md), [AllMemberTranslations](../../../analysis-services/scripting/collections/allmembertranslations-element-assl.md), [AllowDuplicateNames](../../../analysis-services/scripting/properties/allowduplicatenames-element-assl.md), [Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md), [Description](../../../analysis-services/scripting/properties/description-element-assl.md), [DisplayFolder](../../../analysis-services/scripting/properties/displayfolder-element-assl.md), [ID](../../../analysis-services/scripting/properties/id-element-assl.md), [niveaux](../../../analysis-services/scripting/collections/levels-element-assl.md), [MemberNamesUnique](../../../analysis-services/scripting/properties/membernamesunique-element-assl.md), [nom](../../../analysis-services/scripting/properties/name-element-assl.md), [traductions](../../../analysis-services/scripting/collections/translations-element-assl.md)|  
|Éléments dérivés|[Hierarchy](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)|  
  
## <a name="remarks"></a>Notes   
 L'élément *MemberNamesUnique* n'est pas pris en charge en mode DevelopmentMode 1 ou 2 pour SharePoint ou en mode de serveur tabulaire, respectivement.  
  
 L'élément *MemberKeysUnique* n'est pas pris en charge en mode DevelopmentMode 1 ou 2 pour SharePoint ou en mode de serveur tabulaire, respectivement.  
  
 L'élément *AllowDuplicateNames* n'est pas pris en charge en mode DevelopmentMode 1 ou 2 pour SharePoint ou en mode de serveur tabulaire, respectivement.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.Hierarchy>.  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services script des Types de données XML Language &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

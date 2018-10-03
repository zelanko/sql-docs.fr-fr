---
title: Type de données Translation (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Translation Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Translation data type
ms.assetid: d40039e1-3ff6-4e20-8d8b-5baf501f726f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d6bf4fe33120a102239ccd54e7032e98719d0789
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48213690"
---
# <a name="translation-data-type-assl"></a>Type de données Translation (ASSL)
  Définit un type de données primitif représentant une traduction localisée.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Translation>  
   <Language>...</Language>  
   <Caption>...</Caption>  
   <Description>...</Description>  
   <DisplayFolder>...</DisplayFolder>  
   <Annotations>...</Annotations>  
</Translation>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|None|  
|Types de données dérivés|[AttributeTranslation](translation-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[Annotations](../collections/annotations-element-assl.md), [Caption](../properties/caption-element-assl.md), [Description](../properties/description-element-assl.md), [DisplayFolder](../properties/displayfolder-element-assl.md), [Language](../properties/language-element-assl.md)|  
|Éléments dérivés|[AllMemberTranslation](../objects/translation-element-assl.md), [AttributeAllMemberTranslation](../objects/attributeallmembertranslation-element-assl.md), [NamingTemplateTranslation](../objects/namingtemplatetranslation-element-assl.md), [UnknownMemberTranslation](../objects/unknownmembertranslation-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.Translation>.  
  
## <a name="see-also"></a>Voir aussi  
 [Types Analysis Services Scripting Language XML données &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

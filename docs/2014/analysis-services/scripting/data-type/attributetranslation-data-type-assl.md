---
title: Type de données AttributeTranslation (ASSL) | Documents Microsoft
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
- AttributeTranslation Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributeTranslation
helpviewer_keywords:
- AttributeTranslation data type
ms.assetid: a0e29941-ef08-42ad-ab9c-b2efd7910895
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9e7f5fe2157b407cae3909666329537f85a8b7e9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043457"
---
# <a name="attributetranslation-data-type-assl"></a>Type de données AttributeTranslation (ASSL)
  Définit un type de données dérivé représentant une traduction associée une [attribut](../objects/attribute-element-assl.md) élément  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AttributeTranslation>  
   <!-- The following elements extend Translation -->  
   <CaptionColumn>...</CaptionColumn>  
   <MembersWithDataCaption>...</MembersWithDataCaption>  
</AttributeTranslation>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|[Traduction](translation-data-type-assl.md)|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[CaptionColumn](../objects/column-element-assl.md), [MembersWithDataCaption](../properties/caption-element-assl.md)|  
|Éléments dérivés|Consultez [traduction](../objects/translation-element-assl.md) ([traductions](../collections/translations-element-assl.md) collection de [DimensionAttribute](dimensionattribute-data-type-assl.md) ou [ScalarMiningStructureColumn](miningstructurecolumn-data-type-assl.md))|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.AttributeTranslation>.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données de script langage XML Analysis Services &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
---
title: Élément NamingTemplateTranslation (ASSL) | Documents Microsoft
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
- NamingTemplateTranslation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NamingTemplateTranslation
helpviewer_keywords:
- NamingTemplateTranslation element
ms.assetid: 4a97a31d-23bc-4afd-a4dc-bc0ad7121f08
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: dc6c6689f4028c0983267a38435c76e7258768a4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141054"
---
# <a name="namingtemplatetranslation-element-assl"></a>Élément NamingTemplateTranslation (ASSL)
  Fournit une traduction localisée de la [NamingTemplate](../properties/namingtemplate-element-assl.md) élément un parent [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md) type de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<NamingTemplateTranslations>  
   <NamingTemplateTranslation xsi:type="Translation">...</NamingTemplateTranslation>  
</NamingTemplateTranslations>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|[Traduction](translation-element-assl.md)|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[NamingTemplateTranslations](../collections/translations-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de la `NamingTemplateTranslation` élément est utilisé uniquement par les attributs parents (en d’autres termes, la valeur de la [utilisation](../properties/usage-element-dimensionattribute-assl.md) élément de la `DimensionAttribute` parent est défini sur *Parent*) pour stocker la version localisée traduction de la `NamingTemplate` valeur pour une langue donnée.  
  
 L’élément qui correspond au parent de `NamingTemplateTranslations` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément NamingTemplate &#40;ASSL&#41;](../properties/namingtemplate-element-assl.md)   
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  
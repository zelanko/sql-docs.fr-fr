---
title: Élément NamingTemplateTranslations (ASSL) | Documents Microsoft
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
- NamingTemplateTranslations Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NamingTemplateTranslations
helpviewer_keywords:
- NamingTemplateTranslations element
ms.assetid: fde65778-1fa3-490a-9874-8bf2052ef25c
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0e22eaea2ab6d19bf1da5620321f0d2002ed382d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041484"
---
# <a name="namingtemplatetranslations-element-assl"></a>Élément NamingTemplateTranslations (ASSL)
  Fournit une collection de traductions localisées pour l'élément [NamingTemplate](../properties/namingtemplate-element-assl.md) de l'élément parent, [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Attribute xsi:type="DimensionAttribute">  
   ...  
   <NamingTemplateTranslations>  
            <NamingTemplateTranslation xsi:type="Translation">...</NamingTemplateTranslation>  
...</NamingTemplateTranslations>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Attribute](../objects/attribute-element-assl.md) de type [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Éléments enfants|[NamingTemplateTranslation](../objects/translation-element-assl.md) de type [Translation](translations-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 La valeur de la `NamingTemplateTranslation` élément est utilisé uniquement par les attributs parents (en d’autres termes, la valeur de la [utilisation](../properties/usage-element-dimensionattribute-assl.md) élément du parent `DimensionAttribute` a la valeur *Parent*.)  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Voir aussi  
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  
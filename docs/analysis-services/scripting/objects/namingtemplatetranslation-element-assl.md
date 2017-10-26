---
title: "Élément NamingTemplateTranslation (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- NamingTemplateTranslation Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- NamingTemplateTranslation
helpviewer_keywords:
- NamingTemplateTranslation element
ms.assetid: 4a97a31d-23bc-4afd-a4dc-bc0ad7121f08
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aa966a46acf8f6ce0c40b7c2ffb341552afa4e99
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="namingtemplatetranslation-element-assl"></a>Élément NamingTemplateTranslation (ASSL)
  Fournit une traduction localisée de la [NamingTemplate](../../../analysis-services/scripting/properties/namingtemplate-element-assl.md) élément un parent [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md) type de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<NamingTemplateTranslations>  
   <NamingTemplateTranslation xsi:type="Translation">...</NamingTemplateTranslation>  
</NamingTemplateTranslations>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|[Traduction](../../../analysis-services/scripting/objects/translation-element-assl.md)|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[NamingTemplateTranslations](../../../analysis-services/scripting/collections/namingtemplatetranslations-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de la **NamingTemplateTranslation** élément est utilisé uniquement par les attributs parents (en d’autres termes, la valeur de la [utilisation](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md) élément de la **DimensionAttribute** parent est défini sur *Parent*) pour stocker la traduction localisée de la **NamingTemplate** valeur pour une langue donnée.  
  
 L’élément qui correspond au parent de **NamingTemplateTranslations** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément NamingTemplate &#40; ASSL &#41;](../../../analysis-services/scripting/properties/namingtemplate-element-assl.md)   
 [Objets &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  


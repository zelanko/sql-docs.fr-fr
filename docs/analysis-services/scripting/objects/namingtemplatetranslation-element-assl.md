---
title: Élément NamingTemplateTranslation (ASSL) | Documents Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 224bf07113e5e67e4ce5ab4bb94179a55ed3da87
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="namingtemplatetranslation-element-assl"></a>Élément NamingTemplateTranslation (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 [Élément NamingTemplate &#40;ASSL&#41;](../../../analysis-services/scripting/properties/namingtemplate-element-assl.md)   
 [Objets & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  

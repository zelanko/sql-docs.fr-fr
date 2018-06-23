---
title: Élément UnknownMemberTranslation (ASSL) | Documents Microsoft
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
- UnknownMemberTranslation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- UnknownMemberTranslation
helpviewer_keywords:
- UnknownElementTranslation element
ms.assetid: a4b8cdac-b065-4a44-b251-c5ac1cfe5e6f
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 38b04dad97f6c61a884d4ba4234083bbc60bc260
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36144384"
---
# <a name="unknownmembertranslation-element-assl"></a>Élément UnknownMemberTranslation (ASSL)
  Contient une traduction de la légende de la [UnknownMember](member-element-assl.md) , élément pour un [Dimension](dimension-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<UnknownMemberTranslations>  
   <UnknownMemberTranslation xsi:type="Translation">...</UnknownMemberTranslation>  
</UnknownMemberTranslations>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|[Traduction](../data-type/translation-data-type-assl.md)|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[UnknownMemberTranslations](../collections/translations-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de `UnknownMemberTranslation` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Dimension>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Translation &#40;ASSL&#41;](translation-element-assl.md)   
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  
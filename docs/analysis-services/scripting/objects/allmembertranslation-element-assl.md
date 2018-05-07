---
title: Élément AllMemberTranslation (ASSL) | Documents Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 50f76a1af50d68e8c3fc26ab2e79fa6d006a4074
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="allmembertranslation-element-assl"></a>Élément AllMemberTranslation (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contient une traduction de la légende du membre All d’un [hiérarchie](../../../analysis-services/scripting/objects/hierarchy-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AllMemberTranslations>  
   <AllMemberTranslation xsi:type="Translation">...  
   </AllMemberTranslation>  
</AllMemberTranslations>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|[Traduction](../../../analysis-services/scripting/objects/translation-element-assl.md)|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[AllMemberTranslations](../../../analysis-services/scripting/collections/allmembertranslations-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de la **AllMemberTranslations** collection dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.Hierarchy>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Translation &#40;ASSL&#41;](../../../analysis-services/scripting/objects/translation-element-assl.md)   
 [Élément Hierarchy &#40;ASSL&#41;](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)   
 [Objets & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  

---
title: Élément AllMemberTranslations (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AllMemberTranslations Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AllMemberTranslations
helpviewer_keywords:
- AllMemberTranslations element
ms.assetid: 982ee2bf-c88d-4da5-a679-7a6b08a48a0d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0fbb23d215ee8808bae2ad5255447b6384fa7a96
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48075269"
---
# <a name="allmembertranslations-element-assl"></a>Élément AllMemberTranslations (ASSL)
  Contient la collection de [traduction](../objects/translation-element-assl.md) éléments pour la légende du membre All d’un [hiérarchie](../objects/hierarchy-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Hierarchy>  
   ...  
   <AllMemberTranslations>  
      <AllMemberTranslation xsi:type="Translation">...  
            </AllMemberTranslation>  
   </AllMemberTranslations>  
      ...  
</Hierarchy>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucun (collection)|  
|Valeur par défaut|Aucun (collection)|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Hierarchy](../objects/hierarchy-element-assl.md)|  
|Éléments enfants|[AllMemberTranslation](../objects/allmembertranslation-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de `AllMemberTranslations` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.Hierarchy>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Translation &#40;ASSL&#41;](../objects/translation-element-assl.md)   
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  

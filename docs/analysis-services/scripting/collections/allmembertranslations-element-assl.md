---
title: "Élément AllMemberTranslations (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: AllMemberTranslations Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: AllMemberTranslations
helpviewer_keywords: AllMemberTranslations element
ms.assetid: 982ee2bf-c88d-4da5-a679-7a6b08a48a0d
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 63eb22e9012da8043a57956bada680f0c30dfbf7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="allmembertranslations-element-assl"></a>Élément AllMemberTranslations (ASSL)
  Contient la collection de [traduction](../../../analysis-services/scripting/objects/translation-element-assl.md) éléments pour la légende du membre All d’un [hiérarchie](../../../analysis-services/scripting/objects/hierarchy-element-assl.md) élément.  
  
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
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Hierarchy](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)|  
|Éléments enfants|[AllMemberTranslation](../../../analysis-services/scripting/objects/allmembertranslation-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de **AllMemberTranslations** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Hierarchy>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Translation &#40; ASSL &#41;](../../../analysis-services/scripting/objects/translation-element-assl.md)   
 [Collections de &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  

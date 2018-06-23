---
title: Élément IntermediateGranularityAttributeID (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IntermediateGranularityAttributeID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- IntermediateGranularityAttributeID
helpviewer_keywords:
- IntermediateGranularityAttributeID element
ms.assetid: 49895ff0-cb0d-4bcc-ab73-8cb3d5961e12
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 680104347b19e1a7b541ab2eae84f9a6587d1d73
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140611"
---
# <a name="intermediategranularityattributeid-element-assl"></a>Élément IntermediateGranularityAttributeID (ASSL)
  Contient l'identificateur de l'attribut de granularité dans la dimension de cube intermédiaire utilisée pour lier une dimension de référence à une dimension intermédiaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ReferenceMeasureGroupDimension>  
   ...  
   <IntermediateGranularityAttributeID>...  
   </IntermediateGranularityAttributeID>  
   ...  
</ReferenceMeasureGroupDimension>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[ReferenceMeasureGroupDimension](../data-type/dimension-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de `IntermediateGranularityAttributeID` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ReferenceMeasureGroupDimension>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
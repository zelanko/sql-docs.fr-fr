---
title: Élément ModelingFlag (ASSL) | Documents Microsoft
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
- ModelingFlag Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ModelingFlag
helpviewer_keywords:
- ModelingFlag element
ms.assetid: c9af1b9a-506f-4cc1-acd7-e57698cb672c
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: fe0dcb73d3d053edfe29059970c0d5c8ba0d0268
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040054"
---
# <a name="modelingflag-element-assl"></a>Élément ModelingFlag (ASSL)
  Contient un indicateur de modélisation pour une colonne dans une structure d'exploration de données ou un modèle d'exploration de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ModelingFlags>  
   <ModelingFlag xsi:type="MiningModelingFlag">...</ModelingFlag>  
</ModelingFlags>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|[MiningModelingFlag](../data-type/miningmodelingflag-data-type-assl.md)|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[ModelingFlags](../collections/modelingflags-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Un élément étroitement lié dans le modèle objet AMO (Analysis Management Objects) est <xref:Microsoft.AnalysisServices.MiningModelingFlags>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément MiningModel &#40;ASSL&#41;](miningmodel-element-assl.md)   
 [Élément MiningStructure &#40;ASSL&#41;](miningstructure-element-assl.md)   
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  
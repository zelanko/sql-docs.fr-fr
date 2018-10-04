---
title: Élément Materialization (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Materialization Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Materialization element
ms.assetid: a87a95ae-d89c-4005-b22c-47c8991673b7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 149c2bdaa147e129b3d25637c46c10983004c1dc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48106449"
---
# <a name="materialization-element-assl"></a>Élément Materialization (ASSL)
  Indique le type de relation de dimension entre le groupe de mesures et la dimension de référence.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ReferenceMeasureGroupDimension >  
   ...  
   <Materialization>...</Materialization>  
   ...  
</ReferenceMeasureGroupDimension>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Indirect*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[ReferenceMeasureGroupDimension](../data-type/dimension-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Régulière*|La dimension de référence dispose d'une relation régulière, comme dans le cas des dimensions régulières.|  
|*Indirect*|La dimension de référence dispose d'une relation indirecte, comme dans le cas des dimensions plusieurs à plusieurs.|  
  
 L’élément qui correspond au parent de `Materialization` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.ReferenceMeasureGroupDimension>.  
  
## <a name="see-also"></a>Voir aussi  
 [Dimension élément &#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

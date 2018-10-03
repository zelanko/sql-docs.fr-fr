---
title: Élément AggregationDesigns (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AggregationDesigns Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationDesigns
helpviewer_keywords:
- AggregationDesigns element
ms.assetid: 7291956a-9c53-41fe-af2e-2418e26956c5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 03cab5a4737e88eb365f359f64490d67ab7e847f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48174169"
---
# <a name="aggregationdesigns-element-assl"></a>Élément AggregationDesigns (ASSL)
  Contient la collection des conceptions d'agrégation qu'il est possible de partager sur plusieurs partitions dans une base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MeasureGroup>  
   ...  
   <AggregationDesigns>  
      <AggregationDesign>...</AggregationDesign>  
   </AggregationDesigns>  
   ...  
</MeasureGroup>  
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
|Éléments parents|[Groupe de mesures](../objects/group-element-assl.md)|  
|Éléments enfants|[AggregationDesign](../objects/aggregationdesign-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.AggregationDesignCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément de la partition &#40;ASSL&#41;](../objects/partition-element-assl.md)   
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  

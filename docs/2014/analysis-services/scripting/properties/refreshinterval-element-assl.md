---
title: Élément RefreshInterval (ASSL) | Documents Microsoft
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
- RefreshInterval Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- RefreshInterval
helpviewer_keywords:
- RefreshInterval element
ms.assetid: 2761d26a-5fb0-452c-9a89-12f8dc658c33
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 60dbb6d89483305d971488209b8e13f85e7c2840
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052937"
---
# <a name="refreshinterval-element-assl"></a>Élément RefreshInterval (ASSL)
  Spécifie l'intervalle d'actualisation des données liées associées à l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DimensionBinding> <!-- or MeasureGroupBinding, ProactiveCachingIncrementalProcessingBinding, ProactiveCachingQueryBinding -->  
   ...  
   <RefreshInterval>...</RefreshInterval>  
   ...  
</DimensionBinding>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Durée XML|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
|Valeur par défaut|[ProactiveCachingIncrementalProcessingBinding](../data-type/binding-data-type-assl.md) ou [ProactiveCachingQueryBinding](../data-type/querybinding-data-type-assl.md) = 1 PT-s|  
|Valeur par défaut|Tous les autres = PT1m|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[DimensionBinding](../data-type/dimensionbinding-data-type-assl.md), [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-assl.md), [ProactiveCachingIncrementalProcessingBinding](../data-type/binding-data-type-assl.md), [ProactiveCachingQueryBinding](../data-type/querybinding-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Les éléments qui correspondent aux parents de `RefreshInterval` dans le modèle objet AMO (Analysis Management Objects) sont <xref:Microsoft.AnalysisServices.DimensionBinding>, <xref:Microsoft.AnalysisServices.MeasureGroupBinding>, <xref:Microsoft.AnalysisServices.ProactiveCachingIncrementalProcessingBinding> et <xref:Microsoft.AnalysisServices.ProactiveCachingQueryBinding>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
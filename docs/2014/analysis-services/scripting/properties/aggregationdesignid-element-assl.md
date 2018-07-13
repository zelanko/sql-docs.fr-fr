---
title: Élément AggregationDesignID (ASSL) | Microsoft Docs
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
- AggregationDesignID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationDesignID
helpviewer_keywords:
- AggregationDesignID element
ms.assetid: e7f1f7ae-3169-4c0c-aadb-f7465155d652
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 373f77f8195f0e8d9c3000f9e55e0f1395c91b67
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37194279"
---
# <a name="aggregationdesignid-element-assl"></a>Élément AggregationDesignID (ASSL)
  Identifie le [AggregationDesign](../objects/aggregationdesign-element-assl.md) élément associé à la [Partition](../objects/partition-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Partition>  
      ...  
   <AggregationDesignID>...</AggregationDesignID>  
   ...  
</Partition>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Partition](../objects/partition-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de `AggregationDesignID` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.Partition>. Voir aussi <xref:Microsoft.AnalysisServices.AggregationDesign>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément AggregationDesign &#40;ASSL&#41;](../objects/aggregationdesign-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

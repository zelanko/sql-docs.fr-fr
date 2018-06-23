---
title: Élément AggregationStorage (ASSL) | Documents Microsoft
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
- AggregationStorage Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationStorage
helpviewer_keywords:
- AggregationStorage element
ms.assetid: dd082388-534d-4847-9232-8f80fc9fe96e
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bb4bfcab9de31851c054a5f24382a01af1d2d9b1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038910"
---
# <a name="aggregationstorage-element-assl"></a>Élément AggregationStorage (ASSL)
  Identifie la méthode de stockage des agrégations.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ProactiveCaching>  
   ...  
   <AggregationStorage>...</AggregationStorage>  
   ...  
</ProactiveCaching>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Régulière*|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[ProactiveCaching](../objects/proactivecaching-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Régulière*|Les données d'agrégation sont stockées d'après la méthode par défaut.|  
|*MolapOnly*|Les données d'agrégation sont conservées par stockage OLAP multidimensionnel (MOLAP) uniquement.|  
  
 Le *MolapOnly* option est disponible uniquement pour les [Partition](../objects/partition-element-assl.md) élément.  
  
 L’énumération qui correspond aux valeurs autorisées pour `AggregationStorage` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ProactiveCachingAggregationStorage>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
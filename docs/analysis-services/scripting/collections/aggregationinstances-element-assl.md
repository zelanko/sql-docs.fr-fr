---
title: Élément AggregationInstances (ASSL) | Documents Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4b43b48e8827b847c8852010fa2623549f6972d2
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="aggregationinstances-element-assl"></a>Élément AggregationInstances (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contient la collection d’instances d’agrégation qui sont définies dans un [Partition](../../../analysis-services/scripting/objects/partition-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Partition>  
   ...  
   <AggregationInstances>  
      <AggregationInstance>...</AggregationInstance>  
   </AggregationInstances>  
   ...  
</Partition>  
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
|Éléments parents|[Partition](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|Éléments enfants|[AggregationInstance](../../../analysis-services/scripting/objects/aggregationinstance-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.AggregationInstanceCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Collections de & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  

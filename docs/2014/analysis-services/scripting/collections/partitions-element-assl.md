---
title: Élément (ASSL) des partitions | Documents Microsoft
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
- Partitions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Partitions
helpviewer_keywords:
- Partitions element
ms.assetid: e41c97ca-da44-48e9-a454-d25ee74209fd
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 39e719c6ae4e04e1a05abc42f4290bbf0746e55b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153806"
---
# <a name="partitions-element-assl"></a>Élément Partitions (ASSL)
  Contient la collection de [Partition](../objects/partition-element-assl.md) éléments utilisés par un [MeasureGroup](../objects/group-element-assl.md) élément ou la collection de liaisons de partition qui composent une hors ligne [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-out-of-line-assl.md)élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MeasureGroup> <!-- or MeasureGroupBinding -->  
   ...  
   <Partitions>  
      <Partition>...</Partition> <!-- parent: MeasureGroup -->  
      <!-- or -->  
      <Partition xsi:type="PartitionBinding">...</Partition> <!-- parent: MeasureGroupBinding -->  
   </Partitions>  
   ...  
</MeasureGroup>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Groupe de mesures](../objects/group-element-assl.md), [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-out-of-line-assl.md)|  
  
|Ancêtre ou parent|Élément enfant|  
|------------------------|-------------------|  
|[Groupe de mesures](../objects/group-element-assl.md)|[Partition](../objects/partition-element-assl.md)|  
|[MeasureGroupBinding](../data-type/measuregroupbinding-data-type-out-of-line-assl.md)|[Partition](../objects/partition-element-assl.md) de type [PartitionBinding](../data-type/binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.PartitionCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  
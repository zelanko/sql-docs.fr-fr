---
title: Élément StorageLocation (ASSL) | Microsoft Docs
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
- StorageLocation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- StorageLocation
helpviewer_keywords:
- StorageLocation element
ms.assetid: ecf8852f-56a1-4fcf-b0d8-d7eebb75e4ed
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fecb1a20c6c436749913ea9f8f83d284cf1000c2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37163530"
---
# <a name="storagelocation-element-assl"></a>Élément StorageLocation (ASSL)
  Contient l'emplacement de stockage du système de fichiers pour le contenu de l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Cube><!-- or MeasureGroup, Partition -->  
      ...  
   <StorageLocation>...</StorageLocation>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
|Ancêtre ou parent|Valeur par défaut|  
|------------------------|-------------------|  
|[Cube](../objects/cube-element-assl.md)|None|  
|[Groupe de mesures](../objects/group-element-assl.md)|Valeur de `StorageLocation` de l'élément parent `Cube`.|  
|[Partition](../objects/partition-element-assl.md)|Valeur de `StorageLocation` de l'élément parent `MeasureGroup`.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Cube](../objects/cube-element-assl.md), [MeasureGroup](../objects/group-element-assl.md), [Partition](../objects/partition-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Les éléments qui correspondent aux parents de `StorageLocation` dans le modèle objet AMO (Analysis Management Objects) sont <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.MeasureGroup> et <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

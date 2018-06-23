---
title: Élément MeasureGroups (ASSL) | Documents Microsoft
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
- MeasureGroups Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MeasureGroups
helpviewer_keywords:
- MeasureGroups element
ms.assetid: 80e970e9-6ea6-47a9-9e5c-d0f9b01c09c0
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c0162fd018060c767de9b6d7bfa972fc0290d387
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151994"
---
# <a name="measuregroups-element-assl"></a>Élément MeasureGroups (ASSL)
  Contient la collection de [MeasureGroup](../objects/group-element-assl.md) éléments associés à l’élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Cube> <!-- or CubeBinding, Perspective -->  
   ...  
   <MeasureGroups>  
      <MeasureGroup>...</MeasureGroup> <!-- parent: Cube -->  
      <MeasureGroup xsi:type="MeasureGroupBinding">...</MeasureGroup> <!-- parent: CubeBinding -->  
      <MeasureGroup xsi:type="PerspectiveMeasureGroup">...</MeasureGroup> <!-- parent: Perspective -->  
   </MeasureGroups>  
   ...  
</Cube>  
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
|Éléments parents|[Cube](../objects/cube-element-assl.md), [CubeBinding](../data-type/cubebinding-data-type-out-of-line-assl.md), [Perspective](../objects/perspective-element-assl.md)|  
  
|Ancêtre ou parent|Élément enfant|  
|------------------------|-------------------|  
|[Cube](../objects/cube-element-assl.md)|[Groupe de mesures](../objects/group-element-assl.md)|  
|[CubeBinding](../data-type/cubebinding-data-type-out-of-line-assl.md)|[Groupe de mesures](../objects/group-element-assl.md) de type [MeasureGroupBinding](../data-type/binding-data-type-assl.md)|  
|[Point de vue](../objects/perspective-element-assl.md)|[Groupe de mesures](../objects/group-element-assl.md) de type [PerspectiveMeasureGroup](../data-type/perspectivemeasuregroup-data-type-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L'élément correspondant dans le modèle objet AMO (Analysis Management Objects) est <xref:Microsoft.AnalysisServices.MeasureGroupCollection> ou <xref:Microsoft.AnalysisServices.PerspectiveMeasureGroupCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  
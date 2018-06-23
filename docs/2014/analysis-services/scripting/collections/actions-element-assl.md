---
title: Élément actions (ASSL) | Documents Microsoft
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
- Actions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Actions
helpviewer_keywords:
- Actions element
ms.assetid: 100a4209-2c22-4902-a8ca-f2bd99bf8fbb
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 109a6ea97218a75d64a0b9e84371e8e3667134ad
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141426"
---
# <a name="actions-element-assl"></a>Élément Actions (ASSL)
  Contient la collection d’actions pour un [Cube](../objects/cube-element-assl.md) ou [Perspective](../objects/perspective-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Cube> <!-- or Perspective -->  
   ...  
   <Actions>  
      <Action xsi:type="DrillThroughAction">...</Action> <!-- ancestor: Cube -->  
      <Action xsi:type="ReportAction">...</Action> <!-- ancestor: Cube -->  
      <Action xsi:type="StandardAction">...</Action> <!-- ancestor: Cube -->  
      <!-- or -->  
      <Action xsi:type="PerspectiveAction">...</Action> <!-- ancestor: Perspective -->  
      </Actions>  
      ...  
</Cube>  
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
|Éléments parents|[Cube](../objects/cube-element-assl.md), [Perspective](../objects/perspective-element-assl.md)|  
  
|Ancêtre ou parent|Éléments enfants|  
|------------------------|--------------------|  
|[Cube](../data-type/action-data-type-assl.md), [ReportAction](../data-type/reportaction-data-type-assl.md), [StandardAction](../data-type/standardaction-data-type-assl.md)|  
|[Point de vue](../data-type/perspectiveaction-data-type-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Les éléments correspondants dans le modèle objet AMO (Analysis Management Objects) sont <xref:Microsoft.AnalysisServices.ActionCollection> et <xref:Microsoft.AnalysisServices.PerspectiveActionCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  
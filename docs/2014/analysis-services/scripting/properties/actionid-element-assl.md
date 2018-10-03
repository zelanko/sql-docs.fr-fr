---
title: Élément ActionID (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ActionID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ActionID
helpviewer_keywords:
- ActionID element
ms.assetid: 2c9c66b2-a7ea-4874-a0ed-020ce3feab20
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ebbb9a3d62501703b00ec07095f58a51434f84b0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48104829"
---
# <a name="actionid-element-assl"></a>Élément ActionID (ASSL)
  Contient le nom d’un [Action](../objects/action-element-assl.md) élément défini sur un [Cube](../objects/cube-element-assl.md) élément qui est mis à disposition dans un [Perspective](../objects/perspective-element-assl.md) élément comme un [PerspectiveAction](../data-type/action-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<PerspectiveAction>  
   <ActionID>...</ActionID  
</PerspectiveAction>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[PerspectiveAction](../data-type/action-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de `ActionID` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.PerspectiveAction>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément actions &#40;ASSL&#41;](../collections/actions-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

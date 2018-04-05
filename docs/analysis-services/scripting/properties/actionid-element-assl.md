---
title: Élément ActionID (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ActionID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ActionID
helpviewer_keywords:
- ActionID element
ms.assetid: 2c9c66b2-a7ea-4874-a0ed-020ce3feab20
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 508a4fce7624979dac8e8180a5e8cfe070682db0
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="actionid-element-assl"></a>Élément ActionID (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Contient le nom d’un [Action](../../../analysis-services/scripting/objects/action-element-assl.md) élément défini sur un [Cube](../../../analysis-services/scripting/objects/cube-element-assl.md) élément qui est mis à disposition dans un [Perspective](../../../analysis-services/scripting/objects/perspective-element-assl.md) élément comme un [PerspectiveAction](../../../analysis-services/scripting/data-type/perspectiveaction-data-type-assl.md) élément.  
  
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
|Éléments parents|[PerspectiveAction](../../../analysis-services/scripting/data-type/perspectiveaction-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes   
 L’élément qui correspond au parent de **ActionID** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.PerspectiveAction>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément actions &#40; ASSL &#41;](../../../analysis-services/scripting/collections/actions-element-assl.md)   
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

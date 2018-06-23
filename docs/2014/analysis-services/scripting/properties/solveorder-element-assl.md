---
title: Élément SolveOrder (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- SolveOrder Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- SolveOrder
helpviewer_keywords:
- SolveOrder element
ms.assetid: ec43e055-97dd-4f2a-9a7c-2df2e1119e56
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ed5092f93494162179dc2ee142a6769eddd5d6da
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152427"
---
# <a name="solveorder-element-assl"></a>Élément SolveOrder (ASSL)
  Indique l’ordre de résolution dans lequel le [CalculationProperty](../objects/calculationproperty-element-assl.md) est appliqué à un membre calculé ou une définition de cellule calculée.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CalculationProperty>  
   ...  
   <SolveOrder>...</SolveOrder>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Entier|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[CalculationProperty](../objects/calculationproperty-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Le `SolveOrder` propriété s’applique aux `CalculationProperty` éléments avec un [CalculationType](calculationtype-element-assl.md) de *membre* ou *cellules*.  
  
 L’élément qui correspond au parent de `SolveOrder` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.CalculationProperty>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément CalculationProperties &#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [Élément MdxScript &#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [Élément MdxScripts &#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
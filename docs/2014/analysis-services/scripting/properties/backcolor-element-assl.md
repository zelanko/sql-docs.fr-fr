---
title: Élément BackColor (ASSL) | Microsoft Docs
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
- BackColor Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- BackColor
helpviewer_keywords:
- BackColor element
ms.assetid: 9024d131-74cc-4815-833a-f8cae57b7453
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ed491d6307e6e5776843c3f5e490d9369235143b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37274115"
---
# <a name="backcolor-element-assl"></a>Élément BackColor (ASSL)
  Décrit les caractéristiques des couleurs d'affichage de l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CalculationProperty> <!-- or Measure -->  
   ...  
   <BackColor>...</BackColor>  
   ...  
</CalculationProperty>  
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
|Élément parent|[CalculationProperty](../objects/calculationproperty-element-assl.md), [mesure](../objects/measure-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Le `BackColor` propriété contient une expression de langage MDX (Multidimensional Expressions) et s’applique aux `CalculationProperty` éléments avec un [CalculationType](calculationtype-element-assl.md) de *membre* ou  *Cellules*.  
  
 L’élément qui correspond au parent de `BackColor` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.CalculationProperty>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément CalculationProperties &#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [Élément MdxScript &#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [Élément MdxScripts &#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

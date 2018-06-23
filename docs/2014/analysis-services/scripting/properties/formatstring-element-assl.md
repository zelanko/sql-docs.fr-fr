---
title: Élément FormatString (ASSL) | Documents Microsoft
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
- FormatString Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- FormatString
helpviewer_keywords:
- FormatString element
ms.assetid: 7b996221-936e-4f36-a3a8-676eb9869c55
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0760432767a8f7fb1dcdec99c2ca7d76722ddb38
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043225"
---
# <a name="formatstring-element-assl"></a>Élément FormatString (ASSL)
  Décrit le format d’affichage pour un [CalculationProperty](../objects/calculationproperty-element-assl.md) élément ou un [mesure](../objects/measure-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CalculationProperty> <!-- or Measure -->  
   ...  
   <FormatString>...</FormatString>  
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
|Éléments parents|[CalculationProperty](../objects/calculationproperty-element-assl.md), [mesure](../objects/measure-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La propriété `FormatString` contient une expression MDX (Multidimensional Expressions). Dans le cas de `CalculationProperty` éléments, elle s’applique aux éléments avec un [CalculationType](calculationtype-element-assl.md) de *membre* ou *cellules*.  
  
 Les éléments qui correspondent aux parents de `FormatString` dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.CalculationProperty> et <xref:Microsoft.AnalysisServices.Measure>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément CalculationProperties &#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [Élément MdxScript &#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [Élément MdxScripts &#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
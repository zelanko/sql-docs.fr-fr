---
title: Élément ForeColor (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ForeColor Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ForeColor
helpviewer_keywords:
- ForeColor element
ms.assetid: 5125520c-3bce-40e6-a722-8d4d47306fed
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 53436deea642942f7110b542d07312ba78256989
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48216511"
---
# <a name="forecolor-element-assl"></a>Élément ForeColor (ASSL)
  Décrit les caractéristiques d’affichage liées à la couleur de la [CalculationProperty](../objects/calculationproperty-element-assl.md) ou [mesure](../objects/measure-element-assl.md) élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CalculationProperty> <!-- or Measure -->  
   ...  
   <ForeColor>...</ForeColor>  
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
 Le `ForeColor` propriété contient une expression MDX (Multidimensional Expressions) et s’applique aux `CalculationProperty` éléments qui ont un [CalculationType](calculationtype-element-assl.md) de *membre* ou *cellules* .  
  
 Les éléments qui correspondent aux parents de `ForeColor` dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.CalculationProperty> et <xref:Microsoft.AnalysisServices.Measure>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément CalculationProperties &#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [Élément MdxScript &#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [Élément MdxScripts &#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

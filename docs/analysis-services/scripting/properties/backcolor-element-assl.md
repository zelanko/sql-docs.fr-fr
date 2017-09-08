---
title: "Élément BackColor (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- BackColor Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- BackColor
helpviewer_keywords:
- BackColor element
ms.assetid: 9024d131-74cc-4815-833a-f8cae57b7453
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6a81be45420ea11b7795245c89d0d35b6dadc57d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

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
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md), [mesure](../../../analysis-services/scripting/objects/measure-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le **BackColor** propriété contient une expression de langage MDX (Multidimensional Expressions) et s’applique aux **CalculationProperty** éléments avec un [CalculationType](../../../analysis-services/scripting/properties/calculationtype-element-assl.md) de *membre* ou *cellules*.  
  
 L’élément qui correspond au parent de **BackColor** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.CalculationProperty>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément CalculationProperties &#40; ASSL &#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [Élément MdxScript &#40; ASSL &#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [Élément MdxScripts &#40; ASSL &#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

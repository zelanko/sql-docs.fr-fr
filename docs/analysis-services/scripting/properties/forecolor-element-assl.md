---
title: "Élément ForeColor (ASSL) | Documents Microsoft"
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
- ForeColor Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ForeColor
helpviewer_keywords:
- ForeColor element
ms.assetid: 5125520c-3bce-40e6-a722-8d4d47306fed
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2d596597df66ba0faf52ec1530322b2c40a5ee87
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="forecolor-element-assl"></a>Élément ForeColor (ASSL)
  Décrit les caractéristiques des couleurs d’affichage de la [CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md) ou [mesure](../../../analysis-services/scripting/objects/measure-element-assl.md) élément parent.  
  
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
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md), [mesure](../../../analysis-services/scripting/objects/measure-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le **ForeColor** propriété contient une expression MDX (Multidimensional Expressions) et s’applique aux **CalculationProperty** les éléments qui ont un [CalculationType](../../../analysis-services/scripting/properties/calculationtype-element-assl.md) de *membre* ou *cellules*.  
  
 Les éléments qui correspondent aux parents de **ForeColor** dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.CalculationProperty> et <xref:Microsoft.AnalysisServices.Measure>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément CalculationProperties &#40; ASSL &#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [Élément MdxScript &#40; ASSL &#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [Élément MdxScripts &#40; ASSL &#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  


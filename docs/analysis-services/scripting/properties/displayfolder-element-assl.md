---
title: "Élément DisplayFolder (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DisplayFolder Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DisplayFolder
helpviewer_keywords:
- DisplayFolder element
ms.assetid: 55184c02-03e7-4d6c-b87a-d4d34bc11d0e
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fc9e0f1479821a0559c9ac105cdbc2fb4f9f666c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="displayfolder-element-assl"></a>Élément DisplayFolder (ASSL)
  Spécifie le dossier dans lequel l'élément parent doit être répertorié. [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] pour les développeurs et les administrateurs peut-être prendre en charge l’utilisation des dossiers d’affichage pour permettre le classement visuel plusieurs éléments.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CalculationProperty> <!-- or Hierarchy, Kpi, Measure, Translation -->  
   ...  
   <DisplayFolder>...</DisplayFolder>  
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
|Éléments parents|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md), [hiérarchie](../../../analysis-services/scripting/objects/hierarchy-element-assl.md), [Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md), [mesure](../../../analysis-services/scripting/objects/measure-element-assl.md), [traduction](../../../analysis-services/scripting/objects/translation-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Dans les grands cubes, il peut y avoir des centaines de mesures et de hiérarchies. La propriété **DisplayFolder** définit l'apparence pour l'utilisateur sur le client. La valeur de la propriété **DisplayFolder** peut revêtir l'une des formes suivantes :  
  
-   Être vide, ce qui indique que la mesure n'appartient pas à un dossier.  
  
-   Contenir un seul nom de dossier, ce qui indique que la mesure doit être rendue comme appartenant à un dossier du même nom.  
  
-   Contenir plusieurs noms de dossier séparés par une barre oblique inverse (\\), ce qui indique une hiérarchie de dossiers incorporée.  
  
 Le **DisplayFolder** propriété s’applique aux **CalculationProperty** if uniquement des éléments la valeur de [CalculationType](../../../analysis-services/scripting/properties/calculationtype-element-assl.md) a la valeur *membre*.  
  
 Les éléments qui correspondent aux parents de **DisplayFolder** dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.CalculationProperty>, <xref:Microsoft.AnalysisServices.Hierarchy>, <xref:Microsoft.AnalysisServices.Kpi>, <xref:Microsoft.AnalysisServices.Measure>, et <xref:Microsoft.AnalysisServices.Translation>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément CalculationProperties &#40; ASSL &#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [Élément MdxScript &#40; ASSL &#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [Élément MdxScripts &#40; ASSL &#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  


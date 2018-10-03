---
title: Élément DisplayFolder (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DisplayFolder Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DisplayFolder
helpviewer_keywords:
- DisplayFolder element
ms.assetid: 55184c02-03e7-4d6c-b87a-d4d34bc11d0e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 73de197b50ebd3636cb97e6a011fee1e8c3a71af
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48220099"
---
# <a name="displayfolder-element-assl"></a>Élément DisplayFolder (ASSL)
  Spécifie le dossier dans lequel l'élément parent doit être répertorié. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] pour les développeurs et les administrateurs peut-être prendre en charge l’utilisation des dossiers d’affichage pour permettre le classement visuel plusieurs éléments.  
  
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
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[CalculationProperty](../objects/calculationproperty-element-assl.md), [hiérarchie](../objects/hierarchy-element-assl.md), [Kpi](../objects/kpi-element-assl.md), [mesure](../objects/measure-element-assl.md), [traduction](../objects/translation-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Dans les grands cubes, il peut y avoir des centaines de mesures et de hiérarchies. La propriété `DisplayFolder` définit l'apparence pour l'utilisateur sur le client. La valeur de la propriété `DisplayFolder` peut revêtir l'une des formes suivantes :  
  
-   Être vide, ce qui indique que la mesure n'appartient pas à un dossier.  
  
-   Contenir un seul nom de dossier, ce qui indique que la mesure doit être rendue comme appartenant à un dossier du même nom.  
  
-   Contenir plusieurs noms de dossier séparés par une barre oblique inverse (\\), qui dénote une hiérarchie de dossiers incorporée.  
  
 Le `DisplayFolder` propriété s’applique aux `CalculationProperty` if seuls éléments la valeur de [CalculationType](calculationtype-element-assl.md) a la valeur *membre*.  
  
 Les éléments qui correspondent aux parents de `DisplayFolder` dans le modèle objet AMO (Analysis Management Objects) sont <xref:Microsoft.AnalysisServices.CalculationProperty>, <xref:Microsoft.AnalysisServices.Hierarchy>, <xref:Microsoft.AnalysisServices.Kpi>, <xref:Microsoft.AnalysisServices.Measure> et <xref:Microsoft.AnalysisServices.Translation>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément CalculationProperties &#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [Élément MdxScript &#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [Élément MdxScripts &#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

---
title: "Élément IntermediateGranularityAttributeID (ASSL) | Documents Microsoft"
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
- IntermediateGranularityAttributeID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- IntermediateGranularityAttributeID
helpviewer_keywords:
- IntermediateGranularityAttributeID element
ms.assetid: 49895ff0-cb0d-4bcc-ab73-8cb3d5961e12
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 163c4c19455034b2e58a0652f19f584d0f08fc91
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="intermediategranularityattributeid-element-assl"></a>Élément IntermediateGranularityAttributeID (ASSL)
  Contient l'identificateur de l'attribut de granularité dans la dimension de cube intermédiaire utilisée pour lier une dimension de référence à une dimension intermédiaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ReferenceMeasureGroupDimension>  
   ...  
   <IntermediateGranularityAttributeID>...  
   </IntermediateGranularityAttributeID>  
   ...  
</ReferenceMeasureGroupDimension>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[ReferenceMeasureGroupDimension](../../../analysis-services/scripting/data-type/referencemeasuregroupdimension-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de **IntermediateGranularityAttributeID** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ReferenceMeasureGroupDimension>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  


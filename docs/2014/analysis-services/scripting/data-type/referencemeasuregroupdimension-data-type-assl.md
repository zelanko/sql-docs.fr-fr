---
title: Type de données ReferenceMeasureGroupDimension (ASSL) | Documents Microsoft
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
- ReferenceMeasureGroupDimension Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ReferenceMeasureGroupDimension
helpviewer_keywords:
- ReferenceMeasureGroupDimension data type
ms.assetid: 81f7b83e-71a3-4eab-b291-0500d05903dc
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9ca3299aa36df705a107fac63bc5ae726b606e15
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042763"
---
# <a name="referencemeasuregroupdimension-data-type-assl"></a>Type de données ReferenceMeasureGroupDimension (ASSL)
  Définit un type de données dérivé représentant une dimension indirectement liée à la table de faits par le biais d'une dimension intermédiaire. (Par exemple, un groupe de mesures Ventes peut référencer une dimension Géographie liée par le biais de la dimension Client.)  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ReferenceMeasureGroupDimension>  
   <!-- The following elements extend MeasureGroupDimension -->  
      <IntermediateCubeDimensionID>...</IntermediateCubeDimensionID>  
   <IntermediateGranularityAttributeID>...</IntermediateGranularityAttributeID>  
   <Materialization>...</Materialization>  
</ReferenceMeasureGroupDimension>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|[MeasureGroupDimension](dimension-data-type-assl.md)|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[IntermediateCubeDimensionID](../properties/id-element-assl.md), [IntermediateGranularityAttributeID](../properties/attributeid-element-assl.md), [matérialisation](../properties/materialization-element-assl.md)|  
|Éléments dérivés|None|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.ReferenceMeasureGroupDimension>.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données de script langage XML Analysis Services &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
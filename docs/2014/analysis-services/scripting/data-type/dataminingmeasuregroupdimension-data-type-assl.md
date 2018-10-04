---
title: Type de données DataMiningMeasureGroupDimension (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DataMiningMeasureGroupDimension Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DataMiningMeasureGroupDimension
helpviewer_keywords:
- DataMiningMeasureGroupDimension data type
ms.assetid: 56d5c2ec-7e03-4dc7-a668-c8d598d59e55
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9f92fb25375c3741b06ad873ac5f9facd6585570
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48171829"
---
# <a name="dataminingmeasuregroupdimension-data-type-assl"></a>Type de données DataMiningMeasureGroupDimension (ASSL)
  Définit un type de données dérivé représentant la relation entre un groupe de mesures et une dimension d'exploration de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DataMiningMeasureGroupDimension>  
   <!-- The following elements extend MeasureGroupDimension -->  
      <CaseCubeDimensionID>...</CaseCubeDimensionID>  
</DataMiningMeasureGroupDimension>  
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
|Éléments enfants|[CaseCubeDimensionID](../properties/id-element-assl.md)|  
|Éléments dérivés|Consultez [Dimension](../objects/dimension-element-assl.md) ([Dimensions](../collections/dimensions-element-assl.md) collection de [MeasureGroup](../objects/group-element-assl.md))|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.DataMiningMeasureGroupDimension>.  
  
## <a name="see-also"></a>Voir aussi  
 [Types Analysis Services Scripting Language XML données &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

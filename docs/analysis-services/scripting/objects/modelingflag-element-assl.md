---
title: "Élément ModelingFlag (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ModelingFlag Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: ModelingFlag
helpviewer_keywords: ModelingFlag element
ms.assetid: c9af1b9a-506f-4cc1-acd7-e57698cb672c
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dac2667ffaef9eb231148fa8be8d83b5b1e573ee
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="modelingflag-element-assl"></a>Élément ModelingFlag (ASSL)
  Contient un indicateur de modélisation pour une colonne dans une structure d'exploration de données ou un modèle d'exploration de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ModelingFlags>  
   <ModelingFlag xsi:type="MiningModelingFlag">...</ModelingFlag>  
</ModelingFlags>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|[MiningModelingFlag](../../../analysis-services/scripting/data-type/miningmodelingflag-data-type-assl.md)|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[ModelingFlags](../../../analysis-services/scripting/collections/modelingflags-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Un élément étroitement lié dans le modèle objet AMO (Analysis Management Objects) est <xref:Microsoft.AnalysisServices.MiningModelingFlags>.  
  
## <a name="see-also"></a>Voir aussi  
 [MiningModel, élément &#40; ASSL &#41;](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)   
 [Élément MiningStructure &#40; ASSL &#41;](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)   
 [Objets &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  

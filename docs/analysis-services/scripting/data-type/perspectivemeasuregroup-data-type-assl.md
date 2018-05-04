---
title: Type de données PerspectiveMeasureGroup (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PerspectiveMeasureGroup Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- PerspectiveMeasureGroup
helpviewer_keywords:
- PerspectiveMeasureGroup data type
ms.assetid: 5927120d-f30e-4f87-8523-6d17012817d7
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ad2ff813a39fca0f8c0db50710035c74d328835e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="perspectivemeasuregroup-data-type-assl"></a>Type de données PerspectiveMeasureGroup (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Définit un type de données primitif qui fournit des informations sur un groupe de mesures dans un élément [Perspective](../../../analysis-services/scripting/objects/perspective-element-assl.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<PerspectiveMeasureGroup>  
   <MeasureGroupID>...</MeasureGroupID>  
   <Measures>...</Measures>  
   <Annotations>...</Annotations>  
</PerspectiveMeasureGroup>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|Aucune|  
|Types de données dérivés|Aucune|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|Aucune|  
|Éléments enfants|[Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md), [MeasureGroupID](../../../analysis-services/scripting/properties/measuregroupid-element-assl.md), [Measures](../../../analysis-services/scripting/collections/measures-element-assl.md)|  
|Éléments dérivés|[MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md) (collection[MeasureGroups](../../../analysis-services/scripting/collections/measuregroups-element-assl.md) de [Perspective](../../../analysis-services/scripting/objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>Notes  
 Un groupe de mesures dans une perspective a la même structure qu'un groupe de mesures dans le cube sous-jacent.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.PerspectiveMeasureGroup>.  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services script des Types de données XML Language & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

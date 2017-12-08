---
title: "Type de données PerspectiveMeasure (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
apiname: PerspectiveMeasure Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: PerspectiveMeasure
helpviewer_keywords: PerspectiveMeasure data type
ms.assetid: 8622ad67-3dcf-48e2-ad4a-c5f0a086eec3
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e8766d72a3c6b9fa4c399224f4592e3815826a48
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="perspectivemeasure-data-type-assl"></a>Type de données PerspectiveMeasure (ASSL)
  Définit un type de données primitif qui représente des informations sur une mesure dans un [PerspectiveMeasureGroup](../../../analysis-services/scripting/data-type/perspectivemeasuregroup-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<PerspectiveMeasure>  
   <MeasureID>...</MeasureID>  
   <Annotations>...</Annotations>  
</PerspectiveMeasure>  
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
|Éléments enfants|[Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md), [MeasureID](../../../analysis-services/scripting/properties/measureid-element-assl.md)|  
|Éléments dérivés|[Mesure](../../../analysis-services/scripting/objects/measure-element-assl.md) ([mesures](../../../analysis-services/scripting/collections/measures-element-assl.md) collection de [PerspectiveMeasureGroup](../../../analysis-services/scripting/data-type/perspectivemeasuregroup-data-type-assl.md))|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.PerspectiveMeasure>.  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services script des Types de données XML Language &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

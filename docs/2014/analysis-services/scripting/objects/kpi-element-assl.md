---
title: Élément KPI (ASSL) | Documents Microsoft
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
- Kpi Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Kpi
helpviewer_keywords:
- Kpi element
ms.assetid: 1979a58f-97a8-4c1a-aa65-dcfb6d2404cf
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6205e1a14a992ed8bd0fc05f91d162e90be3346c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040272"
---
# <a name="kpi-element-assl"></a>Élément Kpi (ASSL)
  Définit un indicateur de performance clé (KPI) dans un [Cube](cube-element-assl.md) élément ou un [Perspective](perspective-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Kpis>  
   <Kpi> <!-- ancestor: Cube -->  
            <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</Description>  
      <Translations>...</Translations>  
      <DisplayFolder>...</DisplayFolder>  
      <AssociatedMeasureGroupID>...</AssociatedMeasureGroupID>  
      <Value>...</Value>  
            <Goal>...</Goal>  
      <Status>...</Status>  
      <Trend>...</Trend>  
      <TrendGraphic>...</TrendGraphic>  
      <StatusGraphic>...</StatusGraphic>  
      <CurrentTimeMember>...</CurrentTimeMember>  
      <Annotations>...</Annotations>  
   </Kpi>  
   <!-- or -->  
   <Kpi xsi:type="PerspectiveKpi">...</Kpi> <!-- ancestor: Perspective -->  
   </Kpi>  
</Kpis>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
|Ancêtre ou parent|Type de données|  
|------------------------|---------------|  
|[Cube](cube-element-assl.md)|None|  
|[Point de vue](../data-type/perspectivekpi-data-type-assl.md)|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Indicateurs de performance clés](../collections/kpis-element-assl.md)|  
  
## <a name="child-elements"></a>Éléments enfants  
  
|Ancêtre ou parent|Éléments enfants|  
|------------------------|--------------------|  
|[Cube](../collections/annotations-element-assl.md), [AssociatedMeasureGroupID](../properties/id-element-assl.md), [CurrentTimeMember](member-element-assl.md), [Description](../properties/description-element-assl.md), [DisplayFolder](../properties/displayfolder-element-assl.md), [Goal](../properties/goal-element-assl.md), [ID](../properties/id-element-assl.md), [Name](../properties/name-element-assl.md), [Status](../properties/status-element-assl.md), [StatusGraphic](../properties/statusgraphic-element-assl.md), [Translations](../collections/translations-element-assl.md), [Trend](../properties/trend-element-assl.md), [TrendGraphic](../properties/trendgraphic-element-assl.md), [Value](../properties/value-element-assl.md)|  
|[Point de vue](perspective-element-assl.md)|None|  
  
## <a name="remarks"></a>Notes  
 Les éléments correspondants dans le modèle objet AMO (Analysis Management Objects) sont <xref:Microsoft.AnalysisServices.Kpi> et <xref:Microsoft.AnalysisServices.PerspectiveKpi>.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  
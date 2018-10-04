---
title: Élément perspective (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Perspective Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Perspective
helpviewer_keywords:
- Perspective element
ms.assetid: 0442334c-8b00-4451-ad81-02e58c735e8f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7ed510b7c4b9a9c023c6bad875ed2e6293ac2ac4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168229"
---
# <a name="perspective-element-assl"></a>Élément Perspective (ASSL)
  Définit des détails pour un point de vue d’un [Cube](cube-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Perspectives>  
   <<Perspective>  
      <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <Description>...</Description>  
      <Translations>...</Translations>  
      <DefaultMeasure>...</DefaultMeasure>  
      <Dimensions>...</Dimensions>  
            <MeasureGroups>...</MeasureGroups>  
      <Calculations>...</Calculations>  
      <Kpis>...</Kpis>  
            <Actions>...</Actions>  
      <Annotations>...</Annotations>  
   </Perspective>  
</Perspectives>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Perspectives](../collections/perspectives-element-assl.md)|  
|Éléments enfants|[Actions](../collections/actions-element-assl.md), [Annotations](../collections/annotations-element-assl.md), [calculs](../collections/calculations-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [DefaultMeasure](measure-element-assl.md), [ Description](../properties/description-element-assl.md), [Dimensions](../collections/dimensions-element-assl.md), [ID](../properties/id-element-assl.md), [indicateurs de performance clés](../collections/kpis-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [ MeasureGroups](../collections/groups-element-assl.md), [nom](../properties/name-element-assl.md), [traductions](../collections/translations-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Une perspective fournit un sous-ensemble d'un cube obtenu en sélectionnant les dimensions, les hiérarchies, les attributs et d'autres détails à inclure et en définissant la tranche de données à inclure. Une perspective est possédée par un seul cube. Il n'est pas possible de remplacer ou d'ajouter des objets dans une perspective ; les dimensions, les hiérarchies et les autres détails doivent tous exister dans le cube sous-jacent. Il n'est pas possible d'inclure des objets et de les marquer comme non visibles.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.Perspective>.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  

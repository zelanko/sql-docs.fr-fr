---
title: Mesurer, élément (ASSL) | Microsoft Docs
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
- Measure Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Measure
helpviewer_keywords:
- Measure element
ms.assetid: 4c2c2ed1-7f78-4564-982a-132f13bea36f
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 80d59a5356bf1c0b5712e729f230fff9383603cc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37159330"
---
# <a name="measure-element-assl"></a>Élément Measure (ASSL)
  Définit une mesure.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Measures>  
   <Measure> <!-- ancestor: MeasureGroup -->  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</Description>  
      <AggregateFunction>...</AggregateFunction>  
            <DataType>...</DataType>  
            <Source>...</Source>  
      <Visible>...</Visible>  
      <MeasureExpression>...</MeasureExpression>  
      <DisplayFolder>...</DisplayFolder>  
      <FormatString>...</FormatString>  
      <BackColor>...</BackColor>  
      <ForeColor>...</ForeColor>  
            <FontName>...</FontName>  
            <FontSize>...</FontSize>  
            <FontFlags>...</FontFlags>  
            <Translations>...</Translations>  
      <Annotations>...</Annotations>  
   </Measure>  
   <!-- or  -->  
   <Measure xsi:type="AggregationInstanceMeasure">...</Measure> <!-- parent: AggregationInstance -->  
      <!-- or  -->  
   <Measure xsi:type="MeasureBinding">...</Measure> <!-- ancestor: MeasureGroupBinding (out-of-line) -->  
   <!-- or  -->  
   <Measure xsi:type="PerspectiveMeasure">...</Measure> <!-- ancestor: PerspectiveMeasureGroup -->  
</Measures>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
|Ancêtre ou parent|Type de données|  
|------------------------|---------------|  
|[AggregationInstance](../data-type/binding-data-type-assl.md)|  
|[Groupe de mesures](group-element-assl.md)|None|  
|[MeasureGroupBinding (hors ligne)](../data-type/measurebinding-data-type-assl.md)|  
|[PerspectiveMeasureGroup](../data-type/perspectivemeasure-data-type-assl.md)|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Mesures](../collections/measures-element-assl.md)|  
  
|Ancêtre ou parent|Éléments enfants|  
|------------------------|--------------------|  
|[MeasureGroup](../properties/aggregatefunction-element-assl.md), [Annotations](../collections/annotations-element-assl.md), [BackColor](../properties/backcolor-element-assl.md), [DataType](../properties/datatype-element-assl.md), [Description](../properties/description-element-assl.md), [DisplayFolder ](../properties/displayfolder-element-assl.md), [FontFlags](../properties/fontflags-element-assl.md), [FontName](../properties/name-element-assl.md), [FontSize](../properties/fontsize-element-assl.md), [ForeColor](../properties/forecolor-element-assl.md), [FormatString ](../properties/formatstring-element-assl.md), [ID](../properties/id-element-assl.md), [MeasureExpression](../properties/expression-element-assl.md), [nom](../properties/name-element-assl.md), [Source](../properties/source-element-measure-assl.md), [traductions](../collections/translations-element-assl.md), [Visible](../properties/visible-element-assl.md)|  
|Autres|None|  
  
## <a name="remarks"></a>Notes  
 Les détails de liaison peuvent être fournis pour une mesure. Ces détails se comportent ensuite comme les valeurs par défaut par partition.  
  
 Dans les grands cubes, il peut y avoir des centaines de mesures et de hiérarchies. La propriété `DisplayFolder` définit l'apparence pour l'utilisateur sur le client. La valeur de la propriété `DisplayFolder` peut revêtir l'une des formes suivantes :  
  
-   Être vide, ce qui indique que la mesure n'appartient pas à un dossier.  
  
-   Contenir un seul nom de dossier, ce qui indique que la mesure doit être rendue comme appartenant à un dossier du même nom.  
  
-   Contenir plusieurs noms de dossier séparés par une barre oblique inverse (\\), qui dénote une hiérarchie de dossiers incorporée.  
  
 La propriété `DisplayFolder` s'applique également aux mesures calculées et aux hiérarchies.  
  
 Les éléments correspondants dans le modèle objet AMO (Analysis Management Objects) sont <xref:Microsoft.AnalysisServices.Measure> et <xref:Microsoft.AnalysisServices.PerspectiveMeasure>.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  

---
title: Type de données MeasureGroupDimension (ASSL) | Documents Microsoft
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
- MeasureGroupDimension Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MeasureGroupDimension
helpviewer_keywords:
- MeasureGroupDimension data type
ms.assetid: 9d1c1c19-31ce-4c42-b2e6-4c1b08875a83
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 369e20e1eaf3c5716e81a580b587c69efa64455f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151991"
---
# <a name="measuregroupdimension-data-type-assl"></a>Type de données MeasureGroupDimension (ASSL)
  Définit un type de données primitif abstrait représentant la relation entre une dimension et un groupe de mesures.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MeasureGroupDimension>  
   <CubeDimensionID>...</CubeDimensionID>  
      <Annotations>...</Annotations>  
   <Source>...</Source>  
</MeasureGroupDimension>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|None|  
|Types de données dérivés|[DataMiningMeasureGroupDimension](dimension-data-type-assl.md), [DegenerateMeasureGroupDimension](measuregroupdimension-data-type-assl.md), [ManyToManyMeasureGroupDimension](manytomanymeasuregroupdimension-data-type-assl.md), [ReferenceMeasureGroupDimension](referencemeasuregroupdimension-data-type-assl.md), [RegularMeasureGroupDimension](regularmeasuregroupdimension-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[Annotations](../collections/annotations-element-assl.md), [CubeDimensionID](../properties/id-element-assl.md), [Source](../properties/source-element-binding-assl.md)|  
|Éléments dérivés|[Dimension](../objects/dimension-element-assl.md) (collection[Dimensions](../collections/dimensions-element-assl.md) de [MeasureGroup](../objects/group-element-assl.md))|  
  
## <a name="remarks"></a>Notes  
 Chaque type de données `MeasureGroupDimension` est une référence à l'une des dimensions dans le cube. Ces références définissent quelles dimensions du cube s'appliquent au groupe de mesures.  
  
 L'ensemble des attributs fournis détermine la granularité (étendue) avec laquelle les mesures dans le groupe de mesures sont connues. Par exemple, les mesures qui représentent des ventes de produits apparaissent dans le groupe de mesures Sales. Les informations concernant ces mesures sont stockées dans la source de données sous-jacente à une granularité mensuelle, plutôt qu'hebdomadaire ou quotidienne. Dans ce cas, seul l'attribut Month (Mois) serait répertorié pour le type de données `MeasureGroupDimension` décrivant la relation entre une dimension de temps et le groupe de mesures Sales. Dans de rares cas, la granularité peut être définie sous la forme d'un ensemble d'attributs. Par exemple, dans le cas de l'ensemble d'attributs {Day, Week, Month, Year} où Day (Jour) implique Week (Semaine) et Month (Mois) mais Week n'implique pas Month, les mesures contenues dans le groupe de mesures Forecasts (Prévisions) peuvent être connues par mois et par semaine, mais pas par jour.  
  
 Si aucun attribut n'est fourni, le résultat obtenu donnerait l'impression que seul l'attribut de clé de la dimension est répertorié (définition du niveau de granularité le plus bas). Chaque partition d'un groupe de mesures doit posséder la même granularité. L'ensemble des attributs répertoriés ne doit pas apparaître comme un élément redondant par rapport aux relations entre les attributs. Par exemple, si Month implique Year (Année), la granularité est définie sous la forme Month, et non Month et Year.  
  
 Un type de données `MeasureGroupDimension` doit inclure une hiérarchie uniquement s'il inclut des éléments spécifiques à présenter sur celle-ci. (Il n'existe aucun moyen de déterminer quelles hiérarchies s'appliquent à un groupe de mesures particulier). De la même façon, il doit inclure un type de données [MeasureGroupAttribute](measuregroupattribute-data-type-assl.md) uniquement s'il dispose d'éléments spécifiques à signaler à ce sujet.  
  
 Chaque hiérarchie doit être un sous-ensemble des hiérarchies incluses dans l'élément [CubeDimension](cubedimension-data-type-assl.md). Vous ne pouvez pas sélectionner les niveaux même si certains d'entre eux peuvent être automatiquement désactivés en fonction de la granularité du groupe de mesures.  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.MeasureGroupDimension>.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données de script langage XML Analysis Services &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
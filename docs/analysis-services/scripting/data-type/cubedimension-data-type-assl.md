---
title: Type de données CubeDimension (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/15/2017
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
- CubeDimension Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- CubeDimension
helpviewer_keywords:
- CubeDimension data type
ms.assetid: 128ac790-65a1-4e35-b909-8dba2a61b24c
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 222126f9cef7e778cc9271796e7147a36389424b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="cubedimension-data-type-assl"></a>Type de données CubeDimension (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Définit un type de données primitif qui représente la relation entre une dimension et un cube.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CubeDimension>  
      <ID>...</ID>  
   <Name>...</Name>  
   <Translations>...</Translations>  
   <DimensionID>...</DimensionID>  
   <Visible>...</Visible>  
   <AllMemberAggregationUsage>...</AllMemberAggregationUsage>  
   <HierarchyUniqueNameStyle>...</HierarchyUniqueNameStyle>  
   <MemberUniqueNameStyle>...</MemberUniqueNameStyle>  
      <Attributes>...</Attributes>  
   <Hierarchies>...</Hierarchies>  
      <Annotations>...</Annotation>  
</CubeDimension>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|None|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[AllMemberAggregationUsage](../../../analysis-services/scripting/properties/allmemberaggregationusage-element-assl.md), [Annotations](../../../analysis-services/scripting/collections/annotations-element-assl.md), [attributs](../../../analysis-services/scripting/collections/attributes-element-assl.md), [DimensionID](../../../analysis-services/scripting/properties/dimensionid-element-assl.md), [hiérarchies](../../../analysis-services/scripting/collections/hierarchies-element-assl.md), [HierarchyUniqueNameStyle](../../../analysis-services/scripting/properties/hierarchyuniquenamestyle-element-assl.md), [ID](../../../analysis-services/scripting/properties/id-element-assl.md), [MemberUniqueNameStyle](../../../analysis-services/scripting/properties/memberuniquenamestyle-element-assl.md), [nom](../../../analysis-services/scripting/properties/name-element-assl.md), [Visible](../../../analysis-services/scripting/properties/visible-element-assl.md), [traductions](../../../analysis-services/scripting/collections/translations-element-assl.md)|  
|Éléments dérivés|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md) ([Dimensions](../../../analysis-services/scripting/collections/dimensions-element-assl.md) collection de [Cube](../../../analysis-services/scripting/objects/cube-element-assl.md))|  
  
## <a name="remarks"></a>Notes   
 Il y a un type de données **CubeDimension** pour chaque relation de dimension sur un **Cube**. Le type de données **CubeDimension** couvre tous les éléments **MeasureGroups** du cube.  
  
 A **CubeDimension** doit inclure un [CubeHierarchy](../../../analysis-services/scripting/data-type/cubehierarchy-data-type-assl.md) si la dimension a une influence spécifique sur la hiérarchie, y compris la désactivation de la hiérarchie (, autorisant ainsi sélection dont les hiérarchies s’appliquent à une utilisation de la dimension particulier), ou en rendant la hiérarchie invisible.  
  
 De même, un **CubeDimension** doit inclure un [CubeAttribute](../../../analysis-services/scripting/data-type/cubeattribute-data-type-assl.md) uniquement si la dimension a une influence spécifique sur l’attribut. (Bien qu'il n'y ait aucun moyen de sélectionner quels attributs appliquer à une utilisation de dimension particulière, les attributs peuvent être rendus invisibles).  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.CubeDimension>.  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services script des Types de données XML Language &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

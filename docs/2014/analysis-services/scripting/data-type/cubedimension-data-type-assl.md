---
title: Type de données CubeDimension (ASSL) | Documents Microsoft
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
- CubeDimension Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubeDimension
helpviewer_keywords:
- CubeDimension data type
ms.assetid: 128ac790-65a1-4e35-b909-8dba2a61b24c
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4a043895929e09a59d3ae14c5995804c4fa5c7eb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039211"
---
# <a name="cubedimension-data-type-assl"></a>Type de données CubeDimension (ASSL)
  Définit un type de données primitif représentant la relation entre une dimension et un cube.  
  
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
|Éléments enfants|[AllMemberAggregationUsage](../properties/aggregationusage-element-assl.md), [Annotations](../collections/annotations-element-assl.md), [attributs](../collections/attributes-element-assl.md), [DimensionID](../properties/id-element-assl.md), [hiérarchies](../collections/hierarchies-element-assl.md), [HierarchyUniqueNameStyle](../properties/hierarchyuniquenamestyle-element-assl.md), [ID](../properties/id-element-assl.md), [MemberUniqueNameStyle](../properties/memberuniquenamestyle-element-assl.md), [nom](../properties/name-element-assl.md), [Visible](../properties/visible-element-assl.md), [Traductions](../collections/translations-element-assl.md)|  
|Éléments dérivés|[Dimension](../objects/dimension-element-assl.md) ([Dimensions](../collections/dimensions-element-assl.md) collection de [Cube](../objects/cube-element-assl.md))|  
  
## <a name="remarks"></a>Notes  
 Il y a un type de données `CubeDimension` pour chaque relation de dimension sur un `Cube`. Le type de données `CubeDimension` couvre tous les éléments `MeasureGroups` du cube.  
  
 A `CubeDimension` doit inclure un [CubeHierarchy](hierarchy-data-type-assl.md) si la dimension a une influence spécifique sur la hiérarchie, y compris la désactivation de la hiérarchie (ce qui permet la sélection des hiérarchies s’appliquent à un emplacement donné utilisation de la dimension), ou en rendant la hiérarchie invisible.  
  
 De même, un `CubeDimension` doit inclure un [CubeAttribute](cubeattribute-data-type-assl.md) uniquement si la dimension a une influence spécifique sur l’attribut. (Bien qu'il n'y ait aucun moyen de sélectionner quels attributs appliquer à une utilisation de dimension particulière, les attributs peuvent être rendus invisibles).  
  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.CubeDimension>.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données de script langage XML Analysis Services &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
---
title: ID d’élément (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ID
helpviewer_keywords:
- ID element
ms.assetid: ea3ce0f4-9084-45d0-8150-73afb7005af2
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c323bd71865d0dd09bf724373ece03d83e7608ee
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37209939"
---
# <a name="id-element-assl"></a>Élément ID (ASSL)
  Contient l'identificateur unique (ID) unique de l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Action> <!-- or one of the elements listed in the Element Relationships table -->  
   ...  
   <ID>...</ID>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (jusqu'à 100 caractères)|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Action](../objects/action-element-assl.md), [agrégation](../objects/aggregation-element-assl.md), [AggregationDesign](../objects/aggregationdesign-element-assl.md), [Assembly](../objects/assembly-element-assl.md), [Cube](../objects/cube-element-assl.md), [CubeBinding](../data-type/cubebinding-data-type-out-of-line-assl.md), [CubeDimension](../data-type/dimension-data-type-assl.md), [base de données](../objects/database-element-assl.md), [DataSource](../objects/datasource-element-assl.md), [DataSourceView](../objects/datasourceview-element-assl.md), [Dimension ](../objects/dimension-element-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [hiérarchie](../objects/hierarchy-element-assl.md), [Kpi](../objects/kpi-element-assl.md), [niveau](../objects/level-element-assl.md), [MdxScript](../objects/mdxscript-element-assl.md), [Mesure](../objects/measure-element-assl.md), [MeasureGroup](../objects/group-element-assl.md), [MeasureGroupBinding](../data-type/binding-data-type-assl.md), [MiningModel](../objects/miningmodel-element-assl.md), [ MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md), [MiningStructure](../objects/miningstructure-element-assl.md), [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md), [Partition](../objects/partition-element-assl.md), [autorisation](../data-type/permission-data-type-assl.md), [Perspective](../objects/perspective-element-assl.md), [rôle](../objects/role-element-assl.md), [Server](../objects/server-element-assl.md), [Trace](../objects/trace-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Chaque objet principal dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] a un `ID` élément en tant que propriété. La valeur d’un `ID` élément présente les restrictions suivantes :  
  
-   La valeur ne peut pas contenir des espaces de début ni de fin. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supprimera de manière implicite les espaces de début ou de fin de la valeur d'un élément `ID`.  
  
-   La valeur ne peut pas contenir des caractères de contrôle. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supprimera de manière implicite les caractères de contrôle de la valeur d'un élément `ID`.  
  
-   Les valeurs réservées suivantes ne peuvent pas être utilisées :  
  
    -   AUX  
  
    -   CLOCK$  
  
    -   COM1 à COM9 (COM1, COM2, COM3, et ainsi de suite)  
  
    -   CON  
  
    -   LPT1 à LPT9 (LPT1, LPT2, LPT3, et ainsi de suite)  
  
    -   NUL  
  
    -   PRN  
  
 Le tableau suivant répertorie les caractères supplémentaires qui ne peut pas être utilisés dans la valeur d’un `ID` élément, en fonction de l’élément parent.  
  
|Élément parent|Caractères|  
|--------------------|----------------|  
|[Server](../objects/server-element-assl.md)|La valeur doit se conformer aux règles énoncées pour les noms des ordinateurs équipés de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. (Les adresses IP ne sont pas valides.)|  
|[DataSource](../objects/datasource-element-assl.md)|:/\\*&#124;?" [] (){}<>|  
|[Niveau](../objects/level-element-assl.md), [attribut d’élément](../objects/attribute-element-assl.md)|.,;' `:/\\*&#124;?" & % $! [] +={}<>|  
|Tous les autres éléments parents|.,;' `:/\\*&#124;?" & % $! [] de () +={}<>|  
  
## <a name="see-also"></a>Voir aussi  
 [Nommez l’élément &#40;ASSL&#41;](name-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

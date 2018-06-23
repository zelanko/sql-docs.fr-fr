---
title: Nom d’élément (ASSL) | Documents Microsoft
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
- Name Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Name
helpviewer_keywords:
- Name element
ms.assetid: caf2af86-5f9c-4e14-8168-f3a79248b4fe
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: cb2185d9d2a87a2abc3ebb96ad8186fe288e6190
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36053156"
---
# <a name="name-element-assl"></a>Élément Name (ASSL)
  Contient le nom de l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Action> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Name>...</Name>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (jusqu'à 100 caractères)|  
|Valeur par défaut|Varie|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule fois|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Action](../objects/action-element-assl.md), [Aggregation](../objects/aggregation-element-assl.md), [AggregationDesign](../objects/aggregationdesign-element-assl.md), [AlgorithmParameter](../objects/algorithmparameter-element-assl.md), [Annotation](../objects/annotation-element-assl.md), [Assembly](../objects/assembly-element-assl.md), [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md), [Cube](../objects/cube-element-assl.md), [CubeDimension](../data-type/dimension-data-type-assl.md), [CubeHierarchy](../data-type/hierarchy-data-type-assl.md), [Database](../objects/database-element-assl.md), [DataSource](../objects/datasource-element-assl.md), [DataSourceView](../objects/datasourceview-element-assl.md), [Dimension](../objects/dimension-element-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [Group](../objects/group-element-assl.md), [Hierarchy](../objects/hierarchy-element-assl.md), [Kpi](../objects/kpi-element-assl.md), [Level](../objects/level-element-assl.md), [MdxScript](../objects/mdxscript-element-assl.md), [Measure](../objects/measure-element-assl.md), [MeasureGroup](../objects/measuregroup-element-assl.md), [MemberProperty](../objects/attributerelationship-element-assl.md), [MiningModel](../objects/miningmodel-element-assl.md), [MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md), [MiningStructure](../objects/miningstructure-element-assl.md), [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md), [Partition](../objects/partition-element-assl.md), [Permission](../data-type/permission-data-type-assl.md), [Perspective](../objects/perspective-element-assl.md), [PerspectiveCalculation](../data-type/perspectivecalculation-data-type-assl.md), [ReportFormatParameter](../objects/reportformatparameter-element-asl.md), [ReportParameter](../objects/reportparameter-element-assl.md), [Role](../objects/role-element-assl.md), [Server](../objects/server-element-assl.md), [ServerProperty](../objects/serverproperty-element-assl.md), [Trace](../objects/trace-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Chaque élément est utilisé pour définir un objet (une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], une hiérarchie, un attribut et ainsi de suite) a un `Name` élément en tant que propriété. La valeur d'un élément `Name` est soumise aux restrictions suivantes :  
  
-   La valeur ne peut pas contenir des espaces de début ni de fin. Si des espaces de début ou de fin apparaissent dans la valeur d'un élément `Name`, ils seront supprimés de manière implicite par [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
-   La valeur ne doit pas contenir de caractères de contrôle. La présence de caractères de contrôle dans le nom est donc fortement déconseillée et peut parfois provoquer des erreurs de validation XML.  
  
     Pour les objets créés à l'aide de la méthode `GetNewName` dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], AMO vérifie et supprime ensuite tous les caractères de contrôle, les espaces de début et les espaces de fin dans le nom. C'est pourquoi l'utilisation de `GetNewName` est l'approche recommandée pour définir des noms d'objets.  
  
     Toutefois, si vous définissez la propriété `Name` directement, les mêmes contrôles de validation ne sont pas effectués, ce qui peut provoquer des erreurs de validation XML. Une erreur se produit en fonction du caractère de contrôle présent dans le nom.  
  
     Bien que les caractères de contrôle ne doivent jamais être utilisés dans un nom d'objet, Analysis Services ne les empêche pas expressément. Les versions antérieures d'Analysis Services autorisaient parfois des caractères de contrôle dans un nom d'objet. Pour cette raison, [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] ignore les caractères de contrôle dans un nom d'objet afin d'éviter de compromettre les solutions plus anciennes.  
  
-   Les valeurs réservées suivantes ne peuvent pas être utilisées :  
  
    -   AUX  
  
    -   CLOCK$  
  
    -   COM1 à COM9 (COM1, COM2, COM3, et ainsi de suite)  
  
    -   CON  
  
    -   LPT1 à LPT9 (LPT1, LPT2, LPT3, et ainsi de suite)  
  
    -   NUL  
  
    -   PRN  
  
 Le tableau suivant répertorie les caractères supplémentaires qui ne peuvent être employés dans la valeur d'un élément `Name` en fonction de l'élément parent.  
  
|Élément parent|Caractères non valides|  
|--------------------|------------------------|  
|[Server](../objects/server-element-assl.md)|Le nom doit se conformer aux règles énoncées pour les noms des ordinateurs équipés de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. Les adresses IP ne sont pas valides.|  
|[DataSource](../objects/datasource-element-assl.md)|:/\\*&#124;?" [] de (){}<>|  
|[Niveau](../objects/level-element-assl.md), [élément d’attribut](../objects/attribute-element-assl.md)|.,;' `:/\\*&#124;?" & % $! [] de +={}<>|  
|Tous les autres éléments parents|.,;' `:/\\*&#124;?" & % $! %$!+=()[]5D;{}{}<>|  
  
## <a name="see-also"></a>Voir aussi  
 [ID d’élément &#40;ASSL&#41;](id-element-assl.md)   
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
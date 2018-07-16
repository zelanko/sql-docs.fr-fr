---
title: Élément AggregationPrefix (ASSL) | Microsoft Docs
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
- AggregationPrefix Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationPrefix
helpviewer_keywords:
- AggregationPrefix element
ms.assetid: 1581e0df-ae8e-41ce-9c92-f0f7cac487f2
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d7f7fe7ad16c8949116edb13c7d2c9b5144443dd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37293279"
---
# <a name="aggregationprefix-element-assl"></a>Élément AggregationPrefix (ASSL)
  Définit le préfixe commun à utiliser pour les noms d'agrégation dans l'ensemble de l'élément parent associé.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Cube> <!-- or Database, MeasureGroup, Partition -->  
   ...  
   <AggregationPrefix>...</AggregationPrefix>  
   ...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Cube](../objects/cube-element-assl.md), [base de données](../objects/database-element-assl.md), [MeasureGroup](../objects/group-element-assl.md), [Partition](../objects/partition-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Préfixes d’agrégation génèrent des noms d’agrégation dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]et également générer des noms de tables dans la base de données relationnelle pour les agrégations stockées dans une partition ROLAP (OLAP) relationnelle.  
  
 Un nom d'agrégation complètement développé se compose des parties suivantes :  
  
 *\<DatabasePrefix >\<CubePrefix >\<MeasureGroupPrefix >\<PartitionPrefix >\<AggregationID >*  
  
 Les quatre premières parties du nom d'agrégation forment le préfixe d'agrégation. L'utilisateur fournit les quatre premières parties :  
  
-   *DatabasePrefix* représente la valeur de la `AggregationPrefix` élément associé à un `Database` élément.  
  
-   *CubePrefix* représente la valeur de la `AggregationPrefix` élément associé à un `Cube` élément.  
  
-   *MeasureGroupPrefix* représente la valeur de la `AggregationPrefix` élément associé à un `MeasureGroup` élément.  
  
-   *PartitionPrefix* représente la valeur de la `AggregationPrefix` élément associé à un `Partition` élément.  
  
 La cinquième partie du nom, *AggregationID*, est un identificateur défini par le système et les utilisateurs ont aucun contrôle sur cette partie du nom.  
  
 Les éléments qui correspondent aux parents de `AggregationPrefix` dans le modèle objet AMO (Analysis Management Objects) sont <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.MeasureGroup> et <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

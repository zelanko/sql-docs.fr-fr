---
title: "Élément Cardinality (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Cardinality Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Cardinality element
ms.assetid: 60ac8a26-7c8b-4011-9b9b-a29863779428
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4275f4ce39d24aebce00da8275a9a175c9a90238
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="cardinality-element-assl"></a>Élément Cardinality (ASSL)
  Indique la cardinalité de la relation décrite par un [AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md) ou [RegularMeasureGroupDimension](../../../analysis-services/scripting/data-type/regularmeasuregroupdimension-data-type-assl.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<AttributeRelationship> <!-- or RegularMeasureGroupDimension -->  
   ...  
   <Cardinality>...</Cardinality>  
   ...  
</AttributeRelationship>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Nombreux*|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md), [RegularMeasureGroupDimension](../../../analysis-services/scripting/data-type/regularmeasuregroupdimension-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*Nombreux*|Relation plusieurs-à-un|  
|*Une*|Relation un-à-un|  
  
 L’énumération qui correspond aux valeurs autorisées pour **cardinalité** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Cardinality>.  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs et hiérarchies d’attributs](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  


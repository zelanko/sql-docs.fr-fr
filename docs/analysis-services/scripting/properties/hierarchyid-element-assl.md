---
title: "Élément HierarchyID (ASSL) | Documents Microsoft"
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
- HierarchyID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- HierarchyID
helpviewer_keywords:
- HierarchyID element
ms.assetid: 6effe47d-e598-41f8-993a-b2bce49fd7dd
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3e4aa9e9298a84d7befbdeea5011a0e712c8550b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="hierarchyid-element-assl"></a>Élément HierarchyID (ASSL)
  Contient l’identificateur (ID) d’un [CubeHierarchy](../../../analysis-services/scripting/data-type/cubehierarchy-data-type-assl.md), [MeasureGroupHierarchy](../../../analysis-services/scripting/data-type/measuregrouphierarchy-data-type-assl.md), ou [PerspectiveHierarchy](../../../analysis-services/scripting/data-type/perspectivehierarchy-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CubeHierarchy> <!-- or MeasureGroupHierarchy, PerspectiveHierarchy -->  
      ...  
   <HierarchyID>...</HierarchyID>  
      ...  
</CubeHierarchy>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[CubeHierarchy](../../../analysis-services/scripting/data-type/cubehierarchy-data-type-assl.md), [MeasureGroupHierarchy](../../../analysis-services/scripting/data-type/measuregrouphierarchy-data-type-assl.md), [PerspectiveHierarchy](../../../analysis-services/scripting/data-type/perspectivehierarchy-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Les éléments qui correspondent aux parents de **HierarchyID** dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.CubeHierarchy> et <xref:Microsoft.AnalysisServices.PerspectiveHierarchy>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  


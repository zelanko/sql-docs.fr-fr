---
title: "Élément Relationships (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: e78882c9-b14e-4044-848e-ea7fddd3b75d
caps.latest.revision: "7"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 674359f59b5288590dbf8b0ce890227089e31c42
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="relationships-element-assl"></a>Élément Relationships (ASSL)
  Contient la collection de relations pour la dimension associée.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CubeDimension> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Attributes>  
      <Attribute>...</Attribute>  
  </Attributes>  
   ...  
</CubeDimension>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md), [Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md), [PerspectiveDimension](../../../analysis-services/scripting/data-type/perspectivedimension-data-type-assl.md), [RegularMeasureGroupDimension](../../../analysis-services/scripting/data-type/regularmeasuregroupdimension-data-type-assl.md)|  
|Éléments enfants|[Relation](../../../analysis-services/scripting/data-type/relationship-data-type-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Les éléments correspondants dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.RelationshipCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Collections de &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  

---
title: Élément Relationships (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: e78882c9-b14e-4044-848e-ea7fddd3b75d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b0a83a2e7722fab119df3a0918ea0ecbe7c24131
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48134551"
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
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[CubeDimension](../data-type/dimension-data-type-assl.md), [Dimension](../objects/dimension-element-assl.md), [PerspectiveDimension](../data-type/perspectivedimension-data-type-assl.md), [RegularMeasureGroupDimension](../data-type/measuregroupdimension-data-type-assl.md)|  
|Éléments enfants|[Relation](../data-type/relationship-data-type-assl.md)|  
  
## <a name="remarks"></a>Notes  
 Les éléments correspondants dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.RelationshipCollection>.  
  
## <a name="see-also"></a>Voir aussi  
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  

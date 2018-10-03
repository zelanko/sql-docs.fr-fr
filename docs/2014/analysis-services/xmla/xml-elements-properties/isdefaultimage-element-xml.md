---
title: Élément IsDefaultImage (XML) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: e29cd137-af82-4753-a681-0d3e705513f3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0821c2dfaa25f3d9a557663046db0405aca0cb24
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48201369"
---
# <a name="isdefaultimage-element-xml"></a>Élément IsDefaultImage (XML)
  Indique qu'il est possible d'obtenir l'image par défaut de cette entité en parcourant cette relation jusqu'à l'autre table et en extrayant le membre ayant l'attribut IsDefaultImage.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<RelationshipEndVisualizationProperties>  
   ...  
   <IsDefaultImage>...</IsDefaultImage>  
   ...  
</RelationshipEndVisualizationProperties>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Booléen|  
|Valeur par défaut|false|  
|Cardinalité|0-1 : élément facultatif qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[RelationshipEndVisualizationProperties](../../scripting/data-type/relationshipendvisualizationproperties-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Pour les éléments `RelationshipEndVisualizationProperties`, l'élément `IsDefaultImage` indique que l'image par défaut de cette entité peut être obtenue en naviguant jusqu'à l'autre extrémité de cette relation. La valeur par défaut `false` indique qu'il n'existe aucune image par défaut.  
  
  

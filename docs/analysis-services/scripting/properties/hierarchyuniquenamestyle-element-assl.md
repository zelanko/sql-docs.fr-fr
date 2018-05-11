---
title: Élément HierarchyUniqueNameStyle (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b3af9cf51cd813257e7d5a3dbd2ae08d005d4805
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="hierarchyuniquenamestyle-element-assl"></a>Élément HierarchyUniqueNameStyle (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Détermine comment des noms uniques sont générés pour les hiérarchies qui sont contenus dans le [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<CubeDimension>  
   ...  
   <HierarchyUniqueNameStyle>...</HierarchyUniqueNameStyle>  
   ...  
</CubeDimension>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*IncludeDimensionName*|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*IncludeDimensionName*|Le nom de la dimension est inclus dans le nom de la hiérarchie.|  
|*ExcludeDimensionName*|Le nom de la dimension n'est pas inclus dans le nom de la hiérarchie.|  
  
 L’élément qui correspond au parent de **HierarchyUniqueNameStyle** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.CubeDimension>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément cube & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Élément dimension & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

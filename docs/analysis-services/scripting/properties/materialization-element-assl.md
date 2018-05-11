---
title: Élément Materialization (ASSL) | Documents Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c620e4fb43246dcd5d761503c0368665ff4a61a4
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="materialization-element-assl"></a>Élément Materialization (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Indique le type de relation de dimension entre le groupe de mesures et la dimension de référence.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<ReferenceMeasureGroupDimension >  
   ...  
   <Materialization>...</Materialization>  
   ...  
</ReferenceMeasureGroupDimension>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Indirecte*|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[ReferenceMeasureGroupDimension](../../../analysis-services/scripting/data-type/referencemeasuregroupdimension-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*Regular*|La dimension de référence dispose d'une relation régulière, comme dans le cas des dimensions régulières.|  
|*Indirecte*|La dimension de référence dispose d'une relation indirecte, comme dans le cas des dimensions plusieurs à plusieurs.|  
  
 L’élément qui correspond au parent de **matérialisation** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.ReferenceMeasureGroupDimension>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément dimension & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

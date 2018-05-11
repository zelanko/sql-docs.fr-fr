---
title: Élément AggregationDesignID (ASSL) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a947676c65929b3844d1bd8a982818aea2f0d5e9
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="aggregationdesignid-element-assl"></a>Élément AggregationDesignID (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Identifie la [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md) élément associé à la [Partition](../../../analysis-services/scripting/objects/partition-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Partition>  
      ...  
   <AggregationDesignID>...</AggregationDesignID>  
   ...  
</Partition>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Partition](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de **AggregationDesignID** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Partition>. Voir aussi <xref:Microsoft.AnalysisServices.AggregationDesign>.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément AggregationDesign & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)   
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

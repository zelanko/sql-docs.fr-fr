---
title: Élément ClassifiedColumns (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ClassifiedColumns Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ClassifiedColumns
helpviewer_keywords:
- ClassifiedColumns element
ms.assetid: f16b4f51-c38d-4601-98b8-1497dbf12d02
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6e2624c2d944af873fe6a34cbd9ca3684050bf92
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48209829"
---
# <a name="classifiedcolumns-element-assl"></a>Élément ClassifiedColumns (ASSL)
  Contient la collection de colonnes associées classées par le [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MiningStructureColumn xsi:type="ScalarMiningStructureColumn">  
   ...  
   <ClassifiedColumns>  
      <ClassifiedColumnID>...</ClassifiedColumnID>  
   </ClassifiedColumns>  
   ...  
</MiningStructureColumn>  
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
|Éléments parents|[MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) de type[ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|Éléments enfants|[ClassifiedColumnID](../properties/id-element-assl.md)|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de `ClassifiedColumns` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Voir aussi  
 [Type de données MiningStructureColumn &#40;ASSL&#41;](../data-type/miningstructurecolumn-data-type-assl.md)   
 [Élément MiningStructure &#40;ASSL&#41;](../objects/miningstructure-element-assl.md)   
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  

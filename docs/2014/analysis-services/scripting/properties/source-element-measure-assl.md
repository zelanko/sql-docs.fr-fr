---
title: Source de l’élément (mesure) (ASSL) | Documents Microsoft
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
- Source Element (Measure)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Source
helpviewer_keywords:
- Source element
ms.assetid: 9bae7ba4-3065-4623-b3e0-d54cebea7503
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ed41316f62469268d86a89d0c0a5e59f07c8f726
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042760"
---
# <a name="source-element-measure-assl"></a>Élément Source (Measure) (ASSL)
  Contient les détails de la source contenant la valeur de la [mesure](../objects/measure-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Measure>  
      ...  
   <Source xsi:type="DataItem">...</Source>  
      ...  
</Measure>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[Mesure](../objects/measure-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Le `Source` de la `DataItem`, qui sert le `Source` de la `Measure`, peut à son tour être de type [RowBinding](../data-type/binding-data-type-assl.md), [ColumnBinding](../data-type/columnbinding-data-type-assl.md), [MeasureBinding ](../data-type/measurebinding-data-type-assl.md), ou [CubeDimensionBinding](../data-type/dimensionbinding-data-type-assl.md).  
  
 Pour plus d’informations sur la `DataItem` type, y compris une table des objets ASSL et les propriétés de la `DataItem` de type, consultez [Type de données DataItem &#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md).  
  
 L’élément qui correspond au parent de `Source` dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.Measure>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
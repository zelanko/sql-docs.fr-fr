---
title: Élément IsAggregatable (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- IsAggregatable Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- IsAggregatable
helpviewer_keywords:
- IsAggregatable element
ms.assetid: ed7dbe89-259c-4c5c-9660-b965c3af1573
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9974e3ad5f06073fd3aaab2aeaea5abfb6517544
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48093049"
---
# <a name="isaggregatable-element-assl"></a>Élément IsAggregatable (ASSL)
  Spécifie si les valeurs de la [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md) élément peut être agrégé.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DimensionAttribute>  
      ...  
   <IsAggregatable>...</IsAggregatable>  
  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Booléen|  
|Valeur par défaut|True|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L’élément qui correspond au parent de `IsAggregatable` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  

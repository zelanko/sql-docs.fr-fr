---
title: Élément NameColumn (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- NameColumn Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NameColumn
helpviewer_keywords:
- NameColumn element
ms.assetid: 9ff79f2e-26d7-4ab9-a166-14c2c2d1fc07
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b51c297b2b7c81b4cbec4f629cf3efe9e8b367b1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48095649"
---
# <a name="namecolumn-element-assl"></a>Élément NameColumn (ASSL)
  Identifie la colonne qui fournit le nom de l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DimensionAttribute> <!-- or ScalarMiningStructureColumn -->  
   ...  
   <NameColumn xsi:type="DataItem">...</NameColumn>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
|Ancêtre ou parent|Valeur par défaut|  
|------------------------|-------------------|  
|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|Variable (voir Remarques)|  
|[ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|None|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Si le [KeyColumns](../collections/columns-element-assl.md) collection de `DimensionAttribute` contient un seul [KeyColumn](column-element-assl.md) élément représentant une colonne clé avec un type de données chaîne, les mêmes `DataItem` valeurs sont utilisées comme valeurs par défaut le `NameColumn` élément.  
  
 Pour plus d’informations sur la `DataItem` type, notamment un tableau des objets d’Analysis Services Scripting Language (ASSL) et les propriétés de la `DataItem` de type, consultez [Type de données DataItem &#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md).  
  
 Les éléments qui correspondent aux parents de `NameColumn` dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.DimensionAttribute> et <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets &#40;ASSL&#41;](objects-assl.md)  
  
  

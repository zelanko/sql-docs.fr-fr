---
title: "Élément ValueColumn (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ValueColumn Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- ValueColumn element
ms.assetid: 6c2d6822-8ecc-46df-9fa9-bb92ac716c36
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c17b9dea933e1beee1f4957a9bb6f82c669963be
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="valuecolumn-element-assl"></a>Élément ValueColumn (ASSL)
  Identifie la colonne qui fournit la valeur de l'élément parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <ValueColumn xsi:type="DataItem">...</ValueColumn>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Valeur par défaut|Variable (voir Remarques)|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Si le [NameColumn](../../../analysis-services/scripting/objects/namecolumn-element-assl.md) élément de **DimensionAttribute** est spécifié, le même **DataItem** valeurs sont utilisées comme valeurs par défaut pour le **ValueColumn** élément. Si le **NameColumn** élément de **DimensionAttribute** n’est pas spécifié et la [KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md) collection de **DimensionAttribute** contient un seul [KeyColumn](../../../analysis-services/scripting/objects/keycolumn-element-assl.md) élément représentant une colonne clé avec un type de données chaîne, les mêmes **DataItem** valeurs sont utilisées comme valeurs par défaut pour le **ValueColumn** élément.  
  
 Pour plus d’informations sur la **DataItem** type, y compris un tableau d’objets d’Analysis Services Scripting Language (ASSL) et les propriétés de la **DataItem** de type, consultez [Type de données DataItem &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
 Les éléments qui correspondent aux parents de **NameColumn** dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.DimensionAttribute> et <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  


---
title: "Élément NameColumn (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- NameColumn Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- NameColumn
helpviewer_keywords:
- NameColumn element
ms.assetid: 9ff79f2e-26d7-4ab9-a166-14c2c2d1fc07
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3d625f03339e5b17981db9d4e8105679fde40fb0
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

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
|Type de données et longueur|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Valeur par défaut|Consultez le tableau ci-dessous.|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
|Ancêtre ou parent|Valeur par défaut|  
|------------------------|-------------------|  
|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|Variable (voir Remarques)|  
|[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|Aucune|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md), [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Si le [KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md) collection de **DimensionAttribute** contient un seul [KeyColumn](../../../analysis-services/scripting/objects/keycolumn-element-assl.md) élément représentant une colonne clé avec un type de données chaîne, les mêmes **DataItem** valeurs sont utilisées comme valeurs par défaut pour le **NameColumn** élément.  
  
 Pour plus d’informations sur la **DataItem** type, y compris un tableau d’objets d’Analysis Services Scripting Language (ASSL) et les propriétés de la **DataItem** de type, consultez [Type de données DataItem &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
 Les éléments qui correspondent aux parents de **NameColumn** dans le modèle d’objet objets AMO (Analysis Management) sont <xref:Microsoft.AnalysisServices.DimensionAttribute> et <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  

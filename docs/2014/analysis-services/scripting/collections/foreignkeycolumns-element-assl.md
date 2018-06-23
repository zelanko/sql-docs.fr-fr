---
title: Élément ForeignKeyColumns (ASSL) | Documents Microsoft
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
- ForeignKeyColumns Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ForeignKeyColumns
helpviewer_keywords:
- ForeignKeyColumns element
ms.assetid: 0a673c1a-73dd-4217-aa41-56b340b5e1ab
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: da17077a4a75efc53de65b2168a5332db137bfd1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052932"
---
# <a name="foreignkeycolumns-element-assl"></a>Élément ForeignKeyColumns (ASSL)
  Contient la collection des colonnes qui identifient la jointure à la table parente pour une source de données relationnelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MiningStructureColumn xsi:type="TableMiningStructureColumn">  
   ...  
   <ForeignKeyColumns>  
      <ForeignKeyColumn xsi:type="DataItem">...</ForeignKeyColumn>  
...</ForeignKeyColumns>  
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
|Éléments parents|[MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) de type [TableMiningStructureColumn](../data-type/tableminingstructurecolumn-data-type-assl.md)|  
|Éléments enfants|[ForeignKeyColumn](../objects/column-element-assl.md) de type [DataItem](../data-type/dataitem-data-type-assl.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Élément MiningStructure &#40;ASSL&#41;](../objects/miningstructure-element-assl.md)   
 [Collections &#40;ASSL&#41;](collections-assl.md)  
  
  
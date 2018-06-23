---
title: L’élément CellOrdinal (XMLA) | Documents Microsoft
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
- CellOrdinal Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cellordinal
- urn:schemas-microsoft-com:xml-analysis#CellOrdinal
- http://schemas.microsoft.com/analysisservices/2003/engine#CellOrdinal
helpviewer_keywords:
- CellOrdinal element
ms.assetid: 1808c498-e3b4-4e5c-9e22-7f8662d32874
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 2fbcf210fa9c1d816ef78c20fe762e7a7b15d636
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151969"
---
# <a name="cellordinal-element-xmla"></a>Élément CellOrdinal (XMLA)
  Contient la position ordinale dans un cube d’une cellule à mettre à jour par une [UpdateCells](../xml-elements-commands/updatecells-element-xmla.md) commande.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Cell>  
   ...  
   <CellOrdinal>...</CellOrdinal>  
   ...  
</Cell>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Long|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[cellule](cell-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L'élément `CellOrdinal` identifie la cellule à mettre à jour par la commande `UpdateCells`.  
  
 Pour plus d’informations sur la mise à jour des cellules, consultez [Mise à jour de cellules &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Valeur d’élément &#40;XMLA&#41;](value-element-xmla.md)   
 [Élément UpdateCells &#40;XMLA&#41;](../xml-elements-commands/updatecells-element-xmla.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
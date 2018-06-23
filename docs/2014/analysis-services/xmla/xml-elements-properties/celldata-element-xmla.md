---
title: Élément CellData (XMLA) | Documents Microsoft
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
- CellData Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CellData
- http://schemas.microsoft.com/analysisservices/2003/engine#CellData
- urn:schemas-microsoft-com:xml-analysis#CellData
- microsoft.xml.analysis.celldata
helpviewer_keywords:
- CellData element
ms.assetid: 0ebfb5e1-a674-4b9b-bd8c-c529da105f61
caps.latest.revision: 27
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: ce445127e78f7f503bf3b81a640047f0d1f1d87f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152903"
---
# <a name="celldata-element-xmla"></a>Élément CellData (XMLA)
  Contient une collection d'éléments Cell qui représentent les données de cellule que contient un élément [root](root-element-xmla.md) utilisant le type de données [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:mddataset">  
   ...  
   <CellData>  
      <Cell>...</Cell>  
   </CellData>  
</root>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[racine](root-element-xmla.md)|  
|Éléments enfants|[cellule](cell-element-mddataset-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Dans l'élément root parent, l'élément `Axes` est suivi par l'élément `CellData`, une collection d'éléments `Cell` qui contiennent les valeurs de propriété de cellule pour chaque cellule retournée dans le dataset multidimensionnel.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
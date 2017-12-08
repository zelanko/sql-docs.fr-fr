---
title: "Élément CellData (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: CellData Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- CellData
- http://schemas.microsoft.com/analysisservices/2003/engine#CellData
- urn:schemas-microsoft-com:xml-analysis#CellData
- microsoft.xml.analysis.celldata
helpviewer_keywords: CellData element
ms.assetid: 0ebfb5e1-a674-4b9b-bd8c-c529da105f61
caps.latest.revision: "27"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ca30896c998b10fd948cc3dccb1a07132d579fb9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="celldata-element-xmla"></a>Élément CellData (XMLA)
  Contient une collection d'éléments Cell qui représentent les données de cellule que contient un élément [root](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) utilisant le type de données [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) .  
  
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
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[racine](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|Éléments enfants|[Cellule](../../../analysis-services/xmla/xml-elements-properties/cell-element-mddataset-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Dans l'élément root parent, l'élément **Axes** est suivi par l'élément **CellData** , une collection d'éléments **Cell** qui contiennent les valeurs de propriété de cellule pour chaque cellule retournée dans le dataset multidimensionnel.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

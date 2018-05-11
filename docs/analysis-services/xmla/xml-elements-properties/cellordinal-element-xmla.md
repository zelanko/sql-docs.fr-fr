---
title: L’élément CellOrdinal (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d10b59424490885861ce1a976d94bfa54f677fdf
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="cellordinal-element-xmla"></a>Élément CellOrdinal (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contient la position ordinale dans un cube d’une cellule à mettre à jour par une [UpdateCells](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md) commande.  
  
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
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Cellule](../../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le **CellOrdinal** élément identifie la cellule à mettre à jour par le **UpdateCells** commande.  
  
 Pour plus d’informations sur la mise à jour des cellules, consultez [Mise à jour de cellules &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Valeur d’élément & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/value-element-xmla.md)   
 [Élément UpdateCells & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)   
 [Propriétés & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

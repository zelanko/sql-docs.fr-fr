---
title: Valeur d’élément (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2ecaaf902ee1f29700b2d6333bbccd549d9c2193
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38062850"
---
# <a name="value-element-xmla"></a>Élément Value (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contient la valeur souhaitée d’un [attribut](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md) élément doit être ajouté par un [insérer](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md) commande, ou un [cellule](../../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md) élément à mettre à jour par un [UpdateCells](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)commande.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Attribute> <!-- or Cell --!>  
   ...  
   <Value>...</Value>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques d’éléments  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Tout|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Attribut](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md), [cellule](../../../analysis-services/xmla/xml-elements-properties/cell-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Pour **attribut** éléments, le **valeur** élément contient la valeur souhaitée que doit posséder le membre après le **insérer** commande est validée. Pour plus d’informations sur l’insertion de membres, consultez [insertion, mise à jour et suppression de membres &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
 Pour **cellule** éléments, le **valeur** élément contient la valeur souhaitée que doit posséder la cellule après le **UpdateCells** commande est validée. La valeur réelle stockée dans la table d'écriture différée pour cette cellule correspond à la différence entre la valeur d'origine de la cellule et la valeur souhaitée de cette dernière.  
  
 Le type de données utilisé par cet élément doit correspondre au type de données de la cellule à mettre à jour.  
  
 Pour plus d’informations sur la mise à jour des cellules, consultez [Mise à jour de cellules &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md).  
  
## <a name="see-also"></a>Voir aussi
 [Élément CellOrdinal &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/cellordinal-element-xmla.md)   
 [Insérer un élément &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Élément UpdateCells &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)   
 [Propriétés &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

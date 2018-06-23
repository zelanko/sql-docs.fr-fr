---
title: Valeur d’élément (XMLA) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Value Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.value
- urn:schemas-microsoft-com:xml-analysis#Value
- http://schemas.microsoft.com/analysisservices/2003/engine#Value
helpviewer_keywords:
- Value element
ms.assetid: f87ca7f8-d9fe-4730-a706-5d50fcfe21df
caps.latest.revision: 14
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 7a422298e8d1b77f3d036b4cea5761dc6dc6dde4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039586"
---
# <a name="value-element-xmla"></a>Élément Value (XMLA)
  Contient la valeur souhaitée d’un [attribut](attribute-element-xmla.md) élément à ajouter à un [insérer](../xml-elements-commands/insert-element-xmla.md) commande, ou un [cellule](cell-element-xmla.md) élément être mis à jour par une [UpdateCells](../xml-elements-commands/updatecells-element-xmla.md)commande.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Attribute> <!-- or Cell --!>  
   ...  
   <Value>...</Value>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Tout|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Attribut](attribute-element-xmla.md), [cellule](cell-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Pour les éléments `Attribute`, l'élément `Value` contient la valeur souhaitée que doit posséder le membre après validation de la commande `Insert`. Pour plus d’informations sur l’insertion de membres, consultez [insertion, mise à jour et suppression de membres &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
 Pour les éléments `Cell`, l'élément `Value` contient la valeur souhaitée que doit posséder la cellule après validation de la commande `UpdateCells`. La valeur réelle stockée dans la table d'écriture différée pour cette cellule correspond à la différence entre la valeur d'origine de la cellule et la valeur souhaitée de cette dernière.  
  
 Le type de données utilisé par cet élément doit correspondre au type de données de la cellule à mettre à jour.  
  
 Pour plus d’informations sur la mise à jour des cellules, consultez [Mise à jour de cellules &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [L’élément CellOrdinal &#40;XMLA&#41;](cellordinal-element-xmla.md)   
 [Insérer l’élément &#40;XMLA&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [Élément UpdateCells &#40;XMLA&#41;](../xml-elements-commands/updatecells-element-xmla.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
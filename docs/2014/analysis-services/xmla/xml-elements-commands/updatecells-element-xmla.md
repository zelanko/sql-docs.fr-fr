---
title: Élément UpdateCells (XMLA) | Microsoft Docs
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
- UpdateCells Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.updatecells
- urn:schemas-microsoft-com:xml-analysis#UpdateCells
- http://schemas.microsoft.com/analysisservices/2003/engine#UpdateCells
helpviewer_keywords:
- UpdateCells command
ms.assetid: 18336a35-8a46-4532-9ee7-71828b2982af
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 05b3b1dae8f409f367a88b696accb77484304b4e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37219979"
---
# <a name="updatecells-element-xmla"></a>Élément UpdateCells (XMLA)
  Met à jour des cellules dans un cube activé en écriture.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Command>  
   <UpdateCells>  
      <Cell>...</Cell>  
   </UpdateCells>  
</Command>  
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
|Éléments parents|[Commandee](../xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|[Cellule](../xml-elements-properties/cell-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 La commande `UpdateCells` met à jour des cellules dans un cube qui prend en charge l'écriture différée de cellule.  
  
 Pour plus d’informations sur la mise à jour des cellules, consultez [Mise à jour de cellules &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Élément DROP &#40;XMLA&#41;](drop-element-xmla.md)   
 [Insérer un élément &#40;XMLA&#41;](insert-element-xmla.md)   
 [Mettre à jour d’élément &#40;XMLA&#41;](update-element-xmla.md)   
 [Commandes &#40;XMLA&#41;](xml-elements-commands.md)  
  
  

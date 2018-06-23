---
title: Où l’élément (XMLA) | Documents Microsoft
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
- Where Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Where
- microsoft.xml.analysis.where
- http://schemas.microsoft.com/analysisservices/2003/engine#Where
helpviewer_keywords:
- Where element
ms.assetid: 81fb4190-3379-4ddf-8795-a0772f3b92bb
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 4e63d2ecd6f20d374c6746c7d3bc77ad455f1ef6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154469"
---
# <a name="where-element-xmla"></a>Élément Where (XMLA)
  Définit une condition de filtre utilisée par la commande parente [Drop](../xml-elements-commands/drop-element-xmla.md) ou [Update](../xml-elements-commands/update-element-xmla.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Drop> <!-- or Update -->  
   ...  
   <Where>  
      <Attributes>...</Attributes>  
   </Where>  
   ...  
</Insert>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Drop](../xml-elements-commands/drop-element-xmla.md), [Update](../xml-elements-commands/update-element-xmla.md)|  
|Éléments enfants|[Attributs](attributes-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Pour `Drop` commandes, le `Where` élément, combiné à la [DeleteWithDescendants](deletewithdescendants-element-xmla.md) élément, identifie l’étendue des membres d’attribut à supprimer.  
  
 Pour les commandes `Update`, l'élément `Where` identifie l'étendue des membres d'attribut à mettre à jour. Plusieurs membres d'attribut peuvent être mis à jour à l'aide d'une combinaison d'attributs inclus dans la collection `Attributes` de la commande `Update` parente et la collection `Attributes` de l'élément `Where`.  
  
 Pour plus d’informations sur la suppression et la mise à jour des membres d’attribut, consultez [Insertion, mise à jour et suppression de membres &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
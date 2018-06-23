---
title: Élément DROP (XMLA) | Documents Microsoft
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
- Drop Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Drop
- microsoft.xml.analysis.drop
- http://schemas.microsoft.com/analysisservices/2003/engine#Drop
helpviewer_keywords:
- Drop element
ms.assetid: a5d21db3-743a-4958-b16d-b6816a5ee787
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 64f6fd75c3c5032c035ca4af6b9950a0de1e6ddc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153786"
---
# <a name="drop-element-xmla"></a>Élément Drop (XMLA)
  Supprime des membres d'attribut d'une dimension.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Command>  
   <Drop>  
      <Object>...</Object>  
      <DeleteWithDescendants>...</DeleteWithDescendants>  
      <Where>...</Where>  
   </Drop>  
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
|Éléments enfants|[DeleteWithDescendants](../xml-elements-properties/deletewithdescendants-element-xmla.md), [objet](../xml-elements-properties/object-element-dimension-xmla.md), [où](../xml-elements-properties/where-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 La commande `Drop` supprime des membres d'attribut d'une dimension activée en écriture.  
  
 Pour plus d’informations sur la suppression de membres, consultez [insertion, mise à jour et suppression de membres &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Insérer l’élément &#40;XMLA&#41;](insert-element-xmla.md)   
 [Mettre à jour d’élément &#40;XMLA&#41;](update-element-xmla.md)   
 [Commandes &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
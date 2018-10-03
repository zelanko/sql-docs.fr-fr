---
title: Clé d’élément (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Key Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Key
- urn:schemas-microsoft-com:xml-analysis#Key
- microsoft.xml.analysis.key
helpviewer_keywords:
- Key element
ms.assetid: 09d3cd48-49f7-4b58-b8bb-ca75b81bb02f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f1532db273c83f16678d278f068befefcd8df4b4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48101279"
---
# <a name="key-element-xmla"></a>Élément Key (XMLA)
  Contient une valeur de clé de membre pour un membre d'attribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Keys>  
   ...  
   <Key>...</Key>  
   ...  
</Keys>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Tout|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Clés](keys-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Le type de données utilisé par cet élément doit correspondre au type de données de la colonne clé appropriée de l'attribut spécifié. Si les éléments `Key` ne sont pas spécifiés pour un élément `Attribute` parent, les éléments `AttributeName` et `Name` spécifiés dans l'élément `Attribute` parent sont utilisés pour identifier le membre d'attribut à modifier.  
  
## <a name="see-also"></a>Voir aussi  
 [Attribut d’élément &#40;XMLA&#41;](attribute-element-xmla.md)   
 [Élément AttributeName &#40;XMLA&#41;](name-element-xmla.md)   
 [Élément DROP &#40;XMLA&#41;](../xml-elements-commands/drop-element-xmla.md)   
 [Insérer un élément &#40;XMLA&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [Élément KeyColumn &#40;ASSL&#41;](../../scripting/objects/column-element-assl.md)   
 [Mettre à jour d’élément &#40;XMLA&#41;](../xml-elements-commands/update-element-xmla.md)   
 [Où élément &#40;XMLA&#41;](where-element-xmla.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  

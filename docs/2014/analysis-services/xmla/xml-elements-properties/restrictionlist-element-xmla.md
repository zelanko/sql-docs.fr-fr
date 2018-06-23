---
title: Élément RestrictionList (XMLA) | Documents Microsoft
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
- RestrictionList Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#RestrictionList
- microsoft.xml.analysis.restrictionlist
- http://schemas.microsoft.com/analysisservices/2003/engine#RestrictionList
helpviewer_keywords:
- RestrictionList element
ms.assetid: 2297c005-381e-49a4-a207-826f7f9ea93a
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 081722ea3a5bf001b22f8c193cd5530a37809e15
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141034"
---
# <a name="restrictionlist-element-xmla"></a>Élément RestrictionList (XMLA)
  Contient une collection de colonnes et de valeurs de restriction utilisées par la méthode [Discover](../xml-elements-methods-discover.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Restrictions>  
   <RestrictionList>  
      <!-- Zero or more restriction columns and values -->  
   </RestrictionList>  
</Restrictions>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Restrictions](restrictions-element-xmla.md)|  
|Éléments enfants|Colonnes et valeurs de restriction (voir la section « Notes »).|  
  
## <a name="remarks"></a>Notes  
 L'élément `RestrictionList` contient une collection de colonnes de restriction sur lesquelles les données retournées par la méthode `Discover` peuvent être filtrées. Chaque colonne de restriction dans l'élément `RestrictionList` est définie par un élément XML distinct. La valeur de la colonne de restriction correspond aux données figurant dans l'élément XML et le nom de la colonne de restriction correspond au nom de l'élément XML.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
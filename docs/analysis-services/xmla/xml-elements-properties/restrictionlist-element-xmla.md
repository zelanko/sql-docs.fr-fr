---
title: "Élément RestrictionList (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- RestrictionList Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#RestrictionList
- microsoft.xml.analysis.restrictionlist
- http://schemas.microsoft.com/analysisservices/2003/engine#RestrictionList
helpviewer_keywords:
- RestrictionList element
ms.assetid: 2297c005-381e-49a4-a207-826f7f9ea93a
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: df82fa9bb12094ae01535977f10f26622cbac6b2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="restrictionlist-element-xmla"></a>Élément RestrictionList (XMLA)
  Contient une collection de colonnes et de valeurs de restriction utilisées par la méthode [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) .  
  
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
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Restrictions](../../../analysis-services/xmla/xml-elements-properties/restrictions-element-xmla.md)|  
|Éléments enfants|Colonnes et valeurs de restriction (voir la section « Notes »).|  
  
## <a name="remarks"></a>Notes  
 L'élément **RestrictionList** contient une collection de colonnes de restriction sur lesquelles les données retournées par la méthode **Discover** peuvent être filtrées. Chaque colonne de restriction dans l'élément **RestrictionList** est définie par un élément XML distinct. La valeur de la colonne de restriction correspond aux données figurant dans l'élément XML et le nom de la colonne de restriction correspond au nom de l'élément XML.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  


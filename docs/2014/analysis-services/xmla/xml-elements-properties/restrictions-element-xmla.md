---
title: Élément restrictions (XMLA) | Documents Microsoft
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
- Restrictions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Restrictions
- http://schemas.microsoft.com/analysisservices/2003/engine#Restrictions
- microsoft.xml.analysis.restrictions
helpviewer_keywords:
- Restrictions element
ms.assetid: e745ce13-b468-4372-a6f0-0da3d772dda3
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: a096ea973d6b8ba900c3b1d890f49ad019d8e93f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153108"
---
# <a name="restrictions-element-xmla"></a>Élément Restrictions (XMLA)
  Contient les colonnes de restriction et les données utilisées par le [Discover](../xml-elements-methods-discover.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<Discover>  
...  
   <Restrictions>  
      <RestrictionList>...</RestrictionList>  
   </Restrictions>  
...  
</Discover>  
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
|Éléments parents|[Découvrir](../xml-elements-methods-discover.md)|  
|Éléments enfants|[Liste de restrictions](restrictionlist-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 L'élément `Restrictions` représente les colonnes et les données de restriction utilisées pour limiter les informations récupérées par la méthode `Discover`.  
  
## <a name="example"></a>Exemple  
  
```  
<Discover xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <RequestType>DISCOVER_PROPERTIES</RequestType>  
   <Restrictions>  
      <RestrictionList xmlns="urn:schemas-microsoft-com:xml-analysis">  
         <PropertyName>Catalog</PropertyName>  
      </RestrictionList>  
   </Restrictions>  
   <Properties />  
</Discover>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
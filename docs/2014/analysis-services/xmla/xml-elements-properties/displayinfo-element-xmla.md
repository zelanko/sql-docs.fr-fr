---
title: Élément DisplayInfo (XMLA) | Documents Microsoft
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
- DisplayInfo Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.displayinfo
- http://schemas.microsoft.com/analysisservices/2003/engine#DisplayInfo
- urn:schemas-microsoft-com:xml-analysis#DisplayInfo
helpviewer_keywords:
- DisplayInfo element
ms.assetid: 059ce038-38de-4c7d-a72f-4f919cfc7c4a
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: e792ba01df58aacb42600fb9ff8ac686c026badc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039379"
---
# <a name="displayinfo-element-xmla"></a>Élément DisplayInfo (XMLA)
  Contient des informations d'affichage pour l'élément parent [HierarchyInfo](hierarchyinfo-element-xmla.md) ou [Member](member-element-xmla.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<HierarchyInfo> <!-- or Member -->  
   ...  
   <DisplayInfo>...</DisplayInfo>  
   ...  
</HierarchyInfo>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|UnsignedInt|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[HierarchyInfo](hierarchyinfo-element-xmla.md), [Member](member-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L'élément `DisplayInfo` contient différentes informations permettant à une application cliente de restituer l'élément parent `HierarchyInfo` ou `Member`. Sa valeur est équivalente à la propriété DISPLAY_INFO définie pour les ensembles de lignes d'axe dans la spécification OLE DB pour OLAP.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
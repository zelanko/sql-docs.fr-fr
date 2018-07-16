---
title: Cube, élément (XMLA) | Microsoft Docs
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
- Cube Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cube
- urn:schemas-microsoft-com:xml-analysis#Cube
- http://schemas.microsoft.com/analysisservices/2003/engine#Cube
helpviewer_keywords:
- Cube element
ms.assetid: 2e8662f4-fb2e-43af-b70a-9e0b5872c9b9
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e56bc3b206069265fe21329edf688dfae9254e2d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37228129"
---
# <a name="cube-element-xmla"></a>Élément Cube (XMLA)
  Identifie le cube qui contient la dimension représentée par le parent [objet](object-element-dimension-xmla.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Object>  
   ...  
   <Cube>...</Cube>  
   ...  
</Object>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Objet](object-element-dimension-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 L'élément `Cube` est un identificateur d'objet contenant le nom du cube qui contient la dimension représentée par l'élément `Object`.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément de base de données &#40;XMLA&#41;](database-element-xmla.md)   
 [Élément de la dimension &#40;XMLA&#41;](dimension-element-xmla.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  

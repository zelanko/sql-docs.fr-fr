---
title: Élément Locations (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Locations Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Locations
- urn:schemas-microsoft-com:xml-analysis#Locations
- microsoft.xml.analysis.locations
helpviewer_keywords:
- Locations element
ms.assetid: 630929cb-f0dc-472a-86bc-28b67e907c3d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9c48a9b3b4ee2d0c3aea1c1c1013651a434a2685
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48194999"
---
# <a name="locations-element-xmla"></a>Élément Locations (XMLA)
  Contient une collection d'éléments [Location](query-element-xmla.md) utilisée par la commande [Backup](../xml-elements-commands/backup-element-xmla.md), [Restore](../xml-elements-commands/restore-element-xmla.md) ou [Synchronize](../xml-elements-commands/synchronize-element-xmla.md) parente.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
< Backup> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Locations>  
      <Location>...</Location>  
   </Locations>  
   ...  
</Backup>  
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
|Éléments parents|[Backup](../xml-elements-commands/backup-element-xmla.md), [Restore](../xml-elements-commands/restore-element-xmla.md) , or [Synchronize](../xml-elements-commands/synchronize-element-xmla.md)|  
|Éléments enfants|[Emplacement](location-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  

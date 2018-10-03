---
title: Élément Folders (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Folders Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.folders
- http://schemas.microsoft.com/analysisservices/2003/engine#Folders
- urn:schemas-microsoft-com:xml-analysis#Folders
helpviewer_keywords:
- Folders element
ms.assetid: fefb0469-22ea-4804-8dc3-9c49825b32f1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8e8097a5499f1d8d34d9dd5dd53726bf02a4b098
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48174349"
---
# <a name="folders-element-xmla"></a>Élément Folders (XMLA)
  Contient une collection d'éléments [Folder](folder-element-xmla.md) utilisée par l'élément [Location](location-element-xmla.md) parent au cours d'une commande [Restore](../xml-elements-commands/restore-element-xmla.md) ou [Synchronize](../xml-elements-commands/synchronize-element-xmla.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Location>  
   ...  
   <Folders>  
      <Folder>...</Folder>  
   </Folders>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucun (collection)|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Emplacement](location-element-xmla.md)|  
|Éléments enfants|[Dossier](folder-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Élément Restore &#40;XMLA&#41;](../xml-elements-commands/restore-element-xmla.md)   
 [Élément Synchronize &#40;XMLA&#41;](../xml-elements-commands/synchronize-element-xmla.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  

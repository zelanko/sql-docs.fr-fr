---
title: "Élément Folders (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Folders Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.folders
- http://schemas.microsoft.com/analysisservices/2003/engine#Folders
- urn:schemas-microsoft-com:xml-analysis#Folders
helpviewer_keywords: Folders element
ms.assetid: fefb0469-22ea-4804-8dc3-9c49825b32f1
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 83571bacbbd3779909d79d3f327c4088b9222bb6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="folders-element-xmla"></a>Élément Folders (XMLA)
  Contient une collection d'éléments [Folder](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md) utilisée par l'élément [Location](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) parent au cours d'une commande [Restore](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) ou [Synchronize](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) .  
  
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
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Emplacement](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)|  
|Éléments enfants|[Dossier](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Restaurer l’élément &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Synchroniser, élément &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

---
title: "ID d’élément (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#ID
- urn:schemas-microsoft-com:xml-analysis#ID
- microsoft.xml.analysis.id
helpviewer_keywords:
- ID element
ms.assetid: f7d67599-6a70-4455-bfdb-1d127e5eff4e
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c7dcd7bd4904ae4cc3ae2b8a8e3345af52016563
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="id-element-xmla"></a>Élément ID (XMLA)
  Identifie un verrou sur lequel exécuter le parent [verrou](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md) ou [Unlock](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Lock> <!-- or Unlock>  
   ...  
   <ID>...</ID>  
   ...  
</Lock>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Verrou](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md), [déverrouiller](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le **ID** élément contient un identificateur global unique (GUID) utilisé pour identifier un verrou.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet, élément &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)   
 [Élément mode &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/mode-element-xmla.md)   
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  


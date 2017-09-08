---
title: "L’élément DataSourceID (XMLA) | Documents Microsoft"
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
- DataSourceID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.datasourceid
- urn:schemas-microsoft-com:xml-analysis#DataSourceID
- http://schemas.microsoft.com/analysisservices/2003/engine#DataSourceID
helpviewer_keywords:
- DataSourceID element
ms.assetid: 695522c7-acca-420a-a5fb-f01f3fd9a96b
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: eb3374f4a2bc9da44263ed65a4247903671e03dd
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="datasourceid-element-xmla"></a>Élément DataSourceID (XMLA)
  Identifie une source de données utilisée par un [emplacement](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) élément pendant une [sauvegarde](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [restaurer](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md), ou [synchroniser](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) commande.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Location>  
   ...  
   <DataSourceID>...</DataSourceID>  
   ...  
</Location>  
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
|Éléments parents|[Emplacement](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le **DataSourceID** élément contient le nom de la source de données sur l’instance source qui identifie l’instance distante sur laquelle les informations de partition distante doit être sauvegardée, restaurée ou synchronisés.  
  
 Pour plus d’informations sur la sauvegarde et restauration des partitions distantes, consultez [sauvegarde, restauration et synchroniser les bases de données &#40; XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Élément ConnectionString &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/connectionstring-element-xmla.md)   
 [Élément DataSourceType &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/datasourcetype-element-xmla.md)   
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

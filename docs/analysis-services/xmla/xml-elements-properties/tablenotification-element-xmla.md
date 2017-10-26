---
title: "Élément TableNotification (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- TableNotification Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#TableNotification
- microsoft.xml.analysis.tablenotification
- http://schemas.microsoft.com/analysisservices/2003/engine#TableNotification
helpviewer_keywords:
- TableNotification element
ms.assetid: 097b0d53-cb0b-4454-963f-60964fd429e0
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f123f9ca7efe5719ab2bb5f45dcbf6a7f5e0c02a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="tablenotification-element-xmla"></a>Élément TableNotification (XMLA)
  Représente une notification de table pour une commande [NotifyTableChange](../../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<TableNotifications>  
   ...  
   <TableNotification>  
      <DbSchemaName>...</DbSchemaName>  
      <DbTableName>...</DbTableName>  
   </TableNotification>  
   ...  
</TableNotifications>  
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
|Éléments parents|[TableNotifications](../../../analysis-services/xmla/xml-elements-properties/tablenotifications-element-xmla.md)|  
|Éléments enfants|[DbSchemaName](../../../analysis-services/xmla/xml-elements-properties/dbschemaname-element-xmla.md), [DbTableName](../../../analysis-services/xmla/xml-elements-properties/dbtablename-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  


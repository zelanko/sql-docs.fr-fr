---
title: Élément TableNotification (XMLA) | Documents Microsoft
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
- TableNotification Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#TableNotification
- microsoft.xml.analysis.tablenotification
- http://schemas.microsoft.com/analysisservices/2003/engine#TableNotification
helpviewer_keywords:
- TableNotification element
ms.assetid: 097b0d53-cb0b-4454-963f-60964fd429e0
caps.latest.revision: 10
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: fb0524d835c2ada3df0d92119d0510bb55181459
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040725"
---
# <a name="tablenotification-element-xmla"></a>Élément TableNotification (XMLA)
  Représente une notification de table pour une commande [NotifyTableChange](../xml-elements-commands/notifytablechange-element-xmla.md) .  
  
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
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[TableNotifications](tablenotifications-element-xmla.md)|  
|Éléments enfants|[DbSchemaName](name-element-xmla.md), [DbTableName](dbtablename-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
---
title: "Élément TableNotifications (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- TableNotifications Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#TableNotifications
- microsoft.xml.analysis.tablenotifications
- http://schemas.microsoft.com/analysisservices/2003/engine#TableNotifications
helpviewer_keywords:
- TableNotifications element
ms.assetid: 650f307d-1f11-47ce-9d0e-19cf3b1835b7
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 29c30984ad6e151976d50b0768dd0eda937d289f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="tablenotifications-element-xmla"></a>Élément TableNotifications (XMLA)
  Contient une collection d'éléments [TableNotification](../../../analysis-services/xmla/xml-elements-properties/tablenotification-element-xmla.md) utilisée par la commande [NotifyTableChange](../../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<NotifyTableChange >  
   ...  
   <TableNotifications>  
      <TableNotification>...</TableNotification>  
   </TableNotifications>  
   ...  
</NotifyTableChange>  
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
|Éléments parents|[NotifyTableChange](../../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md)|  
|Éléments enfants|[TableNotification](../../../analysis-services/xmla/xml-elements-properties/tablenotification-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  


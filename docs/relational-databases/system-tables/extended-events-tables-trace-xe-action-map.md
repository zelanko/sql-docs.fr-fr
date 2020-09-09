---
description: Tables d’événements étendus - trace_xe_action_map
title: trace_xe_action_map (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- trace_xe_action_map_TSQL
- trace_xe_action_map
dev_langs:
- TSQL
helpviewer_keywords:
- extended events [SQL Server], tables
- trace_xe_action_map
ms.assetid: 208a1413-ce7f-4521-b765-d74723627302
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5f3b742741d3add5b54c07d3cec4f47bbd919e2d
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89540396"
---
# <a name="extended-events-tables---trace_xe_action_map"></a>Tables d’événements étendus - trace_xe_action_map
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Contient une ligne pour chaque action Événements étendus mappée à un ID de colonne Trace SQL. Cette table est stockée dans la base de données Master, dans le schéma sys.  
  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|trace_column_id|**smallint**|ID de la colonne Trace SQL en cours de mappage.|  
|package_name|**nvarchar(60)**|Nom du package Événements étendus où réside l'action mappée.|  
|xe_action_name|**nvarchar(60)**|Nom de l'action Événements étendus mappée à la colonne Trace SQL.|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser la requête suivante pour identifier les actions Événements étendus qui sont équivalentes aux colonnes Trace SQL :  
  
```  
SELECT tc.name AS trace_column, am.package_name, am.xe_action_name  
FROM sys.trace_columns AS tc  
INNER JOIN sys.trace_xe_action_map AS am  
   ON tc.trace_column_id = am.trace_column_id  
```  
  
 Les colonnes Trace SQL qui ne sont pas mappées aux actions ne sont pas incluses dans la table.  
  
## <a name="see-also"></a>Voir aussi  
 [trace_xe_event_map &#40;Transact-SQL&#41;](../../relational-databases/system-tables/extended-events-tables-trace-xe-event-map.md)  
  
  

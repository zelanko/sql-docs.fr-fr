---
title: sys. server_event_session_events (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_event_session_events
- server_event_session_events_TSQL
- sys.server_event_session_events
- sys.server_event_session_events_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_event_session_events catalog view
- xe
ms.assetid: 75986e91-1fc7-4f14-98ac-4e90154a74db
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 08d902a7eb4d0db60d6fdf3289c972316f557205
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85664578"
---
# <a name="sysserver_event_session_events-transact-sql"></a>sys.server_event_session_events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Renvoie une ligne pour chaque événement d’une session d’événements.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|ID de la session d'événements. N'accepte pas la valeur NULL.|  
|event_id|**int**|ID de l'événement. Cet ID est unique au sein d'une session d'événements. N'accepte pas la valeur NULL.|  
|name|**sysname**|Nom de l’événement. N'accepte pas la valeur NULL.|  
|package|**sysname**|Nom du package d'événement qui contient l'événement. N'accepte pas la valeur NULL.|  
|module|**sysname**|Nom du module qui contient l'événement. N'accepte pas la valeur NULL.|  
|prédicat|**nvarchar (3000)**|Expression de prédicat qui est appliquée à l’événement. Autorise la valeur NULL.|  
|predicate_xml|**nvarchar (3000)**|Expression de prédicat XML qui est appliquée à l'événement. Autorise la valeur NULL.|  
  
## <a name="permissions"></a>Autorisations  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="remarks"></a>Remarques  
 Cette vue a les cardinalités de relation suivantes.  
  
||||  
|-|-|-|  
|À partir|À|Relation|  
|sys.server_event_session_events.event_session_id|sys. server_event_sessions. event_session_id|Plusieurs-à-un|  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Affichages catalogue des événements étendus &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)   
 [Événements étendus](../../relational-databases/extended-events/extended-events.md)  
  
  

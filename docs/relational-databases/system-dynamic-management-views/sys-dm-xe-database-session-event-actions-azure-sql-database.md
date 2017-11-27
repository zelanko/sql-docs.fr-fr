---
title: "Sys.dm_xe_database_session_event_actions (de base de données SQL Azure) | Documents Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: 
ms.prod_service: sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: dmv's
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 48519fd9-c7c2-434b-848d-ccbf41133fdd
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.openlocfilehash: 42ac4136c77b3ba00784276b12898f3d4e08d7f2
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmxedatabasesessioneventactions-azure-sql-database"></a>Sys.dm_xe_database_session_event_actions (de base de données SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Retourne des informations sur les actions de la session d'événements. Les actions sont exécutées lorsque les événements sont déclenchés. Cette vue de gestion totalise des statistiques sur le nombre d'exécutions d'une action et la durée totale de son exécution.  
  
||  
|-|  
|**S’applique aux**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 et toutes les futures versions.|  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary (8)**|Adresse mémoire de la session d'événements. N'accepte pas la valeur NULL.|  
|action_name|**nvarchar (60)**|Le nom de l’action. N'accepte pas la valeur NULL.|  
|action_package_guid|**uniqueidentifier**|GUID pour le package qui contient l'action. N'accepte pas la valeur NULL.|  
|event_name|**nvarchar (60)**|Nom de l'événement auquel est liée l'action. N'accepte pas la valeur NULL.|  
|event_package_guid|**uniqueidentifier**|GUID pour le package qui contient l'événement. N'accepte pas la valeur NULL.|  
  
## <a name="permissions"></a>Permissions  
 Nécessite l’autorisation VIEW DATABASE STATE.  
  
### <a name="relationship-cardinalities"></a>Cardinalités de la relation  
  
|De|Pour|Relation|  
|----------|--------|------------------|  
|Sys.dm_xe_database_session_event_actions.event_session_address|Sys.dm_xe_database_sessions.Address|Plusieurs-à-un|  
|Sys.dm_xe_database_session_event_actions.action_name<br /><br /> sys.dm_xe_session_event_actions.action_package_guid|sys.dm_xe_objects.name<br /><br /> Sys.dm_xe_database_session_events.event_package_guid|Plusieurs-à-un|  
|Sys.dm_xe_database_session_event_actions.EVENT_NAME<br /><br /> Sys.dm_xe_database_session_event_actions.event_package_guid|sys.dm_xe_objects.name<br /><br /> sys.dm_xe_objects.package_guid|Plusieurs-à-un|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../../relational-databases/extended-events/extended-events.md)  
  
  

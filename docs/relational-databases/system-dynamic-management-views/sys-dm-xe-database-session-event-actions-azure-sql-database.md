---
title: Sys.dm_xe_database_session_event_actions (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
ms.assetid: 48519fd9-c7c2-434b-848d-ccbf41133fdd
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 0516016ad04132cae3899811b8f20f7f43538d53
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56035880"
---
# <a name="sysdmxedatabasesessioneventactions-azure-sql-database"></a>sys.dm_xe_database_session_event_actions (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Retourne des informations sur les actions de la session d'événements. Les actions sont exécutées lorsque les événements sont déclenchés. Cette vue de gestion totalise des statistiques sur le nombre d'exécutions d'une action et la durée totale de son exécution.  
  
||  
|-|  
|**S’applique à** : [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 et toutes les futures versions.|  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|Adresse mémoire de la session d'événements. N'accepte pas la valeur NULL.|  
|action_name|**nvarchar(60)**|Le nom de l’action. N'accepte pas la valeur NULL.|  
|action_package_guid|**uniqueidentifier**|GUID pour le package qui contient l'action. N'accepte pas la valeur NULL.|  
|event_name|**nvarchar(60)**|Nom de l'événement auquel est liée l'action. N'accepte pas la valeur NULL.|  
|event_package_guid|**uniqueidentifier**|GUID pour le package qui contient l'événement. N'accepte pas la valeur NULL.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’autorisation VIEW DATABASE STATE.  
  
### <a name="relationship-cardinalities"></a>Cardinalités de la relation  
  
|From|Pour|Relation|  
|----------|--------|------------------|  
|sys.dm_xe_database_session_event_actions.event_session_address|sys.dm_xe_database_sessions.address|Plusieurs-à-un|  
|sys.dm_xe_database_session_event_actions.action_name<br /><br /> sys.dm_xe_session_event_actions.action_package_guid|sys.dm_xe_objects.name<br /><br /> sys.dm_xe_database_session_events.event_package_guid|Plusieurs-à-un|  
|sys.dm_xe_database_session_event_actions.event_name<br /><br /> sys.dm_xe_database_session_event_actions.event_package_guid|sys.dm_xe_objects.name<br /><br /> sys.dm_xe_objects.package_guid|Plusieurs-à-un|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../../relational-databases/extended-events/extended-events.md)  
  
  

---
title: "Sys.database_event_session_fields (de base de données SQL Azure) | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.reviewer: 
ms.service: 
ms.component: system-catalog-views
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: Azure SQL Database
ms.assetid: 9b5c94d6-612c-4e0f-976d-ac6ba55da3ac
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 16d550e1a453b921eb0768ab758557192e9f0e16
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdatabaseeventsessionfields-azure-sql-database"></a>Sys.database_event_session_fields (de base de données SQL Azure)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque colonne personnalisable définie explicitement sur les événements et les cibles.  
  
||  
|-|  
|**S’applique aux**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 et les versions ultérieures.|  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|ID de la session d'événements. N'accepte pas la valeur NULL.|  
|object_id|**int**|ID de l'objet auquel est associé ce champ. N'accepte pas la valeur NULL.|  
|name|**sysname**|Le nom du champ. N'accepte pas la valeur NULL.|  
|valeur|**sql_variant**|La valeur du champ. N'accepte pas la valeur NULL.|  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation VIEW DATABASE STATE sur le serveur.  
  
## <a name="remarks"></a>Notes  
 Cette vue a les cardinalités de relation suivantes.  
  
||||  
|-|-|-|  
|De|Pour|Relation|  
|Sys.database_event_session_actions.event_session_id|Sys.database_event_sessions.event_session_id|Plusieurs-à-un|  
|Sys.database_event_session_actions.event_id<br /><br /> Sys.database_event_session_actions.object_id<br /><br /> Sys.database_event_session_actions.event_session_id|Sys.database_event_session_events.event_session_id<br /><br /> Sys.database_event_session_events.event_id|Plusieurs-à-un|  
|Sys.database_event_session_actions.event_session_id<br /><br /> Sys.database_event_session_actions.object_id|Sys.database_event_session_targets.event_session_id<br /><br /> Sys.database_event_session_targets.target_id|Plusieurs-à-un|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../../relational-databases/extended-events/extended-events.md)  
  
  

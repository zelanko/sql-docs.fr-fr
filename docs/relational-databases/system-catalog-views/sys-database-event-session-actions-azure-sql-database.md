---
title: "Sys.database_event_session_actions (de base de données SQL Azure) | Documents Microsoft"
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
ms.assetid: 32494df1-7ab7-4b88-a858-6b1021d67433
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 594515b901a0b8c284ef81fd5a426094e17a74d4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdatabaseeventsessionactions-azure-sql-database"></a>Sys.database_event_session_actions (de base de données SQL Azure)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque action d'un événement d'une session d'événements.  
  
||  
|-|  
|**S’applique aux**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 et les versions ultérieures.|  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|ID de la session d'événements. N'accepte pas la valeur NULL.|  
|event_id|**int**|ID de l'événement. Cet ID est unique dans l'objet de la session d'événements. N'accepte pas la valeur NULL.|  
|name|**sysname**|Le nom de l’action. Autorise la valeur NULL.|  
|package|**sysname**|Nom du package d'événement qui contient l'événement. Autorise la valeur NULL.|  
|module|**sysname**|Nom du module qui contient l'événement. Autorise la valeur NULL.|  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation VIEW DATABASE STATE sur le serveur.  
  
## <a name="remarks"></a>Notes  
 Cette vue a les cardinalités de relation suivantes.  
  
||||  
|-|-|-|  
|De|Pour|Relation|  
|Sys.database_event_session_actions.event_session_id|Sys.sys.database_event_sessions.event_session_id|Plusieurs-à-un|  
|Sys.database_event_session_actions.event_id<br /><br /> Sys.database_event_session_actions.event_session_id|Sys.database_event_session_events.event_session_id<br /><br /> Sys.database_event_session_events.event_id|Plusieurs-à-un|  
  
  

---
title: sys. dm_exec_session_wait_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_session_wait_stats
- sys.dm_exec_session_wait_stats_tsql
- dm_exec_session_wait_stats
- dm_exec_session_wait_stats_tsql
helpviewer_keywords:
- sys.dm_exec_session_wait_stats
ms.assetid: df84842a-71eb-4fda-b448-5953cf9985dc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6fc51bec78cf01522e6731648bdb7870ea7d9fb0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73982612"
---
# <a name="sysdm_exec_session_wait_stats-transact-sql"></a>sys. dm_exec_session_wait_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Retourne des informations sur toutes les attentes rencontrées par les threads qui ont été exécutés pour chaque session. Vous pouvez utiliser cette vue pour diagnostiquer les problèmes de performance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] liés à la session et à des requêtes et des lots spécifiques.  Cette vue retourne les mêmes informations que celles regroupées pour [sys. dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md) , mais fournit également le numéro de **session_id** .  
  
**S’applique à** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] (et versions ultérieures).  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|session_id|**smallint**|ID de la session.|  
|wait_type|**nvarchar (60)**|Nom du type d’attente. Pour plus d’informations, consultez [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md).|  
|waiting_tasks_count|**bigint**|Nombre d'attentes sur ce type d'attente. Ce compteur est incrémenté au début de chaque attente.|  
|wait_time_ms|**bigint**|Temps d'attente total en millisecondes pour ce type d'attente. Ce temps comprend signal_wait_time_ms.|  
|max_wait_time_ms|**bigint**|Temps d'attente maximal sur ce type d'attente.|  
|signal_wait_time_ms|**bigint**|Différence entre le moment où le thread qui attend a été signalé et le moment où il a commencé à s'exécuter.|  
  
## <a name="remarks"></a>Notes  
 Cette vue de gestion dynamique réinitialise les informations pour une session lorsque la session est ouverte, ou lorsque la session est réinitialisée (si le regroupement de connexions est en cours).  
  
 Pour plus d’informations sur les types d’attente, consultez [sys. dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md).  
  
## <a name="permissions"></a>Autorisations  
 Si l’utilisateur dispose de l’autorisation **View Server State** sur le serveur, il voit toutes les sessions en cours d’exécution sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]l’instance de ; dans le cas contraire, l’utilisateur verra uniquement la session active.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [SQL Server vues de gestion dynamique liées au système d’exploitation &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)  
 

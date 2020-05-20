---
title: sys. dm_resource_governor_workload_groups (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_workload_groups
- sys.dm_resource_governor_workload_groups_TSQL
- dm_resource_governor_workload_groups
- dm_resource_governor_workload_groups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_resource_governor_workload_groups dynamic management view
ms.assetid: f63c4914-1272-43ef-b135-fe1aabd953e0
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5dcd93a0c74d8fc12af14809c8ca66bf59275dee
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82821049"
---
# <a name="sysdm_resource_governor_workload_groups-transact-sql"></a>sys.dm_resource_governor_workload_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne les statistiques de groupe de charges de travail et la configuration en mémoire actuelle du groupe de charges de travail. Cette vue peut être jointe avec sys.dm_resource_governor_resource_pools pour obtenir le nom de pool de ressources.  
  
> [!NOTE]  
>  Pour appeler cette valeur à partir de [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] , utilisez le nom **sys. dm_pdw_nodes_resource_governor_workload_groups**.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|group_id|**int**|ID du groupe de charges de travail. N'accepte pas la valeur NULL.|  
|name|**sysname**|Nom du groupe de charges de travail. N'accepte pas la valeur NULL.|  
|pool_id|**int**|ID du pool de ressources. N'accepte pas la valeur NULL.|  
|external_pool_id|**int**|**S’applique à** : [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] et versions ultérieures.<br /><br /> ID du pool de ressources externes. N'accepte pas la valeur NULL.|  
|statistics_start_time|**datetime**|Heure à laquelle la collection de statistiques a été réinitialisée pour le groupe de charges de travail. N'accepte pas la valeur NULL.|  
|total_request_count|**bigint**|Nombre cumulatif de demandes traitées dans le groupe de charges de travail. N'accepte pas la valeur NULL.|  
|total_queued_request_count|**bigint**|Nombre cumulatif de demandes mises en file d'attente une fois la limite GROUP_MAX_REQUESTS atteinte. N'accepte pas la valeur NULL.|  
|active_request_count|**int**|Nombre de demandes en cours. N'accepte pas la valeur NULL.|  
|queued_request_count|**int**|Nombre actuel de demandes en attente. N'accepte pas la valeur NULL.|  
|total_cpu_limit_violation_count|**bigint**|Nombre cumulatif de demandes dépassant la limite de l'UC. N'accepte pas la valeur NULL.|  
|total_cpu_usage_ms|**bigint**|Utilisation cumulative de l'UC, en millisecondes, par ce groupe de charges de travail. N'accepte pas la valeur NULL.|  
|max_request_cpu_time_ms|**bigint**|Utilisation maximale de l'UC, en millisecondes, pour une demande unique. N'accepte pas la valeur NULL.<br /><br /> **Remarque :** Il s’agit d’une valeur mesurée, contrairement à request_max_cpu_time_sec, qui est un paramètre configurable. Pour plus d’informations, consultez [Classe d’événements CPU Threshold Exceeded](../../relational-databases/event-classes/cpu-threshold-exceeded-event-class.md).|  
|blocked_task_count|**int**|Nombre actuel de tâches bloquées. N'accepte pas la valeur NULL.|  
|total_lock_wait_count|**bigint**|Nombre cumulatif d'attentes de verrou qui se sont produites. N'accepte pas la valeur NULL.|  
|total_lock_wait_time_ms|**bigint**|Somme cumulative du temps écoulé, en millisecondes, du maintien d'un verrou. N'accepte pas la valeur NULL.|  
|total_query_optimization_count|**bigint**|Nombre cumulatif d'optimisations de requête dans ce groupe de charges de travail. N'accepte pas la valeur NULL.|  
|total_suboptimal_plan_generation_count|**bigint**|Nombre cumulatif de générations de plans non optimaux qui se sont produites dans ce groupe de charges de travail en raison de la sollicitation de la mémoire. N'accepte pas la valeur NULL.|  
|total_reduced_memgrant_count|**bigint**|Nombre cumulatif d'allocations de mémoire qui ont atteint la limite de taille de requête maximale. N'accepte pas la valeur NULL.|  
|max_request_grant_memory_kb|**bigint**|Taille maximale d'allocation de mémoire, en kilo-octets, d'une demande unique depuis que les statistiques ont été réinitialisées. N'accepte pas la valeur NULL.|  
|active_parallel_thread_count|**bigint**|Nombre actuel d’utilisations de threads parallèles. N'accepte pas la valeur NULL.|  
|importance|**sysname**|Valeur de configuration actuelle de l'importance relative d'une demande dans ce groupe de charges de travail. L’importance est l’un des éléments suivants, avec la valeur par défaut moyenne : faible, moyenne ou élevée.<br /><br /> N'accepte pas la valeur NULL.|  
|request_max_memory_grant_percent|**int**|Paramètre actuel de l'allocation de mémoire maximale, en pourcentage, pour une demande unique. N'accepte pas la valeur NULL.|  
|request_max_cpu_time_sec|**int**|Paramètre actuel de la limite maximale d'utilisation de l'UC, en secondes, pour une demande unique. N'accepte pas la valeur NULL.|  
|request_memory_grant_timeout_sec|**int**|Paramètre actuel du délai d'attente d'allocation de mémoire, en secondes, pour une demande unique. N'accepte pas la valeur NULL.|  
|group_max_requests|**int**|Paramètre actuel du nombre maximal de demandes simultanées. N'accepte pas la valeur NULL.|  
|max_dop|**int**|Degré maximal de parallélisme pour le groupe de charges de travail. La valeur par défaut 0 utilise des paramètres globaux. N'accepte pas la valeur NULL.|  
|pdw_node_id|**int**|**S’applique à**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ,[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Identificateur du nœud sur lequel cette distribution se trouve.|  
  
## <a name="remarks"></a>Notes  
 Cette vue de gestion dynamique montre la configuration en mémoire. Pour consulter les métadonnées de configuration stockées, utilisez l'affichage catalogue sys.resource_governor_workload_groups.  
  
 Lorsque l’instruction ALTER RESOURCE GOVERNOR RESET STATISTICs est exécutée avec succès, les compteurs suivants sont réinitialisés : statistics_start_time, total_request_count, total_queued_request_count, total_cpu_limit_violation_count, total_cpu_usage_ms, max_request_cpu_time_ms, total_lock_wait_count, total_lock_wait_time_ms, total_query_optimization_count, total_suboptimal_plan_generation_count, total_reduced_memgrant_count et max_request_grant_memory_kb. statistics_start_time est défini sur la date et l’heure système actuelles, les autres compteurs ont la valeur zéro (0).  
  
## <a name="permissions"></a>Autorisations  
 Requiert l'autorisation VIEW SERVER STATE.  
  
## <a name="see-also"></a>Voir aussi  
 [Vues et fonctions de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys. dm_resource_governor_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)   
 [sys. resource_governor_workload_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-workload-groups-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  




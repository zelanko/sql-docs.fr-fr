---
title: Sys.dm_resource_governor_workload_groups_history_ex (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_workload_groups_history_ex_TSQL
- sys.dm_resource_governor_workload_groups_history_ex
- dm_resource_governor_workload_groups_history_ex
- dm_resource_governor_workload_groups_history_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_resource_governor_workload_groups_history_ex dynamic management view
author: joesackmsft
ms.author: josack
manager: craigg
ms.openlocfilehash: 1a2123c3da5945fb42184631e43fe27d83972375
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66744023"
---
# <a name="sysdmresourcegovernorworkloadgroupshistoryex-azure-sql-database"></a>sys.dm_resource_governor_workload_groups_history_ex (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Statistiques des pools d’instantané renvoie à des intervalles de 15 secondes pour les 30 dernières minutes de ressource pour une base de données SQL Azure.
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**pool_id**| INT |ID du pool de ressources. N'accepte pas la valeur NULL.|
|**group_id**| INT |ID du groupe de charges de travail. N'accepte pas la valeur NULL.|
|**nom**| nvarchar (256) |Nom du groupe de charges de travail. N'accepte pas la valeur NULL.|
|**snapshot_time**| datetime |Date et heure de l’instantané de statistiques de groupe de ressources réalisé.|
|**duration_ms**| INT |Durée entre l’instantané actuel et précédente.|
|**active_worker_count**| INT |Nombre total de workers dans l’instantané actuel.|
|**active_request_count**| INT |Nombre de demandes en cours. N'accepte pas la valeur NULL.|
|**active_session_count**| INT |Total des sessions actives dans l’instantané actuel.|
|**total_request_count**| BIGINT |Nombre cumulatif de demandes traitées dans le groupe de charges de travail. N'accepte pas la valeur NULL.|
|**delta_request_count**| INT |Nombre de demandes traitées dans le groupe de charge de travail depuis la dernière capture instantanée. N'accepte pas la valeur NULL.|
|**total_cpu_usage_ms**| BIGINT |Utilisation cumulative de l'UC, en millisecondes, par ce groupe de charges de travail. N'accepte pas la valeur NULL.|
|**delta_cpu_usage_ms**| INT |Utilisation de l’UC en millisecondes depuis la dernière capture instantanée. N'accepte pas la valeur NULL.|
|**delta_cpu_usage_preemptive_ms**| INT |Appels win32 PreEmptive ne régissent pas par RG de processeur SQL, depuis la dernière capture instantanée.|
|**delta_reads_reduced_memgrant_count**| INT |Le nombre d’allocations de mémoire qui a atteint la limite de taille maximale des requêtes depuis la dernière capture instantanée. N'accepte pas la valeur NULL.|
|**reads_throttled**| INT |Nombre total de lectures limitées.|
|**delta_reads_queued**| INT |Le total de sorties de lecture empilées depuis la dernière capture instantanée. Autorise la valeur NULL. Null si le groupe de ressources n’est pas régi pour les e/s.|
|**delta_reads_issued**| INT |Le total de sorties de lecture émises depuis la dernière capture instantanée. Autorise la valeur NULL. Null si le groupe de ressources n’est pas régi pour les e/s.|
|**delta_reads_completed**| INT |Le total de sorties de lecture terminées depuis la dernière capture instantanée. N'accepte pas la valeur NULL.|
|**delta_read_bytes**| BIGINT |Nombre total d’octets lus depuis la dernière capture instantanée. N'accepte pas la valeur NULL.|
|**delta_read_stall_ms**| INT |Durée totale (en millisecondes) entre l’arrivée d’e/s en lecture et l’achèvement depuis la dernière capture instantanée. N'accepte pas la valeur NULL.|
|**delta_read_stall_queued_ms**| INT |Durée totale (en millisecondes) entre la lecture d’arrivée des e/s et problème depuis la dernière capture instantanée. Autorise la valeur NULL. Null si le groupe de ressources n’est pas régi pour les e/s. Valeur différente de zéro delta_read_stall_queued_ms signifie qu'e/s est affectée par RG.|
|**delta_writes_queued**| INT |Le total de sorties d’écriture empilées depuis la dernière capture instantanée. Autorise la valeur NULL. Null si le groupe de ressources n’est pas régi pour les e/s.|
|**delta_writes_issued**| INT |Le total de sorties d’écriture émises depuis la dernière capture instantanée. Autorise la valeur NULL. Null si le groupe de ressources n’est pas régi pour les e/s.|
|**delta_writes_completed**| INT |Le total de sorties d’écriture terminées depuis la dernière capture instantanée. N'accepte pas la valeur NULL.|
|**delta_writes_bytes**| BIGINT |Le nombre total d’octets écrits depuis la dernière capture instantanée. N'accepte pas la valeur NULL.|
|**delta_write_stall_ms**| INT |Durée totale (en millisecondes) entre l’arrivée de d’e/s d’écriture et de saisie semi-automatique depuis la dernière capture instantanée. N'accepte pas la valeur NULL.|
|**delta_background_writes**| INT |Le Nb total d’écritures effectué par les tâches en arrière-plan depuis la dernière capture instantanée.|
|**delta_background_write_bytes**| BIGINT |La taille totale d’écriture effectuée par les tâches en arrière-plan depuis la dernière capture instantanée, en octets.|
|**delta_log_bytes_used**| BIGINT |Journal utilisé depuis la dernière capture instantanée en octets.|
|**delta_log_temp_db_bytes_used**| BIGINT |Utilisé depuis la dernière capture instantanée en octets du journal tempdb.|
|**delta_query_optimizations**| BIGINT |Le nombre d’optimisations de requêtes dans ce groupe de charge de travail depuis la dernière capture instantanée. N'accepte pas la valeur NULL.|
|**delta_suboptimal_plan_generations**| BIGINT |Le nombre de générations de plan non optimal qui se sont produites dans ce groupe de charge de travail en raison d’une sollicitation de la mémoire depuis la dernière capture instantanée. N'accepte pas la valeur NULL.
|**max_memory_grant_kb**| BIGINT |Allocation de la mémoire maximale pour le groupe dans la base de connaissances.|
|**max_request_cpu_msec**| BIGINT |Utilisation maximale de l'UC, en millisecondes, pour une demande unique. N'accepte pas la valeur NULL.|
|**max_concurrent_request**| INT |Paramètre actuel du nombre maximal de demandes simultanées. N'accepte pas la valeur NULL.|
|**max_io**| INT |Limite d’e/s maximale pour le groupe.|
|**max_global_io**| INT |Identifié à titre d'information uniquement. Non pris en charge. La compatibilité future n'est pas garantie.
|**max_queued_io**| INT |Identifié à titre d'information uniquement. Non pris en charge. La compatibilité future n'est pas garantie.|
|**max_log_rate_kb**| BIGINT |Taux de journal maximal (en kilo-octets par seconde) au niveau de groupe de ressources.|
|**max_session**| INT |Limite de session pour le groupe.|
|**max_worker**| INT |Limite de travail pour le groupe.|
|||

## <a name="permissions"></a>Autorisations

Cette vue nécessite l’autorisation VIEW SERVER STATE.

## <a name="remarks"></a>Notes

Les utilisateurs peuvent accéder à cette vue de gestion dynamique pour surveiller de près de la consommation des ressources en temps réel pour le pool de charge de travail utilisateur, ainsi que des pools internes du système de l’instance de base de données SQL Azure.

> [!IMPORTANT]
> La plupart des données signalées par cette DMV est prévu pour une utilisation interne et est susceptible de changer.

## <a name="examples"></a>Exemples

L’exemple suivant retourne les données de taux de journal maximale et la consommation à chaque instantané par pool d’utilisateur :

```sql
SELECT snapshot_time,
       name,
       max_log_rate_kb,
       delta_log_bytes_used
FROM sys.dm_resource_governor_workload_groups_history_ex
WHERE name LIKE 'User%'
ORDER BY snapshot_time DESC;
```

## <a name="see-also"></a>Voir aussi

- [Gouvernance de taux de journal de traduction](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits-database-server#transaction-log-rate-governance)
- [Limites de ressources DTU de pool élastique](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits-elastic-pools)
- [Limites de ressources de pool élastique vCore](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-elastic-pools)

---
title: Sys.dm_exec_procedure_stats (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_procedure_stats_TSQL
- dm_exec_procedure_stats_TSQL
- dm_exec_procedure_stats
- sys.dm_exec_procedure_stats
dev_langs: TSQL
helpviewer_keywords: sys.dm_exec_procedure_stats dynamic management view
ms.assetid: ab8ddde8-1cea-4b41-a7e4-697e6ddd785a
caps.latest.revision: "24"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: f935b0e9a4c150830a03ecb2ea1f67a4cd270d3f
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmexecprocedurestats-transact-sql"></a>sys.dm_exec_procedure_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne les statistiques sur les performances des agrégats pour les procédures stockées mises en cache. La vue retourne une ligne pour chaque plan de procédure stockée mise en cache et la durée de vie de la ligne correspond à celle pendant laquelle la procédure stockée reste mise en cache. Lorsqu'une procédure stockée est supprimée du cache, la ligne correspondante est éliminée de cette vue. À ce stade, un événement de trace SQL de statistiques de performances est déclenché comme **sys.dm_exec_query_stats**.  
  
 Dans [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], les vues de gestion dynamique ne peuvent pas exposer des informations qui ont un impact sur la relation contenant-contenu de la base de données, ou exposer des informations concernant d'autres bases de données auxquelles l'utilisateur a accès. Pour éviter d'exposer ces informations, chaque ligne contenant des données qui n'appartient pas au locataire connecté est filtrée.  
  
> **Remarque :** une requête initiale de **sys.dm_exec_procedure_stats** peut produire des résultats inexacts s’il existe une charge de travail en cours d’exécution sur le serveur. Des résultats plus précis peuvent être déterminés en réexécutant la requête.  
  
> **Remarque pour l’entrepôt de données SQL Azure** Pour appeler cette de [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilisez le nom **sys.dm_pdw_nodes_exec_procedure_stats**.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|ID de base de données dans lequel réside la procédure stockée.|  
|**object_id**|**int**|Numéro d'identification d'objet de la procédure stockée.|  
|**type**|**char(2)**|Type de l'objet :<br /><br /> P = procédure stockée SQL<br /><br /> PC = Procédure stockée d'assembly (CLR)<br /><br /> X = Procédure stockée étendue|  
|**type_desc**|**nvarchar (60)**|Description du type d'objet :<br /><br /> SQL_STORED_PROCEDURE<br /><br /> CLR_STORED_PROCEDURE<br /><br /> EXTENDED_STORED_PROCEDURE|  
|**sql_handle**|**varbinary(64)**|Il peut servir à mettre en corrélation avec des requêtes de **sys.dm_exec_query_stats** qui ont été exécutées à partir de cette procédure stockée.|  
|**plan_handle**|**varbinary(64)**|Identificateur du plan en mémoire. Cet identificateur est temporaire et il reste constant uniquement tant que le plan est dans le cache. Cette valeur peut être utilisée avec la **sys.dm_exec_cached_plans** vue de gestion dynamique.<br /><br /> Sa valeur est toujours 0x000 lorsqu'une procédure stockée compilée en mode natif interroge une table optimisée en mémoire.|  
|**cached_time**|**datetime**|Heure à laquelle la procédure stockée a été ajoutée au cache.|  
|**last_execution_time**|**datetime**|Heure de dernière exécution de la procédure stockée.|  
|**execution_count**|**bigint**|Nombre d'exécutions de la procédure stockée depuis sa dernière compilation.|  
|**total_worker_time**|**bigint**|Temps processeur total, en microsecondes, consommé par les exécutions de cette procédure stockée depuis sa compilation.<br /><br /> Pour les procédures stockées compilées en mode natif, **total_worker_time** peut être inexact si plusieurs exécutions sont réalisées en moins d’une milliseconde.|  
|**last_worker_time**|**bigint**|Temps processeur, en microsecondes, consommé lors de la dernière exécution de la procédure stockée. <sup>1</sup>|  
|**min_worker_time**|**bigint**|Temps processeur minimal, en microsecondes, consommé par cette procédure stockée lors d'une seule exécution. <sup>1</sup>|  
|**max_worker_time**|**bigint**|Temps processeur maximal, en microsecondes, consommé par cette procédure stockée lors d'une seule exécution. <sup>1</sup>|  
|**total_physical_reads**|**bigint**|Nombre total de lectures physiques effectuées par les exécutions de cette procédure stockée depuis sa compilation.<br /><br /> Sa valeur est toujours 0 lors de l'interrogation d'une table optimisée en mémoire.|  
|**last_physical_reads**|**bigint**|Nombre de lectures physiques effectuées lors de la dernière exécution de la procédure stockée.<br /><br /> Sa valeur est toujours 0 lors de l'interrogation d'une table optimisée en mémoire.|  
|**min_physical_reads**|**bigint**|Nombre minimal de lectures physiques effectuées par cette procédure stockée lors d'une seule exécution.<br /><br /> Sa valeur est toujours 0 lors de l'interrogation d'une table optimisée en mémoire.|  
|**max_physical_reads**|**bigint**|Nombre maximal de lectures physiques effectuées par cette procédure stockée lors d'une seule exécution.<br /><br /> Sa valeur est toujours 0 lors de l'interrogation d'une table optimisée en mémoire.|  
|**total_logical_writes**|**bigint**|Nombre total d'écritures logiques effectuées par les exécutions de cette procédure stockée depuis sa compilation.<br /><br /> Sa valeur est toujours 0 lors de l'interrogation d'une table optimisée en mémoire.|  
|**last_logical_writes**|**bigint**|Numéro du nombre de pages du pool de mémoires tampons modifiées lors de la dernière exécution du plan. Si une page est déjà modifiée, aucune écriture n'est comptée.<br /><br /> Sa valeur est toujours 0 lors de l'interrogation d'une table optimisée en mémoire.|  
|**min_logical_writes**|**bigint**|Nombre minimal d'écritures logiques effectuées par cette procédure stockée lors d'une seule exécution.<br /><br /> Sa valeur est toujours 0 lors de l'interrogation d'une table optimisée en mémoire.|  
|**max_logical_writes**|**bigint**|Nombre maximal d'écritures logiques effectuées par cette procédure stockée lors d'une seule exécution.<br /><br /> Sa valeur est toujours 0 lors de l'interrogation d'une table optimisée en mémoire.|  
|**total_logical_reads**|**bigint**|Nombre total de lectures logiques effectuées par les exécutions de cette procédure stockée depuis sa compilation.<br /><br /> Sa valeur est toujours 0 lors de l'interrogation d'une table optimisée en mémoire.|  
|**last_logical_reads**|**bigint**|Nombre de lectures logiques effectuées lors de la dernière exécution de la procédure stockée.<br /><br /> Sa valeur est toujours 0 lors de l'interrogation d'une table optimisée en mémoire.|  
|**min_logical_reads**|**bigint**|Nombre minimal de lectures logiques effectuées par cette procédure stockée lors d'une seule exécution.<br /><br /> Sa valeur est toujours 0 lors de l'interrogation d'une table optimisée en mémoire.|  
|**max_logical_reads**|**bigint**|Nombre maximal de lectures logiques effectuées par cette procédure stockée lors d'une seule exécution.<br /><br /> Sa valeur est toujours 0 lors de l'interrogation d'une table optimisée en mémoire.|  
|**total_elapsed_time**|**bigint**|Temps total écoulé, en microsecondes, pour les exécutions de cette procédure stockée.|  
|**last_elapsed_time**|**bigint**|Temps écoulé, en microsecondes, pour la dernière exécution de cette procédure stockée.|  
|**min_elapsed_time**|**bigint**|Temps minimal écoulé, en microsecondes, pour les différentes exécutions de cette procédure stockée.|  
|**max_elapsed_time**|**bigint**|Temps maximal écoulé, en microsecondes, pour les différentes exécutions de cette procédure stockée.|  
|**pdw_node_id**|**int**|**S’applique aux**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L’identificateur du nœud qui se trouve sur cette distribution.|  
  
 <sup>1</sup> des procédures stockées compilées en mode natif lors de la collecte de statistiques est activée, des temps de travail est collecté en millisecondes. Si la requête s'exécute en moins d'une milliseconde, la valeur est 0.  
  
## <a name="permissions"></a>Permissions  
Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] niveaux Premium, nécessite le `VIEW DATABASE STATE` autorisation dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard et les niveaux de base, nécessite le **administrateur du serveur** ou **administrateur Active Directory de Azure** compte. 
  
## <a name="remarks"></a>Notes  
 Les statistiques de la vue sont mises à jour lorsqu'une exécution de procédure stockée se termine.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne des informations sur les dix principales procédures stockées identifiées d'après le temps moyen écoulé.  
  
```  
SELECT TOP 10 d.object_id, d.database_id, OBJECT_NAME(object_id, database_id) 'proc name',   
    d.cached_time, d.last_execution_time, d.total_elapsed_time,  
    d.total_elapsed_time/d.execution_count AS [avg_elapsed_time],  
    d.last_elapsed_time, d.execution_count  
FROM sys.dm_exec_procedure_stats AS d  
ORDER BY [total_worker_time] DESC;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Les fonctions et vues de gestion dynamique &#40; liées à l’exécution Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Sys.dm_exec_sql_text &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
 [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
 
 [Sys.dm_exec_trigger_stats &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)  
  
  



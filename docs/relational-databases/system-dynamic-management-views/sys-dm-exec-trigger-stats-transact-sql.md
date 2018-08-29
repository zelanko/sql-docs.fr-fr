---
title: Sys.dm_exec_trigger_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/10/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_exec_trigger_stats
- dm_exec_trigger_stats_TSQL
- sys.dm_exec_trigger_stats_TSQL
- sys.dm_exec_trigger_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_trigger_stats dynamic management function
ms.assetid: 863498b4-849c-434d-b748-837411458738
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e4fafc4fb5f082c5be3c3c66537a5ff6d8e7d0f7
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43085760"
---
# <a name="sysdmexectriggerstats-transact-sql"></a>sys.dm_exec_trigger_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne les statistiques sur les performances des agrégats pour les déclencheurs mis en cache. La vue contient une ligne par déclencheur, et la durée de vie de la ligne correspond à celle pendant laquelle le déclencheur reste mis en cache. Lorsqu'un déclencheur est supprimé du cache, la ligne correspondante est éliminée de cette vue. À ce stade, un événement de trace SQL de statistiques de performances est déclenché similaire à **sys.dm_exec_query_stats**.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**Int**|ID de base de données dans lequel réside le déclencheur.|  
|**object_id**|**Int**|Numéro d'identification d'objet du déclencheur.|  
|**type**|**char(2)**|Type de l'objet :<br /><br /> TA = Déclencheur assembly (CLR)<br /><br /> TR = Déclencheur SQL|  
|**Type_desc**|**nvarchar(60)**|Description du type d'objet :<br /><br /> CLR_TRIGGER<br /><br /> SQL_TRIGGER|  
|**sql_handle**|**varbinary(64)**|Cela peut être utilisé pour mettre en corrélation avec des requêtes de **sys.dm_exec_query_stats** qui ont été exécutées à partir de ce déclencheur.|  
|**plan_handle**|**varbinary(64)**|Identificateur du plan en mémoire. Cet identificateur est temporaire et il reste constant uniquement tant que le plan est dans le cache. Cette valeur peut être utilisée avec le **sys.dm_exec_cached_plans** vue de gestion dynamique.|  
|**cached_time**|**datetime**|Heure à laquelle le déclencheur a été ajouté au cache.|  
|**last_execution_time**|**datetime**|Heure de dernière exécution du déclencheur.|  
|**execution_count**|**bigint**|Le nombre de fois où le déclencheur a été exécuté depuis sa dernière compilation.|  
|**total_worker_time**|**bigint**|La quantité totale de temps processeur, en microsecondes, consommé par les exécutions de ce déclencheur depuis sa compilation.|  
|**last_worker_time**|**bigint**|Temps processeur, en microsecondes, consommé lors de la dernière exécution du déclencheur.|  
|**min_worker_time**|**bigint**|Le temps processeur maximal, en microsecondes, consommé ce déclencheur lors d’une seule exécution.|  
|**max_worker_time**|**bigint**|Le temps processeur maximal, en microsecondes, consommé ce déclencheur lors d’une seule exécution.|  
|**total_physical_reads**|**bigint**|Le nombre total de lectures physiques effectuées par les exécutions de ce déclencheur depuis sa compilation.|  
|**last_physical_reads**|**bigint**|Le nombre de lectures physiques effectuées à la dernière fois que le déclencheur a été exécuté.|  
|**min_physical_reads**|**bigint**|Le nombre minimal de lectures physiques par ce déclencheur effectuées lors d’une seule exécution.|  
|**max_physical_reads**|**bigint**|Le nombre maximal de lectures physiques par ce déclencheur effectuées lors d’une seule exécution.|  
|**total_logical_writes**|**bigint**|Le nombre total d’écritures logiques effectuées par les exécutions de ce déclencheur depuis sa compilation.|  
|**last_logical_writes**|**bigint**|Le nombre d’écritures logiques effectuées à la dernière fois que le déclencheur a été exécuté.|  
|**min_logical_writes**|**bigint**|Le nombre minimal d’écritures logiques par ce déclencheur effectuées lors d’une seule exécution.|  
|**max_logical_writes**|**bigint**|Le nombre maximal d’écritures logiques par ce déclencheur effectuées lors d’une seule exécution.|  
|**total_logical_reads**|**bigint**|Le nombre total de lectures logiques effectuées par les exécutions de ce déclencheur depuis sa compilation.|  
|**last_logical_reads**|**bigint**|Le nombre de lectures logiques effectuées à la dernière fois que le déclencheur a été exécuté.|  
|**min_logical_reads**|**bigint**|Le nombre minimal de lectures logiques effectuées lors d’une seule exécution ce déclencheur.|  
|**max_logical_reads**|**bigint**|Le nombre maximal de lectures logiques effectuées lors d’une seule exécution ce déclencheur.|  
|**total_elapsed_time**|**bigint**|La durée écoulée totale, en microsecondes, pour les exécutions de ce déclencheur.|  
|**last_elapsed_time**|**bigint**|Temps écoulé, en microsecondes, pour la dernière exécution de ce déclencheur.|  
|**min_elapsed_time**|**bigint**|Durée calendaire minimale, en microsecondes, pour les différentes exécutions de ce déclencheur.|  
|**max_elapsed_time**|**bigint**|Durée calendaire maximale, en microsecondes, pour les différentes exécutions de ce déclencheur.| 
|**total_spills**|**bigint**|Le nombre total de pages répandues par l’exécution de ce déclencheur depuis sa compilation.<br /><br /> **S’applique aux**: compter [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**last_spills**|**bigint**|Le nombre de pages répandues la dernière fois que le déclencheur a été exécuté.<br /><br /> **S’applique aux**: compter [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**min_spills**|**bigint**|Le nombre minimal de pages de ce déclencheur a été dispersées jamais en une seule exécution.<br /><br /> **S’applique aux**: compter [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**max_spills**|**bigint**|Le nombre maximal de pages que ce déclencheur a été dispersées jamais en une seule exécution.<br /><br /> **S’applique aux**: compter [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
  
## <a name="remarks"></a>Notes  
 Dans [!INCLUDE[ssSDS](../../includes/sssds-md.md)], les vues de gestion dynamique ne peuvent pas exposer des informations qui ont un impact sur la relation contenant-contenu de la base de données, ou exposer des informations concernant d'autres bases de données auxquelles l'utilisateur a accès. Pour éviter d'exposer ces informations, chaque ligne contenant des données qui n'appartient pas au locataire connecté est filtrée.  

Les statistiques de la vue sont actualisées lorsqu'une requête est terminée.  
  
## <a name="permissions"></a>Permissions  

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], nécessite le `VIEW DATABASE STATE` autorisation dans la base de données.   
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne des informations sur les cinq principaux déclencheurs identifiés d'après le temps moyen écoulé.  
  
```sql  
SELECT TOP 5 d.object_id, d.database_id, DB_NAME(database_id) AS 'database_name',   
    OBJECT_NAME(object_id, database_id) AS 'trigger_name', d.cached_time,  
    d.last_execution_time, d.total_elapsed_time,   
    d.total_elapsed_time/d.execution_count AS [avg_elapsed_time],   
    d.last_elapsed_time, d.execution_count  
FROM sys.dm_exec_trigger_stats AS d  
ORDER BY [total_worker_time] DESC;  
```  
  
## <a name="see-also"></a>Voir aussi  
[Fonctions et vues de gestion dynamique liées à l’exécution &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
[sys.dm_exec_sql_text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
[sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
[Sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)   
[sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
  

---
title: sys.dm_exec_dms_workers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SYS.DM_EXEC_DMS_WORKERS_TSQL
- DM_EXEC_DMS_WORKERS_TSQL
- DM_EXEC_DMS_WORKERS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- dm_exec_dms_workers management view
- sys.dm_exec_dms_workers management view
ms.assetid: f468da29-78c3-4f10-8a3c-17905bbf46f2
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3728fddb26d45107b0e695453bef6eeb9fa5de63
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68097783"
---
# <a name="sysdmexecdmsworkers-transact-sql"></a>Sys.dm_exec_dms_workers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Contient des informations sur tous les traitements étapes effectuées DMS.  
  
 Cette vue affiche les données pour les 1000 derniers requêtes et les demandes actives ; demandes actives ont toujours les données présentes dans cette vue.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**nvarchar(32)**|Les requêtes que ce processus de travail DMS est la partie of.request_id, step_index, et dms_step_index forment la clé pour cette vue.||  
|step_index|**int**|Étape de que ce processus de travail DMS est la partie de la requête.|Consultez l’index de l’étape dans [sys.dm_exec_distributed_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-distributed-request-steps-transact-sql.md).|  
|dms_step_index|**int**|Étape dans le plan DMS que ce processus de travail est en cours d’exécution.|Consultez [sys.dm_exec_dms_workers (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-dms-workers-transact-sql.md)|  
|compute_node_id|**int**|Nœud qui le processus de travail est en cours d’exécution.|Consultez [sys.dm_exec_compute_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).|  
|distribution_id|**int**|||  
|type|**nvarcha(32)**|||  
|status|**nvarchar(32)**|État de cette étape|'Pending', 'Running', 'Complete', 'Failed', 'UndoFailed', 'PendingCancel', 'Cancelled', 'Undone', 'Aborted'|  
|bytes_per_sec|**bigint**|||  
|bytes_processed|**bigint**|||  
|rows_processed|**bigint**|||  
|start_time|**datetime**|Heure de début de l’étape d’exécution|Plus petit ou égal à l’heure actuelle et supérieur ou égal à end_compile_time de la requête à laquelle appartient cette étape.|  
|end_time|**datetime**|Heure à laquelle cette étape exécutée avec succès, a été annulée ou a échoué.|Plus petit ou égal à l’heure actuelle et supérieur ou égal à heure_début, la valeur NULL pour les étapes d’exécution ou en file d’attente.|  
|total_elapsed_time|**int**|Quantité totale de temps à qu'exécuter l’étape de requête, en millisecondes|Comprise entre 0 et la différence entre end_time et start_time. 0 pour les étapes en attente.|  
|cpu_time|**bigint**|||  
|query_time|**int**|||  
|buffers_available|**int**|||  
|dms_cpid|**int**|||  
|sql_spid|**int**|||  
|error_id|**nvarchar(36)**|||  
|source_info|**nvarchar(4000)**|||  
|destination_info|**nvarchar(4000)**|||  
|command|**nvarchar(4000)**|||  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes avec les vues de gestion dynamique de PolyBase](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Vues de gestion dynamique liées à la base de données &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  

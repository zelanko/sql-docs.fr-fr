---
title: sys. DM _exec_dms_workers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2019
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
ms.openlocfilehash: 6fd005563251ba674449020c7af25ce20ea98b4a
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73532940"
---
# <a name="sysdm_exec_dms_workers-transact-sql"></a>sys. DM _exec_dms_workers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Contient des informations sur tous les Workers effectuant les étapes DMS.  
  
 Cette vue affiche les données des 1000 dernières demandes et demandes actives. les demandes actives comportent toujours les données présentes dans cette vue.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|`nvarchar(32)`|Requête que ce Worker DMS fait partie de. request_id, step_index et dms_step_index constituent la clé de cette vue.||  
|step_index|`int`|Étape de requête dont ce Worker DMS fait partie.|Consultez index Step dans [sys. DM _exec_distributed_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-distributed-request-steps-transact-sql.md).|  
|dms_step_index|`int`|Étape du plan DMS que ce processus de travail exécute.|Consultez [sys. DM _exec_dms_workers (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-dms-workers-transact-sql.md)|  
|compute_node_id|`int`|Nœud sur lequel le processus de travail s’exécute.|Consultez [sys. DM _exec_compute_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).|  
|distribution_id|`int`|||  
|type|`nvarcha(32)`|||  
|status|`nvarchar(32)`|État de cette étape|« Pending », « Running », « Complete », « failed », « UndoFailed », « PendingCancel », « Cancelled », « UNDONE », « Aborted »|  
|bytes_per_sec|`bigint`|||  
|bytes_processed|`bigint`|||  
|rows_processed|`bigint`|||  
|start_time|`datetime`|Heure à laquelle l’étape a démarré l’exécution|Plus petite ou égale à l’heure actuelle et supérieure ou égale à end_compile_time de la requête à laquelle cette étape appartient.|  
|end_time|`datetime`|Heure à laquelle cette étape s’est terminée, a été annulée ou a échoué.|La valeur est inférieure ou égale à l’heure actuelle et supérieure ou égale à start_time, définie sur la valeur NULL pour les étapes en cours d’exécution ou en attente.|  
|total_elapsed_time|`int`|Durée totale d’exécution de l’étape de la requête, en millisecondes|Entre 0 et la différence entre end_time et start_time. 0 pour les étapes en file d’attente.|  
|cpu_time|`bigint`|||  
|query_time|`int`|||  
|buffers_available|`int`|||  
|dms_cpid|`int`|||  
|sql_spid|`int`|||  
|error_id|`nvarchar(36)`|||  
|source_info|`nvarchar(4000)`|||  
|destination_info|`nvarchar(4000)`|||  
|commande|`nvarchar(4000)`|||
|compute_pool_id|`int`|Identificateur unique du pool.|

## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes de Polybase avec les vues de gestion dynamique](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Vues &#40;de gestion dynamique liées aux bases de données Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  

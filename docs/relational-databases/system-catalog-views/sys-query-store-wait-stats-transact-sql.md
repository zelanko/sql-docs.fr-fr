---
title: Sys.query_store_wait_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/21/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.query_store_wait_stats
- query_store_wait_stats
dev_langs:
- TSQL
helpviewer_keywords:
- query_store_wait_stats catalog view
- sys.query_store_wait_stats catalog view
ms.assetid: ccf7a57c-314b-450c-bd34-70749a02784a
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 68ceb35ee3ef2cb3db3233c7050380584163c317
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067922"
---
# <a name="sysquerystorewaitstats-transact-sql"></a>Sys.query_store_wait_stats (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Contient des informations sur les informations d’attente pour la requête.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**wait_stats_id**|**bigint**|Identificateur de la ligne représentant les statistiques d’attente pour le plan_id runtime_stats_interval_id, execution_type et wait_category. Il est unique seulement pour les intervalles de statistiques de runtime passées. Pour l’intervalle actuellement actif, il existe peut-être plusieurs lignes représentant des statistiques d’attente pour le plan référencé par plan_id, avec le type d’exécution représenté par execution_type et la catégorie d’attente représenté par wait_category. En règle générale, une ligne représente les statistiques d’attente sont vidés sur le disque, tandis que les autres (s) représentent l’état en mémoire. Pour obtenir l’état réel pour chaque intervalle vous devez donc d’agréger les mesures, regroupement par plan_id, runtime_stats_interval_id, execution_type et wait_category. |  
|**plan_id**|**bigint**|Clé étrangère. Joint à [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md).|  
|**runtime_stats_interval_id**|**bigint**|Clé étrangère. Joint à [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md).|  
|**wait_category**|**tinyint**|Types d’attente sont classés à l’aide de la table ci-dessous, et ensuite les temps d’attente est agrégé dans ces catégories d’attente. Différentes catégories d’attente nécessitent une analyse de suivi différente pour résoudre le problème, mais les types à partir du même prospect de catégorie à des expériences de résolution des problèmes similaires d’attente, et en fournissant la requête affectée en outre à des attentes est la pièce manquante pour terminer le majorité de ces expériences avec succès.|
|**wait_category_desc**|**nvarchar(128)**|Pour obtenir une description textuelle du champ de catégorie d’attente, consultez le tableau ci-dessous.|
|**execution_type**|**tinyint**|Détermine le type d’exécution de requête :<br /><br /> 0 - exécution normale (achevée correctement)<br /><br /> 3 - initié par le client annulé l’exécution<br /><br /> 4 - exception abandonnée de l’exécution|  
|**execution_type_desc**|**nvarchar(128)**|Description textuelle du champ de type d’exécution :<br /><br /> 0 - standard<br /><br /> 3 - abandonnée<br /><br /> 4 - exception|  
|**total_query_wait_time_ms**|**bigint**|Total `CPU wait` heure pour le plan de requête dans l’intervalle d’agrégation et de catégorie (indiqué en millisecondes) d’attente.|
|**avg_query_wait_time_ms**|**float**|Durée du plan de requête par l’exécution dans la catégorie d’intervalle et l’attente d’agrégation (indiquée en millisecondes) d’attente moyen.|
|**last_query_wait_time_ms**|**bigint**|Dernière durée du plan de requête dans l’intervalle d’agrégation d’attente et la catégorie (indiqué en millisecondes) d’attente.|
|**min_query_wait_time_ms**|**bigint**|Minimum `CPU wait` heure pour le plan de requête dans l’intervalle d’agrégation et de catégorie (indiqué en millisecondes) d’attente.|
|**max_query_wait_time_ms**|**bigint**|Maximale `CPU wait` heure pour le plan de requête dans l’intervalle d’agrégation et de catégorie (indiqué en millisecondes) d’attente.|
|**stdev_query_wait_time_ms**|**float**|`Query wait` écart de durée de la requête planifier au sein de l’intervalle d’agrégation et catégorie (indiqué en millisecondes) d’attente.|

## <a name="wait-categories-mapping-table"></a>Table de mappage des catégories d’attente

« % » est utilisé comme un caractère générique
  
|Valeur entière|Catégorie d’attente|Incluent des types d’attente dans la catégorie|  
|-----------------|---------------|-----------------|  
|**0**|**Unknown**|Inconnu |  
|**1**|**Unité centrale**|SOS_SCHEDULER_YIELD|
|**2**|**Thread de travail**|THREADPOOL|
|**3**|**Verrou**|LCK_M_ %|
|**4**|**Verrou**|LATCH_ %|
|**5**|**Verrou de mémoire tampon**|PAGELATCH_ %|
|**6**|**Mémoire tampon d’e/s**|PAGEIOLATCH_ %|
|**7**|**Compilation***|RESOURCE_SEMAPHORE_QUERY_COMPILE|
|**8**|**CLR SQL**|CLR%, SQLCLR%|
|**9**|**Mise en miroir**|DBMIRROR %|
|**10**|**Transaction**|XACT%, DTC%, TRAN_MARKLATCH_%, MSQL_XACT_%, TRANSACTION_MUTEX|
|**11**|**Idle**|% SLEEP_, LAZYWRITER_SLEEP, SQLTRACE_BUFFER_FLUSH, SQLTRACE_INCREMENTAL_FLUSH_SLEEP, SQLTRACE_WAIT_ENTRIES, FT_IFTS_SCHEDULER_IDLE_WAIT, XE_DISPATCHER_WAIT, REQUEST_FOR_DEADLOCK_SEARCH, LOGMGR_QUEUE, ONDEMAND_TASK_QUEUE, CHECKPOINT_ FILE D’ATTENTE, XE_TIMER_EVENT|
|**12**|**PreEmptive**|PREEMPTIVE_ %|
|**13**|**Service Broker**|% BROKER_ **(mais pas BROKER_RECEIVE_WAITFOR)**|
|**14**|**E/s de journal Tran**|LOGMGR, LOGBUFFER, LOGMGR_RESERVE_APPEND, LOGMGR_FLUSH, LOGMGR_PMM_LOG, CHKPT, WRITELOG|
|**15**|**E/s réseau**|ASYNC_NETWORK_IO, NET_WAITFOR_PACKET, PROXY_NETWORK_IO, EXTERNAL_SCRIPT_NETWORK_IOF|
|**16**|**Parallelism**|CXPACKET, EXCHANGE|
|**17**|**Mémoire**|RESOURCE_SEMAPHORE, CMEMTHREAD, CMEMPARTITIONED, EE_PMOLOCK, MEMORY_ALLOCATION_EXT, RESERVED_MEMORY_ALLOCATION_EXT, MEMORY_GRANT_UPDATE|
|**18**|**Attente de l’utilisateur**|WAITFOR, WAIT_FOR_RESULTS, BROKER_RECEIVE_WAITFOR|
|**19**|**Suivi**|TRACEWRITE, SQLTRACE_LOCK, SQLTRACE_FILE_BUFFER, SQLTRACE_FILE_WRITE_IO_COMPLETION, SQLTRACE_FILE_READ_IO_COMPLETION, SQLTRACE_PENDING_BUFFER_WRITERS, SQLTRACE_SHUTDOWN, QUERY_TRACEOUT, TRACE_EVTNOTIFF|
|**20**|**Recherche en texte intégral**|FT_RESTART_CRAWL, OUTIL D’EXTRACTION DE TEXTE INTÉGRAL, MSSEARCH, FT_METADATA_MUTEX, FT_IFTSHC_MUTEX, FT_IFTSISM_MUTEX, FT_IFTS_RWLOCK, FT_COMPROWSET_RWLOCK, FT_MASTER_MERGE, FT_PROPERTYLIST_CACHE, FT_MASTER_MERGE_COORDINATOR, PWAIT_RESOURCE_SEMAPHORE_FT_ PARALLEL_QUERY_SYNC|
|**21**|**Autres e/s de disque**|ASYNC_IO_COMPLETION, IO_COMPLETION, BACKUPIO, WRITE_COMPLETION, IO_QUEUE_LIMIT, IO_RETRY|
|**22**|**Réplication**|SE_REPL_ %, REPL_ %, HADR_ % **(mais pas HADR_THROTTLE_LOG_RATE_GOVERNOR)** , PWAIT_HADR_ %, REPLICA_WRITES, FCB_REPLICA_WRITE, FCB_REPLICA_READ, PWAIT_HADRSIM|
|**23**|**Administrateur du taux de journal**|LOG_RATE_GOVERNOR, POOL_LOG_RATE_GOVERNOR, HADR_THROTTLE_LOG_RATE_GOVERNOR, INSTANCE_LOG_RATE_GOVERNOR|

**Compilation** catégorie d’attente n’est actuellement pas pris en charge.

## <a name="permissions"></a>Autorisations

 Nécessite l’autorisation `VIEW DATABASE STATE`.  
  
## <a name="see-also"></a>Voir aussi

- [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)
- [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)
- [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)
- [sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)
- [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)
- [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)
- [Analyse des performances à l’aide du magasin de requêtes](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)
- [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)
- [Procédures stockées de Query Store &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  

---
title: Sys.dm_os_spinlock_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/03/2019
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_spinlock_stats_TSQL
- dm_os_spinlock_stats_TSQL
- dm_os_spinlock_stats
- sys.dm_os_spinlock_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_spinlock_stats dynamic management view
author: bluefooted
ms.author: pamela
ms.reviewer: maghan
manager: amitban
ms.openlocfilehash: eae0057441fe6bc356c7cea6c1e6ded829bbb9e6
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265690"
---
# <a name="sysdmosspinlockstats-transact-sql"></a>Sys.dm_os_spinlock_stats (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne des informations sur toutes les attentes de verrouillage spinlock organisé par type.  
  

|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|name|**nvarchar (256)**|Nom du type de verrouillage spinlock.|  
|collisions|**bigint**|Le nombre de fois où un thread tente d’acquérir le verrouillage spinlock et est bloqué, car un autre thread actuellement maintient le verrouillage spinlock.|  
|effectue des spins|**bigint**|Le nombre de fois qu’un thread exécute une boucle lors de la tentative d’acquérir le verrouillage spinlock.|  
|spins_per_collision|**real**|Ratio de spins par collision.|  
|sleep_time|**bigint**|La quantité de temps en millisecondes passé par threads à se mettre en veille en cas d’une interruption.|  
|interruptions|**int**|Le nombre de fois où un thread « tourne » ne parvient pas à acquérir le verrouillage spinlock et abandonne le planificateur.|  


## <a name="permissions"></a>Autorisations  
Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] niveaux Premium, nécessite le `VIEW DATABASE STATE` autorisation dans la base de données. Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard et les niveaux de base, nécessite le **administrateur du serveur** ou un **administrateur Azure Active Directory** compte.    
  
## <a name="remarks"></a>Notes  
 
 Sys.dm_os_spinlock_stats peut être utilisé pour identifier la source de la contention de verrouillage tournant. Dans certaines situations, vous pourrez peut-être résoudre ou de réduire la contention de verrouillage tournant. Il peut toutefois arriver que vous soyez obligé de contacter le Support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
 Vous pouvez réinitialiser le contenu de sys.dm_os_spinlock_stats en utilisant `DBCC SQLPERF` comme suit :  
  
```  
DBCC SQLPERF ('sys.dm_os_spinlock_stats', CLEAR);  
GO  
```  
  
 Cette commande remet tous les compteurs à 0.  
  
> [!NOTE]  
>  Ces statistiques ne sont pas conservées si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] redémarre. Toutes les données sont cumulées à partir de la dernière réinitialisation des statistiques ou à partir du démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="spinlocks"></a>Verrouillages spinlock  
 Un verrouillage spinlock est un objet de synchronisation légers utilisé pour sérialiser l’accès aux structures de données qui sont généralement conservées pendant une courte période de temps. Lorsqu’un thread tente d’accéder à une ressource protégée par un verrouillage spinlock, qui est maintenu par un autre thread, le thread exécute une boucle, ou « ajouter » et essayez d’accéder à la ressource à nouveau, au lieu de cédant immédiatement le planificateur comme avec un verrou ou d’autres ressources délai d’attente. Le thread continuera à tourner jusqu'à ce que la ressource est disponible, ou la boucle se termine, moment où le thread sera génèrent le planificateur et revenir en arrière dans la file d’attente exécutable. Cette pratique permet de réduire le changement de contexte de thread excessive, mais lors de la contention pour un verrouillage spinlock est élevée, l’utilisation importante du processeur peut être observé.
   
 Le tableau suivant contient la brève description des types de verrouillage tournant plus courants.  
  
|Type de verrouillage tournant|Description|  
|-----------------|-----------------|  
|ABR|À usage interne uniquement|
|ADB_CACHE|À usage interne uniquement|
|ALLOC_CACHES_HASH|À usage interne uniquement|
|APPENDONLY_STORAGE|À usage interne uniquement|
|APRC_BACK_OFF_STATS|À usage interne uniquement|
|APRC_EVENT_LIST|À usage interne uniquement|
|APRC_QUEUE_LIST|À usage interne uniquement|
|APRC_VALIDATION_QUEUE_LIST|À usage interne uniquement|
|ASYNC_OP_ADMIN_CLIENT_REGISTRATION_LIST|À usage interne uniquement|
|ASYNC_OP_ADMIN_WORK_REGISTRATION_HASH_TABLE|À usage interne uniquement|
|ASYNCSTATSLIST|À usage interne uniquement|
|BACKUP|À usage interne uniquement|
|BACKUP_COPY_CONTEXT|À usage interne uniquement|
|BACKUP_CTX|À usage interne uniquement|
|BASE_XACT_HASH|À usage interne uniquement|
|BLOCKER_ENUM|À usage interne uniquement|
|BPREPARTITION|À usage interne uniquement|
|BPWORKFILE|À usage interne uniquement|
|BUF_HASH|À usage interne uniquement|
|BUF_LINK|À usage interne uniquement|
|BUF_WRITE_LOG|À usage interne uniquement|
|CACHEOBJ_DBG|À usage interne uniquement|
|CHANNELFORCECLOSEMANAGER|À usage interne uniquement|
|CHECK_AGGREGATE_STATE|À usage interne uniquement|
|CLR_HOSTTASK|À usage interne uniquement|
|CLR_SPIN_LOCK|À usage interne uniquement|
|CMED_DATABASE|À usage interne uniquement|
|CMED_HASH_SET|À usage interne uniquement|
|COLUMNDATASETSESSIONLIST|À usage interne uniquement|
|COLUMNSTORE_HASHTABLE|À usage interne uniquement|
|COLUMNSTOREBUILDSTATE_LIST|À usage interne uniquement|
|COM_INIT|À usage interne uniquement|
|VALIDABLE|À usage interne uniquement|
|COMPPLAN_SKELETON|À usage interne uniquement|
|CONNECTION_MANAGER|À usage interne uniquement|
|SE CONNECTE|À usage interne uniquement|
|CSIBUILDMEM|À usage interne uniquement|
|CURSOR|À usage interne uniquement|
|CURSQL|À usage interne uniquement|
|DATAPORTCONSUMER|À usage interne uniquement|
|DATAPORTSOURCEINFOCREDIT|À usage interne uniquement|
|DATAPORTSOURCEINFOQUEUE|À usage interne uniquement|
|DATASET_FREELIST|À usage interne uniquement|
|DBCC_CHECK|À usage interne uniquement|
|DBSEEDING_OPERATION|À usage interne uniquement|
|DBT_HASH|À usage interne uniquement|
|DBT_IO_LIST|À usage interne uniquement|
|DBTABLE|Contrôle l’accès à une structure de données en mémoire pour chaque base de données dans SQL Server qui contient les propriétés de cette base de données. Consultez [cet article](https://techcommunity.microsoft.com/t5/SQL-Server/Improving-Concurrency-Scalability-of-SQL-Server-workload-by/ba-p/384789) pour plus d’informations. |
|DEFERRED_WF_EXT_DROP|À usage interne uniquement|
|DEK_INSTANCE|À usage interne uniquement|
|DELAYED_PARTITIONED_STACK|À usage interne uniquement|
|DELETEBITMAP|À usage interne uniquement|
|DIAG_MANAGER|À usage interne uniquement|
|DIAG_OBJECT|À usage interne uniquement|
|DIGEST_CACHE|À usage interne uniquement|
|DINPBUF|À usage interne uniquement|
|DIRECTLOGCONSUMER|À usage interne uniquement|
|DP_LIST|Contrôle l’accès à la liste des pages de modifications pour une base de données qui a le point de contrôle indirect sous tension. Consultez [cet article](https://techcommunity.microsoft.com/t5/SQL-Server/Indirect-Checkpoint-and-tempdb-8211-the-good-the-bad-and-the-non/ba-p/385510) pour plus d’informations.|
|DROP|À usage interne uniquement|
|DROP_TEMPO|À usage interne uniquement|
|DROPPED_ALLOC_UNIT|À usage interne uniquement|
|DTC_HASHTABLE|À usage interne uniquement|
|DTT_LIST|À usage interne uniquement|
|ENDD_LIST|À usage interne uniquement|
|EXT_CACHE|À usage interne uniquement|
|EXTENT_ACTIVATION|À usage interne uniquement|
|FABRIC_DB_MGR_PTR|À usage interne uniquement|
|FABRIC_LOG_MANAGEMENT_INPUT_VALUE|À usage interne uniquement|
|FABRIC_REPLICA_TRANSPORT|À usage interne uniquement|
|FABRIC_TVF_DATA_CONSUMER_LIST|À usage interne uniquement|
|FABRIC_TVF_LOAD_LIB|À usage interne uniquement|
|FCB_REPLICA_SYNC|À usage interne uniquement|
|FGCB_PRP_FILL|À usage interne uniquement|
|FILE_HANDLE_CACHE|À usage interne uniquement|
|FILE_TABLE|À usage interne uniquement|
|FILESTREAM_CHUNKER|À usage interne uniquement|
|FREE_SPACE_CACHE_ENTRY|À usage interne uniquement|
|FS_CONTAINER_LIST_WITH_DELETE|À usage interne uniquement|
|FS_DELETED_FOLDER_CLEANUP|À usage interne uniquement|
|FSAGENT|À usage interne uniquement|
|FSGHOST_STATUS|À usage interne uniquement|
|FT_INIT|À usage interne uniquement|
|GHOST_FREE|À usage interne uniquement|
|GHOST_HASH|À usage interne uniquement|
|GLOBAL_SCHEDULER_LIST|À usage interne uniquement|
|GLOBAL_TRACE_FLAGS|À usage interne uniquement|
|GLOBALTRANS|À usage interne uniquement|
|GROUP_COMMIT_FEEDBACK_LOOP|À usage interne uniquement|
|GUARDIAN|À usage interne uniquement|
|HADR_AGH_X_ACCESS|À usage interne uniquement|
|HADR_AR_CONTROLLER_COLLECTION|À usage interne uniquement|
|HADR_AR_DB_MGR|À usage interne uniquement|
|HADR_AR_TRANSPORT|À usage interne uniquement|
|HADR_COMPRESSION_MGR_POOL|À usage interne uniquement|
|HADR_FABRIC_FACTORY|À usage interne uniquement|
|HADR_PRIORITY_QUEUE|À usage interne uniquement|
|HADR_TRANSPORT_CONTROL|À usage interne uniquement|
|HADR_TRANSPORT_LIST|À usage interne uniquement|
|HADRSEEDINGLIST|À usage interne uniquement|
|HOBT_DROPPED|À usage interne uniquement|
|HOBT_HASH|À usage interne uniquement|
|HTTP|À usage interne uniquement|
|HTTP_CONNCACHE|À usage interne uniquement|
|HTTP_ENDPOINT|À usage interne uniquement|
|IDENTITÉ|À usage interne uniquement|
|INDEX_CREATE|À usage interne uniquement|
|IO_DISPENSER_PAUSE|À usage interne uniquement|
|IO_RG_VOLUME_HASHTABLE|À usage interne uniquement|
|IOREQ|À usage interne uniquement|
|ISSRESOURCE|À usage interne uniquement|
|KTM_ENLISTMENT|À usage interne uniquement|
|LANG_RES_LOAD|À usage interne uniquement|
|LIVE_TARGET_TVF|À usage interne uniquement|
|LOCK_FREE_LIST|À usage interne uniquement|
|LOCK_HASH|Protège l’accès à la table de hachage de gestionnaire de verrou qui stocke des informations sur les verrous maintenus dans une base de données. Consultez [cet article](https://support.microsoft.com/kb/2926217) pour plus d’informations.|
|LOCK_NOTIFICATION|À usage interne uniquement|
|LOCK_RESOURCE_ID|À usage interne uniquement|
|LOCK_RW_ABTX_HASH_SET|À usage interne uniquement|
|LOCK_RW_AGDB_HEALTH_DIAG|À usage interne uniquement|
|LOCK_RW_CMED_HASH_SET|À usage interne uniquement|
|LOCK_RW_DPT_TABLE|À usage interne uniquement|
|LOCK_RW_IN_ROW_TRACKER|À usage interne uniquement|
|LOCK_RW_LOGIN_RATE_STATS|À usage interne uniquement|
|LOCK_RW_PVS_PAGE_TRACKER|À usage interne uniquement|
|LOCK_RW_RBIO_REQ|À usage interne uniquement|
|LOCK_RW_SECURITY_CACHE|À usage interne uniquement|
|LOCK_RW_TEST|À usage interne uniquement|
|LOCK_RW_WPR_BUCKET|À usage interne uniquement|
|LOCK_SORT_STREAM|À usage interne uniquement|
|LOCK_SQLSATELLITE_MESSAGE|À usage interne uniquement|
|LOG_CONSOLIDATION|À usage interne uniquement|
|LOG_RG_GOVERNOR|À usage interne uniquement|
|LOGCACHE_ACCESS|À usage interne uniquement|
|LOGFLUSHQ|À usage interne uniquement|
|LOGIOSEQ|À usage interne uniquement|
|LOGIOSEQMAPPENDINGMESSAGEQUEUE|À usage interne uniquement|
|LOGLC|À usage interne uniquement|
|LOGLFM|À usage interne uniquement|
|LOGON_TRIGGER_CACHE|À usage interne uniquement|
|LOGPOOL_HASHBUCKET|À usage interne uniquement|
|LOGPOOL_REFCOUNTEDOBJECT|À usage interne uniquement|
|LOGPOOL_SHAREDCACHEBUFFER|À usage interne uniquement|
|LOGPOOL_SIZEPERRESOURCEPOOL|À usage interne uniquement|
|LPE_BATCH|À usage interne uniquement|
|LPE_SESSION|À usage interne uniquement|
|LPE_SXTP|À usage interne uniquement|
|LSID|À usage interne uniquement|
|LSLIST|À usage interne uniquement|
|LSNREFLIST|À usage interne uniquement|
|LSS_SYNC_DTC|À usage interne uniquement|
|MD_CHANGE_NOTIFICATION|À usage interne uniquement|
|MDB_REMOTE_BATCH_STATS_HASH_TABLE|À usage interne uniquement|
|MDB_REMOTE_SESSION_HASH_TABLE|À usage interne uniquement|
|MEM_MGR|À usage interne uniquement|
|MGR_CACHE|À usage interne uniquement|
|MIGRATION_BUF_LIST|À usage interne uniquement|
|NETCONN_ADDRESS|À usage interne uniquement|
|ONDEMAND_TASK|À usage interne uniquement|
|ONE_PROC_SIM_NODE_CONTEXT|À usage interne uniquement|
|ONE_PROC_SIM_NODE_CONTEXT_LIST|À usage interne uniquement|
|ONE_PROC_SIM_REPLICA_CONTEXT|À usage interne uniquement|
|ONE_PROC_SIM_SERVICE_PARTITION|À usage interne uniquement|
|OPT_IDX_MISS_ID|À usage interne uniquement|
|OPT_IDX_MISS_KEY|À usage interne uniquement|
|OPT_IDX_STATS|À usage interne uniquement|
|OPT_INFO_MGR|À usage interne uniquement|
|PAGE_WORKITEMLIST|À usage interne uniquement|
|PAGECOPIER|À usage interne uniquement|
|PARALLELREDOCACHE|À usage interne uniquement|
|PARTITIONED_HEAP_FREE_LIST|À usage interne uniquement|
|PROGRESS_REPORT|À usage interne uniquement|
|QE_SHUTDOWN|À usage interne uniquement|
|QSCAN_CACHE|À usage interne uniquement|
|QUERY_EXEC_STATS|À usage interne uniquement|
|QUERY_STORE_ASYNC_PERSIST|À usage interne uniquement|
|QUERY_STORE_ASYNC_QUEUE_TLIST|À usage interne uniquement|
|QUERY_STORE_CAPTURE_POLICY_INTERVAL|À usage interne uniquement|
|QUERY_STORE_CAPTURE_POLICY_STATS|À usage interne uniquement|
|QUERY_STORE_CAPTURE_POLICY_THRESHOLD|À usage interne uniquement|
|QUERY_STORE_CURRENT_INTERVAL|À usage interne uniquement|
|QUERY_STORE_HT_CACHE|À usage interne uniquement|
|QUERY_STORE_LIST|À usage interne uniquement|
|QUERY_STORE_PLAN_COMP_AGG|À usage interne uniquement|
|QUERY_STORE_PLAN_LIST|À usage interne uniquement|
|QUERY_STORE_READ_ONLY_FLAGS|À usage interne uniquement|
|QUERY_STORE_SELF_AGG|À usage interne uniquement|
|QUERY_STORE_STMT_COMP_AGG|À usage interne uniquement|
|QUERYEXEC|À usage interne uniquement|
|QUERYSCAN|À usage interne uniquement|
|RANGE_GENERATION|À usage interne uniquement|
|READ_AHEAD|À usage interne uniquement|
|REDOMGRSTATE|À usage interne uniquement|
|REMOTE_SESSION_CACHE|À usage interne uniquement|
|REMOTEBLOCKIO|À usage interne uniquement|
|REMOTEOP|À usage interne uniquement|
|REPL_LOGREADER_HISTORY_CACHE|À usage interne uniquement|
|REPL_LOGREADER_PERDB_HISTORY_CACHE|À usage interne uniquement|
|RESMANAGER|À usage interne uniquement|
|RESSOURCES|À usage interne uniquement|
|RESQUEUE|À usage interne uniquement|
|RFS_THREAD_QUEUE|À usage interne uniquement|
|RG_TIMER|À usage interne uniquement|
|ROWGROUP_VERSIONS|À usage interne uniquement|
|RPCCHANNELPOOL|À usage interne uniquement|
|RPCPACKAGE|À usage interne uniquement|
|RPCREQUESTORCONTEXT|À usage interne uniquement|
|RWLOCK_LAST|À usage interne uniquement|
|SATELLITE_CONNECTION|À usage interne uniquement|
|SBS_CLIENT_ENDPOINTS|À usage interne uniquement|
|SBS_CLIENT_REQUESTS|À usage interne uniquement|
|SBS_DISPATCH|À usage interne uniquement|
|SBS_PENDING|À usage interne uniquement|
|SBS_SERVER_XACT_TASK_PROXY|À usage interne uniquement|
|SBS_TRANSPORT|À usage interne uniquement|
|SBS_UCS_DISPATCH|À usage interne uniquement|
|SÉCURITÉ|À usage interne uniquement|
|SECURITY_CACHE|À usage interne uniquement|
|SECURITY_FEDAUTH_AAD_BECWSCONNS|À usage interne uniquement|
|SEMANTIC_TICACHE|À usage interne uniquement|
|SEQUENCED_OBJECT|À usage interne uniquement|
|SEQUEUE_SIZED_THREADSAFE|À usage interne uniquement|
|SESSION_KILLER|À usage interne uniquement|
|SESSION_MANAGER|À usage interne uniquement|
|SESSION_SEC_CONTEXT|À usage interne uniquement|
|SETRANGE_SYNC|À usage interne uniquement|
|SHARABLE_SESSION_OBJECTS|À usage interne uniquement|
|SLO_INFO_LIST|À usage interne uniquement|
|SNI|À usage interne uniquement|
|SNI_NODE_PENDING_IO_QUEUE|À usage interne uniquement|
|SOAPSESSIONS|À usage interne uniquement|
|SOS_ABORT_TASK|À usage interne uniquement|
|SOS_ACTIVEDESCRIPTOR|À usage interne uniquement|
|SOS_BLOCKALLOCPARTIALLIST|À usage interne uniquement|
|SOS_BLOCKDESCRIPTORBUCKET|À usage interne uniquement|
|SOS_CACHESTORE|Synchronise l’accès aux diverses de caches en mémoire dans SQL Server tels que le cache du plan ou le cache de la table temporaire. Une contention importante sur ce type de verrouillage spinlock peut signifier plusieurs choses en fonction de cache spécifique qui est en conflit. Contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] le Support technique pour l’aide pour résoudre ce type de verrouillage spinlock. |
|SOS_CACHESTORE_CLOCK|À usage interne uniquement|
|SOS_CLOCKALG_INTERNODE_SYNC|À usage interne uniquement|
|SOS_DEBUG_HOOK|À usage interne uniquement|
|SOS_DESCDATABUFFERLIST|À usage interne uniquement|
|SOS_LARGEPAGE_ALLOCATOR|À usage interne uniquement|
|SOS_MINITHREAD|À usage interne uniquement|
|SOS_NODE|À usage interne uniquement|
|SOS_OBJECT_POOL|À usage interne uniquement|
|SOS_OBJECT_STORE|À usage interne uniquement|
|SOS_OOM_CHECK|À usage interne uniquement|
|SOS_PHYS_PAGE_CACHE|À usage interne uniquement|
|SOS_RESOURCE_CLERK_LIST|À usage interne uniquement|
|SOS_RINGBUFFER_RECORD|À usage interne uniquement|
|SOS_RW|À usage interne uniquement|
|SOS_SATELLITE_USER_POOL|À usage interne uniquement|
|SOS_SCHEDULER|À usage interne uniquement|
|SOS_SELIST_SIZED_SLOCK|À usage interne uniquement|
|SOS_SUSPEND_QUEUE|À usage interne uniquement|
|SOS_SYSTHREAD|À usage interne uniquement|
|SOS_SYSTHREAD_DISPATCHER|À usage interne uniquement|
|SOS_TASK|À usage interne uniquement|
|SOS_TLIST|À usage interne uniquement|
|SOS_VM_LOW|À usage interne uniquement|
|SOS_WAIT_STATS|À usage interne uniquement|
|SOS_WAITABLE_ADDRESS_HASHBUCKET|À usage interne uniquement|
|SPIN_EVENT_MUTEX|À usage interne uniquement|
|SPL_DISPATCHER_LIST|À usage interne uniquement|
|SPL_DISPATCHER_QUEUE|À usage interne uniquement|
|SPL_NONYIELD_ANALYSIS|À usage interne uniquement|
|SPL_QUERY_STORE_CTX_INITIALIZED|À usage interne uniquement|
|SPL_QUERY_STORE_EXEC_STATS_AGG|À usage interne uniquement|
|SPL_QUERY_STORE_EXEC_STATS_READ|À usage interne uniquement|
|SPL_QUERY_STORE_STATS_COOKIE_CACHE|À usage interne uniquement|
|SPL_SOS_DISPATCHER|À usage interne uniquement|
|SPL_TDS_PKT_QUEUE|À usage interne uniquement|
|SPL_XE_BUFFER_MGR|À usage interne uniquement|
|SPL_XE_DISPATCHER_QUEUE|À usage interne uniquement|
|SPL_XE_NOTIFICATION_CALLBACK_LIST|À usage interne uniquement|
|SPL_XE_SESSION_EVENT_MGR|À usage interne uniquement|
|SPL_XE_SESSION_MGR|À usage interne uniquement|
|SPL_XE_SESSION_TARGET_MGR|À usage interne uniquement|
|SPT_PROFILE|À usage interne uniquement|
|SQL_MGR|À usage interne uniquement|
|SQL_NORM|À usage interne uniquement|
|SQLTRACE_FILE_BUFFER|À usage interne uniquement|
|SRVPROC|À usage interne uniquement|
|STACK_HASHER|À usage interne uniquement|
|SUBLATCH|À usage interne uniquement|
|SUBPDESC|À usage interne uniquement|
|SUBPDESC_LIST|À usage interne uniquement|
|SVC_BROKER_CTRL|À usage interne uniquement|
|SVC_BROKER_DEBUG_LIST|À usage interne uniquement|
|SVC_BROKER_LIST|À usage interne uniquement|
|SVC_BROKER_OBJECT|À usage interne uniquement|
|SYNCPOINT_RESOURCE|À usage interne uniquement|
|TaskElapsedExecutionMonitor|À usage interne uniquement|
|TDS_TVP|À usage interne uniquement|
|TESTTEAM|À usage interne uniquement|
|TESTTEAMEXPONENTIAL|À usage interne uniquement|
|TESTTEAMEXPONENTIALTASTAS|À usage interne uniquement|
|TESTTEAMTASTAS|À usage interne uniquement|
|TMP_SESS_KEY|À usage interne uniquement|
|TSQL_DEBUG|À usage interne uniquement|
|TXFRM_REPL|À usage interne uniquement|
|VDI_OPERATION|À usage interne uniquement|
|WINFAB_REPORT_FAULT|À usage interne uniquement|
|WRITE_PAGE_RECORDER|À usage interne uniquement|
|X_PACKET_LIST|À usage interne uniquement|
|X_PIPE|À usage interne uniquement|
|X_PIPE_DEMAND|À usage interne uniquement|
|X_PORT|À usage interne uniquement|
|XACT_LOCK_INFO|À usage interne uniquement|
|XACT_LOCKINFO_TASK|À usage interne uniquement|
|XACT_WORKSPACE|À usage interne uniquement|
|XCB|À usage interne uniquement|
|XCB_FREE_LIST|À usage interne uniquement|
|XCB_HASH|À usage interne uniquement|
|XCHNG_TRACE|À usage interne uniquement|
|XDES|À usage interne uniquement|
|XDES_HASH|À usage interne uniquement|
|XDESMGR|À usage interne uniquement|
|XDESTABLELIST|À usage interne uniquement|
|XE_RATE_LIMITER_STRETCHDB|À usage interne uniquement|
|XE_SESSION_STORAGE|À usage interne uniquement|
|XID_ARRAY|À usage interne uniquement|
|XIO_BLOCKLIST|À usage interne uniquement|
|XIO_REQSTR|À usage interne uniquement|
|XIO_SEQNUMBUMP|À usage interne uniquement|
|XIOSTATS|À usage interne uniquement|
|XTP_RT_DATA_LIST|À usage interne uniquement|
|XTS_MGR|À usage interne uniquement|
|XVB_CSN|À usage interne uniquement|
|XVB_LIST|À usage interne uniquement|
 

  
## <a name="see-also"></a>Voir aussi  
 
 [DBCC SQLPERF &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-sqlperf-transact-sql.md)   
 
 [Vues de gestion dynamique liées à système d’exploitation SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  

 [Dans quel cas Spinlock un importante pilote de processeur dans SQL Server ?](https://techcommunity.microsoft.com/t5/SQL-Server-Support/When-is-Spinlock-a-Significant-Driver-of-CPU-utilization-in-SQL/ba-p/530142)

 [Diagnostic et la résolution des conflits de verrouillage tournant sur SQL Server](https://www.microsoft.com/download/details.aspx?id=26666)
  
  



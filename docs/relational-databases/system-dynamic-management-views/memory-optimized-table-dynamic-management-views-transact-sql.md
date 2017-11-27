---
title: "Mémoire optimisée Table des vues de gestion dynamique (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 02/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: ccd82fed-1a3f-47de-85c4-1c9bdd80b027
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: af84a0ba17f3a4d10e20919c3ae7c4c90f688eb3
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="memory-optimized-table-dynamic-management-views-transact-sql"></a>Vues de gestion dynamique des tables mémoire optimisées (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Les éléments suivants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vues de gestion dynamique (DMV) sont utilisés avec l’OLTP en mémoire :  
  
 Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
|||  
|-|-|   
|[Sys.dm_db_xtp_checkpoint_stats &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-stats-transact-sql.md)|[Sys.dm_db_xtp_checkpoint_files &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql.md)|
|[Sys.dm_db_xtp_gc_cycle_stats &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-gc-cycle-stats-transact-sql.md)|[sys.dm_db_xtp_hash_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-hash-index-stats-transact-sql.md)| 
|[sys.dm_db_xtp_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-index-stats-transact-sql.md)|[sys.dm_db_xtp_memory_consumers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-memory-consumers-transact-sql.md)|
|[Sys.dm_db_xtp_merge_requests (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-merge-requests-transact-sql.md)|[sys.dm_db_xtp_object_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-object-stats-transact-sql.md)|
|[sys.dm_db_xtp_nonclustered_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-nonclustered-index-stats-transact-sql.md)|[sys.dm_db_xtp_table_memory_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-table-memory-stats-transact-sql.md)|  
|[Sys.dm_db_xtp_transactions &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-transactions-transact-sql.md)|[Sys.dm_xtp_gc_queue_stats &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-queue-stats-transact-sql.md)|  
|[Sys.dm_xtp_gc_stats &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-stats-transact-sql.md)|[Sys.dm_xtp_system_memory_consumers &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xtp-system-memory-consumers-transact-sql.md)|
|[Sys.dm_xtp_transaction_stats &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-xtp-transaction-stats-transact-sql.md)||

### <a name="object-catalog-views"></a>Affichages catalogue d'objets

Les vues de catalogue d’objet suivantes sont utilisées spécifiquement avec OLTP en mémoire.

|||  
|-|-|   
|[Sys.hash_indexes &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-hash-indexes-transact-sql.md)|[Sys.memory_optimized_tables_internal_attributes &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-memory-optimized-tables-internal-attributes-transact-sql.md)|  

### <a name="internal-dmvs"></a>Vues de gestion dynamique internes

Il existe des vues DMV supplémentaires qui sont destinés à un usage interne uniquement et pour lequel nous ne fournir aucune documentation directe. Dans la zone de tables optimisées en mémoire, la DMV non documentées sont les suivantes :

- Sys.dm_xtp_threads
- Sys.dm_xtp_transaction_recent_rows


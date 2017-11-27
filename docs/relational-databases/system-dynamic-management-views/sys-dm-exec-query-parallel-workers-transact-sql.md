---
title: Sys.dm_exec_query_parallel_workers (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 05/24/2017
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
- dm_exec_query_parallel_workers_TSQL
- dm_exec_query_parallel_workers
- sys.dm_exec_query_parallel_workers_TSQL
- sys.dm_exec_query_parallel_workers
dev_langs: TSQL
helpviewer_keywords: sys.dm_exec_query_parallel_workers dynamic management view
ms.assetid: 1d72cef1-22d8-4ae0-91db-6694fe918c9f
caps.latest.revision: "1"
author: pelopes
ms.author: pelopes
manager: ajayj
ms.workload: Inactive
ms.openlocfilehash: dd0653ae9177673026eb07bbc14f2b6769315e00
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmexecqueryparallelworkers-transact-sql"></a>Sys.dm_exec_query_parallel_workers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Retourne des informations de disponibilité de travailleur par nœud.  
  
|Nom|Type de données| Description|  
|----------|---------------|-----------------|  
|**node_id :**|**int**|ID de nœud NUMA.|  
|**scheduler_count**|**int**|Nombre de planificateurs sur ce nœud.|  
|**max_worker_count**|**int**|Nombre maximal de threads de travail pour les requêtes parallèles.|  
|**reserved_worker_count**|**int**|Nombre de threads de travail réservés par les requêtes parallèles, ainsi que le nombre de traitements principales utilisé par toutes les demandes.| 
|**free_worker_count**|**int**|Nombre de threads de travail disponibles pour les tâches.<br /><br />**Remarque :** chaque demande entrante consomme au moins 1 processus de travail est soustrait du nombre de travail disponible.  Il est possible que le nombre de travail disponible peut être un nombre négatif sur un serveur très chargé.| 
|**used_worker_count**|**int**|Nombre de workers utilisé par les requêtes parallèles.|  
  
## <a name="permissions"></a>Permissions  
 Sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requiert l’autorisation VIEW SERVER STATE sur le serveur.  
  
 Sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)] niveaux Premium requiert l’autorisation VIEW DATABASE STATE dans la base de données. Sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Standard et les niveaux de base nécessite le [!INCLUDE[ssSDS](../../includes/sssds-md.md)] compte d’administrateur.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-viewing-current-parallel-worker-availability"></a>A. Affichage de la disponibilité de travail parallèle en cours  

``` tsql 
SELECT * FROM sys.dm_exec_query_parallel_workers;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Les fonctions et vues de gestion dynamique &#40; liées à l’exécution Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Sys.dm_os_workers &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)

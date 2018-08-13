---
title: Sys.dm_exec_query_parallel_workers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_exec_query_parallel_workers_TSQL
- dm_exec_query_parallel_workers
- sys.dm_exec_query_parallel_workers_TSQL
- sys.dm_exec_query_parallel_workers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_parallel_workers dynamic management view
ms.assetid: 1d72cef1-22d8-4ae0-91db-6694fe918c9f
caps.latest.revision: 1
author: pelopes
ms.author: pelopes
manager: ajayj
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: dd1f4c3c0c7ed42184ce008fe1641a2c35f0ee3a
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39564983"
---
# <a name="sysdmexecqueryparallelworkers-transact-sql"></a>Sys.dm_exec_query_parallel_workers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Retourne des informations de disponibilité de worker par nœud.  
  
|Nom   |Type de données|Description|  
|----------|---------------|-----------------|  
|**node_id**|**Int**|ID de nœud NUMA.|  
|**scheduler_count**|**Int**|Nombre de planificateurs sur ce nœud.|  
|**max_worker_count**|**Int**|Nombre maximal de travailleurs pour les requêtes parallèles.|  
|**reserved_worker_count**|**Int**|Nombre de traitements réservés par les requêtes parallèles, plus le nombre de workers principales utilisé par toutes les demandes.| 
|**free_worker_count**|**Int**|Nombre de travailleurs disponibles pour les tâches.<br /><br />**Remarque :** chaque requête entrante consomme au moins 1 worker, ce qui est soustrait du nombre de travail gratuit.  Il est possible que le nombre de travail gratuit peut être un nombre négatif sur un serveur très chargé.| 
|**used_worker_count**|**Int**|Nombre de workers utilisé par les requêtes parallèles.|  
  
## <a name="permissions"></a>Permissions  

Sur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], nécessite `VIEW SERVER STATE` autorisation.   
Sur [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], nécessite le `VIEW DATABASE STATE` autorisation dans la base de données.   
 
## <a name="examples"></a>Exemples  
  
### <a name="a-viewing-current-parallel-worker-availability"></a>A. Affichage de la disponibilité de travail parallèles en cours  

```sql 
SELECT * FROM sys.dm_exec_query_parallel_workers;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Fonctions et vues de gestion dynamique liées à l’exécution &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Sys.dm_os_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)

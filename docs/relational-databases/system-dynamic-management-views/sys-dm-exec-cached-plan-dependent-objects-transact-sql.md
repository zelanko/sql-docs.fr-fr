---
title: Sys.dm_exec_cached_plan_dependent_objects (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_cached_plan_dependent_objects
- dm_exec_cached_plan_dependent_objects_TSQL
- sys.dm_exec_cached_plan_dependent_objects_TSQL
- dm_exec_cached_plan_dependent_objects
dev_langs: TSQL
helpviewer_keywords: sys.dm_exec_cached_plan_dependent_objects dynamic management function
ms.assetid: 9b6cf5f7-b267-44fb-aac8-f49c9aa10cc1
caps.latest.revision: "19"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b6e044c20434b7aa8a0f927d4c626984309f7a29
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmexeccachedplandependentobjects-transact-sql"></a>sys.dm_exec_cached_plan_dependent_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque plan d'exécution [!INCLUDE[tsql](../../includes/tsql-md.md)], plan d'exécution CLR (Common Language Runtime) et curseur associé à un plan.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
dm_exec_cached_plan_dependent_objects(plan_handle)  
```  
  
## <a name="arguments"></a>Arguments  
 *plan_handle*  
 Identifie de façon univoque un plan d'exécution de requête pour un traitement exécuté ; ce plan réside dans la mémoire cache des plans. *plan_handle* est **varbinary(64)**. Le *plan_handle* peut être obtenu à partir des objets de gestion dynamique suivants :  
  
-   [Sys.dm_exec_cached_plans &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
-   [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-   [Sys.dm_exec_requests &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
## <a name="table-returned"></a>Table retournée  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**usecounts**|**int**|Nombre d'utilisations du curseur ou contexte d'utilisation.<br /><br /> Colonne n'acceptant pas la valeur NULL.|  
|**memory_object_address**|**varbinary (8)**|Adresse mémoire du curseur ou contexte d'utilisation.<br /><br /> Colonne n'acceptant pas la valeur NULL.|  
|**cacheobjtype**|**nvarchar(50)**|Type d’objet de cache de Plan. Colonne n'acceptant pas la valeur NULL. Les valeurs possibles sont<br /><br /> Plan exécutable<br /><br /> Fonction compilée par le CLR<br /><br /> Procédure compilée par le CLR<br /><br /> Curseur|  
  
## <a name="permissions"></a>Permissions  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="physical-joins"></a>Jointures physiques  
 ![Diagramme des relations](../../relational-databases/system-dynamic-management-views/media/dm-dependent-objects.gif "diagramme des relations")  
  
## <a name="relationship-cardinalities"></a>Cardinalités de la relation  
  
|De|Pour|Le|Relation|  
|----------|--------|--------|------------------|  
|**dm_exec_cached_plan_dependent_objects**|**dm_os_memory_objects**|**memory_object_address**|Un à un|  
  
## <a name="see-also"></a>Voir aussi  
 [Les fonctions et vues de gestion dynamique &#40; liées à l’exécution Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Sys.syscacheobjects &#40; Transact-SQL &#41;](../../relational-databases/system-compatibility-views/sys-syscacheobjects-transact-sql.md)  
  
  

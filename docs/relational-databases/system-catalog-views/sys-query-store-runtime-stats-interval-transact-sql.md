---
title: sys. query_store_runtime_stats_interval (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/23/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- QUERY_STORE_RUNTIME_STATS_INTERVAL
- SYS.QUERY_STORE_RUNTIME_STATS_INTERVAL
- QUERY_STORE_RUNTIME_STATS_INTERVAL_TSQL
- SYS.QUERY_STORE_RUNTIME_STATS_INTERVAL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.query_store_runtime_stats_interval catalog view
- query_store_runtime_stats_interval catalog view
ms.assetid: 2be83785-0569-41a3-88c8-59bfa0932e6e
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||= azure-sqldw-latest||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c76e22bc0041c69ffc8ab9d0632ff69f8518031b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68067946"
---
# <a name="sysquery_store_runtime_stats_interval-transact-sql"></a>sys. query_store_runtime_stats_interval (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Contient des informations sur l’heure de début et de fin de chaque intervalle au cours desquelles les informations des statistiques d’exécution du runtime pour une requête ont été collectées.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**runtime_stats_interval_id**|**bigint**|Clé primaire|
|**start_time**|**datetimeoffset**|Heure de début de l’intervalle.|
|**end_time**|**datetimeoffset**|Heure de fin de l’intervalle.|
|**Commentaire**|**nvarchar(32)**|Toujours NULL.|
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’autorisation **View Database State** .  
  
## <a name="see-also"></a>Voir aussi  
 [sys. database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys. query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys. query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys. query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys. query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys. query_store_runtime_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [Analyse des performances à l’aide de l’Magasin des requêtes](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Affichages catalogue &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Procédures stockées du Magasin des requêtes &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  

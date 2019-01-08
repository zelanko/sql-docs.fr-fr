---
title: Sys.query_store_query_text (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/29/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SYS.QUERY_STORE_QUERY_TEXT
- QUERY_STORE_QUERY_TEXT
- SYS.QUERY_STORE_QUERY_TEXT_TSQL
- QUERY_STORE_QUERY_TEXT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.query_store_query_text catalog view
- query_store_query_text catalog view
ms.assetid: f7032fa0-7c16-4492-bb82-685806c63a8c
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8b5fe04b5852eeebc858067505eaa0342ad8cb87
ms.sourcegitcommit: c7febcaff4a51a899bc775a86e764ac60aab22eb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2018
ms.locfileid: "52712240"
---
# <a name="sysquerystorequerytext-transact-sql"></a>Sys.query_store_query_text (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Contient le [!INCLUDE[tsql](../../includes/tsql-md.md)] texte et le handle SQL de la requête.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**query_text_id**|**bigint**|Clé primaire.|  
|**query_sql_text**|**nvarchar(max)**|Texte SQL de la requête, tel que fourni par l’utilisateur. Inclut des espaces blancs, des indicateurs et des commentaires.|  
|**statement_sql_handle**|**vabinary(64)**|Handle SQL de la requête individuelle.|  
|**is_part_of_encrypted_module**|**bit**|Texte de la requête fait partie d’un module de cryptée.|  
|**has_restricted_text**|**bit**|Texte de la requête contient un mot de passe ou d’autres mots unmentionable.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite le **VIEW DATABASE STATE** autorisation.  
  
## <a name="see-also"></a>Voir aussi  
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [Sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_runtime_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Analyse des performances à l'aide du magasin de requêtes](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Procédures stockées du Magasin des requêtes &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)   
 [sys.fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)  
  
  

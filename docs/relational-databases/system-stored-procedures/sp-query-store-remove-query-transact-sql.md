---
title: sp_query_store_remove_query (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SP_QUERY_STORE_REMOVE_QUERY
- SP_QUERY_STORE_REMOVE_QUERY_TSQL
- SYS.SP_QUERY_STORE_REMOVE_QUERY
- SYS.SP_QUERY_STORE_REMOVE_QUERY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_query_store_remove_query
- sp_query_store_remove_query
ms.assetid: cc39ca92-3cba-478e-beef-65560aa84007
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cb6c495252d0ed8a312b8e7727385e8eb21ad4ed
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58526301"
---
# <a name="spquerystoreremovequery-transact-sql"></a>sp_query_store_remove_query (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Supprime la requête, ainsi que tous les plans et les statistiques d’exécution à partir du magasin de requête.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_query_store_remove_query [ @query_id = ] query_id [;]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @query_id = ] query_id` Est l’id de la requête doit être supprimé du magasin de requête. *query_id* est un **bigint**, sans valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
  
## <a name="permissions"></a>Autorisations  
 Nécessite le **EXECUTE** autorisation sur la base de données, et **supprimer** autorisation sur les affichages catalogue du magasin de requête.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant retourne des informations sur les requêtes dans le magasin de requêtes.  
  
```  
SELECT Txt.query_text_id, Txt.query_sql_text, Pl.plan_id, Qry.*  
FROM sys.query_store_plan AS Pl  
JOIN sys.query_store_query AS Qry  
    ON Pl.query_id = Qry.query_id  
JOIN sys.query_store_query_text AS Txt  
    ON Qry.query_text_id = Txt.query_text_id ;  
```  
  
 Après avoir identifié le query_id que vous souhaitez supprimer, utilisez l’exemple suivant pour supprimer la requête.  
  
 L'exemple suivant.  
  
```  
EXEC sp_query_store_remove_query 3;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_query_store_force_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)   
 [sp_query_store_remove_plan &#40;Transct-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql.md)   
 [sp_query_store_unforce_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)   
 [sp_query_store_reset_exec_stats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql.md)   
 [sp_query_store_flush_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-flush-db-transact-sql.md)   
 [Affichages catalogue du Magasin des requêtes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)   
 [Analyse des performances à l'aide du magasin de requêtes](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)  
  
  

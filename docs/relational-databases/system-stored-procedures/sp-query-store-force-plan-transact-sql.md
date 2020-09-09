---
description: sp_query_store_force_plan (Transact-SQL)
title: sp_query_store_force_plan (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SYS.SP_QUERY_STORE_FORCE_PLAN
- SP_QUERY_STORE_FORCE_PLAN
- SYS.SP_QUERY_STORE_FORCE_PLAN_TSQL
- SP_QUERY_STORE_FORCE_PLAN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_query_store_force_plan
- sp_query_store_force_plan
ms.assetid: 0068f258-b998-4e4e-b47b-e375157c8213
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 503305e4e1954f7d549244bee058ad449c975ec7
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89534974"
---
# <a name="sp_query_store_force_plan-transact-sql"></a>sp_query_store_force_plan (Transact-SQL)

[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

Active le forçage d’un plan particulier pour une requête particulière.  
  
 Lorsqu’un plan est forcé pour une requête donnée, chaque fois [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qu’il rencontre une requête, il tente de forcer le plan dans l’optimiseur de requête. Si le forçage de plan échoue, un événement étendu est déclenché et l’optimiseur de requête est invité à optimiser de manière normale.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sp_query_store_force_plan [ @query_id = ] query_id , [ @plan_id = ] plan_id [;]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @query_id = ] query_id` ID de la requête. *query_id* est de type **bigint**, sans valeur par défaut.  
  
`[ @plan_id = ] plan_id` ID du plan de requête à forcer. *plan_id* est de type **bigint**, sans valeur par défaut.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’autorisation **ALTER** sur la base de données.
  
## <a name="examples"></a>Exemples  
 L’exemple suivant retourne des informations sur les requêtes dans le magasin de requêtes.  
  
```sql  
SELECT Txt.query_text_id, Txt.query_sql_text, Pl.plan_id, Qry.*  
FROM sys.query_store_plan AS Pl  
JOIN sys.query_store_query AS Qry  
    ON Pl.query_id = Qry.query_id  
JOIN sys.query_store_query_text AS Txt  
    ON Qry.query_text_id = Txt.query_text_id ;  
```  
  
 Après avoir identifié les query_id et les plan_id que vous souhaitez imposer, utilisez l’exemple suivant pour forcer la requête à utiliser un plan.  
  
```sql  
EXEC sp_query_store_force_plan 3, 3;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_query_store_remove_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql.md)   
 [sp_query_store_remove_query &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql.md)   
 [sp_query_store_unforce_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)   
 [Affichages catalogue Magasin des requêtes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)   
 [Analyse des performances à l’aide de l’Magasin des requêtes](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [sp_query_store_reset_exec_stats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql.md)   
 [sp_query_store_flush_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-flush-db-transact-sql.md)       
 [Bonnes pratiques relatives au Magasin des requêtes](../../relational-databases/performance/best-practice-with-the-query-store.md#CheckForced)    
  
  

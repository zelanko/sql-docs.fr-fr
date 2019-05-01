---
title: sys.dm_exec_query_plan_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/23/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_exec_query_plan_stats
- sys.dm_exec_query_plan_stats_TSQL
- dm_exec_query_plan_stats_TSQL
- dm_exec_query_plan_stats
helpviewer_keywords:
- sys.dm_exec_query_plan_stats management view
ms.assetid: fdc7659e-df41-488e-b2b5-0d79734dfacb
author: pmasl
ms.author: pelopes
manager: amitban
ms.openlocfilehash: 89185976120c15f9d1fcdfef75f2bddb41415c65
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63474279"
---
# <a name="sysdmexecqueryplanstats-transact-sql"></a>sys.dm_exec_query_plan_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-asdb-xxxx-xxx.md)]

Retourne l’équivalent du dernier plan d’exécution réel connu pour un plan de requête mis en cache précédemment. 

## <a name="syntax"></a>Syntaxe

```
sys.dm_exec_query_plan_stats(plan_handle)  
``` 

## <a name="arguments"></a>Arguments 
*plan_handle*  
Est un jeton qui identifie de façon unique un plan d’exécution de requête pour un lot qui a été exécutée et son plan réside dans le cache du plan, ou est en cours d’exécution. *plan_handle* est **varbinary (64)**.   

Le *plan_handle* peut être obtenu à partir d’objets de gestion dynamique suivants :  
  
-   [sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
-   [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-   [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  

-   [sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)  

-   [sys.dm_exec_trigger_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)  

## <a name="table-returned"></a>Table retournée

|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|
|**dbid**|**smallint**|ID de la base de données de contexte qui était en fonction lorsque l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] correspondant à ce plan a été compilée. Pour les instructions SQL ad hoc et préparées, l'ID de la base de données où les instructions ont été compilées.<br /><br /> Colonne acceptant la valeur NULL.|  
|**objectid**|**Int**|ID de l'objet (par exemple, procédure stockée ou fonction définie par l'utilisateur) pour ce plan de requête. Pour les traitements ad hoc et préparées, cette colonne est **null**.<br /><br /> Colonne acceptant la valeur NULL.|  
|**nombre**|**smallint**|Entier servant à la numérotation des procédures stockées. Par exemple, un groupe de procédures pour le **commandes** application peut être nommée **orderproc ; 1**, **orderproc ; 2**, et ainsi de suite. Pour les traitements ad hoc et préparées, cette colonne est **null**.<br /><br /> Colonne acceptant la valeur NULL.|  
|**encrypted**|**bit**|Indique si la procédure stockée correspondante est chiffrée.<br /><br /> 0 = Non chiffrée.<br /><br /> 1 = Chiffrée.<br /><br /> Colonne n'acceptant pas la valeur NULL.|  
|**query_plan**|**xml**|Contient le dernier runtime connu Showplan représentation le plan d’exécution réel qui est spécifié avec *plan_handle*. Le plan d'exécution de requêtes est au format XML. Un plan est généré pour chaque traitement contenant par exemple des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] ad hoc, des appels de procédures stockées et des appels de fonctions définies par l'utilisateur.<br /><br /> Colonne acceptant la valeur NULL.| 

## <a name="remarks"></a>Notes
Cette fonction système est disponible à partir de [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 2.4.

Il s’agit d’une fonctionnalité d’activation qui nécessite l’activation de l’[indicateur de trace](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451. En commençant par [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 2.5 et dans [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], pour effectuer cette opération au niveau de la base de données, consultez l’option LAST_QUERY_PLAN_STATS dans [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).

Cette fonction système fonctionne sous le **léger** infrastructure de profilage des statistiques d’exécution de requête. Pour plus d’informations, consultez [Infrastructure du profilage de requête](../../relational-databases/performance/query-profiling-infrastructure.md).  

Dans les conditions suivantes, un plan de requête de sortie **équivalent à un plan d’exécution réel** est retourné dans le **query_plan** colonne de la table retournée pour **sys.dm_exec_query_plan_ statistiques**:  

-   Le plan se trouve dans [sys.dm_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md).     
    **AND**    
-   La requête en cours d’exécution est complexe ou la consommation de ressources.

Dans les conditions suivantes, un **simplifiée <sup>1</sup>**  sortie Showplan est retournée dans le **query_plan** colonne de la table retournée pour **sys.dm_exec_ query_plan_stats**:  

-   Le plan se trouve dans [sys.dm_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md).     
    **AND**    
-   La requête est assez simple, généralement classés en tant que partie d’une charge de travail OLTP.

<sup>1</sup> compter [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 2.5, cela fait référence à un plan de requête qui contient uniquement l’opérateur de nœud racine (SELECT). Pour [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] cela fait référence au plan de mise en cache comme étant disponibles par le biais de CTP 2.4 `sys.dm_exec_cached_plans`.

Dans les conditions suivantes, **aucune sortie est retournée** de **sys.dm_exec_query_plan_stats**:

-   Le plan de requête est spécifié à l’aide de *plan_handle* a été supprimé du cache du plan.     
    **OR**    
-   Le plan de requête n’a pas mis en cache en premier lieu. Pour plus d’informations, consultez [l’exécution de planifier la mise en cache et réutilisation ](../../relational-databases/query-processing-architecture-guide.md#execution-plan-caching-and-reuse).
  
> [!NOTE] 
> En raison d’une limitation du nombre de niveaux imbriqués autorisés dans les **xml** type de données, **sys.dm_exec_query_plan** ne peut pas retourner des plans de requête qui correspondent ou sont supérieurs à 128 niveaux d’éléments imbriqués. Dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cette condition a empêché le plan de requête retournant et génère [erreur 6335](../../relational-databases/errors-events/database-engine-events-and-errors.md#errors-6000-to-6999). Dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 et versions ultérieures, le **query_plan** colonne retourne NULL.  

## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation `VIEW SERVER STATE` sur le serveur.  

## <a name="examples"></a>Exemples  
  
### <a name="a-looking-at-last-known-actual-query-execution-plan-for-a-specific-cached-plan"></a>A. Recherchez au dernier plan d’exécution réel connu un plan mis en cache spécifique  
 L’exemple suivant interroge **sys.dm_exec_cached_plans** pour rechercher le plan vous intéresse et copie son `plan_handle` à partir de la sortie.  
  
```sql  
SELECT * FROM sys.dm_exec_cached_plans;  
GO  
```  
  
Pour obtenir le dernier connus réel plan d’exécution, utilisez ensuite copié `plan_handle` avec la fonction système **sys.dm_exec_query_plan_stats**.  
  
```sql  
SELECT * FROM sys.dm_exec_query_plan_stats(< copied plan_handle >);  
GO  
```   

### <a name="b-looking-at-last-known-actual-query-execution-plan-for-all-cached-plans"></a>B. Recherchez au dernier plan d’exécution réel connus tous les plans mis en cache
  
```sql  
SELECT *   
FROM sys.dm_exec_cached_plans AS cp
CROSS APPLY sys.dm_exec_sql_text(plan_handle) AS st
CROSS APPLY sys.dm_exec_query_plan_stats(plan_handle) AS qps;  
GO  
```   

### <a name="c-looking-at-last-known-actual-query-execution-plan-for-a-specific-cached-plan-and-query-text"></a>C. Recherchez au dernier plan d’exécution réel connu un plan mis en cache spécifique et le texte de la requête

```sql  
SELECT *   
FROM sys.dm_exec_cached_plans AS cp
CROSS APPLY sys.dm_exec_sql_text(plan_handle) AS st
CROSS APPLY sys.dm_exec_query_plan_stats(plan_handle) AS qps
WHERE st.text LIKE 'SELECT * FROM Person.Person%';  
GO  
```   

### <a name="d-look-at-cached-events-for-trigger"></a>D. Examinez les événements mis en cache pour le déclencheur

```sql
SELECT *
FROM sys.dm_exec_cached_plans
CROSS APPLY sys.dm_exec_query_plan_stats(plan_handle)
WHERE objtype ='Trigger';
GO
```

## <a name="see-also"></a>Voir aussi
  [Indicateurs de trace](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Vues de gestion dynamique liées à l’exécution &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  


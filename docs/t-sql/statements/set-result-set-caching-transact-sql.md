---
title: DÉFINIR LA MISE EN CACHE DU JEU DE RÉSULTATS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/03/2019
ms.prod: sql
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.technology: t-sql
ms.topic: language-reference
f1_keywords: ''
dev_langs:
- TSQL
helpviewer_keywords: ''
author: XiaoyuL-Preview
ms.author: xiaoyul
manager: craigg
monikerRange: =azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: cd0141a6fbd21c11f7401fa2c45dae0cc75b983d
ms.sourcegitcommit: ccea98fa0768d01076cb6ffef0b4bdb221b2f9d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2019
ms.locfileid: "65561492"
---
# <a name="set-result-set-caching-transact-sql"></a>DÉFINIR LA MISE EN CACHE DU JEU DE RÉSULTATS (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Entraine la mise en cache des jeux de résultats de requête par Azure SQL Data Warehouse.
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe

```
SET RESULT_SET_CACHING { ON | OFF };
```  
  
## <a name="remarks"></a>Notes   
  
Cette commande doit être exécutée lorsque vous êtes connecté à la base de données master.  La modification de ce paramètre de base de données prend effet immédiatement.  Des coûts de stockage sont facturés en mettant en cache des jeux de résultats de requête. Après avoir désactivé la mise en cache de résultats pour une base de données, le cache de résultats rendu persistant auparavant sera immédiatement supprimé depuis le stockage Azure SQL Data Warehouse. Une nouvelle colonne nommée is_result_set_caching_on est introduite dans [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql?view=azure-sqldw-latest
) pour afficher le paramètre de mise en cache de résultats pour une base de données.  

**ACTIF** Spécifie que les jeux de résultats de requête retournés à partir de cette base de données seront mis en cache dans le stockage Azure SQL Data Warehouse.

**INACTIF** Spécifie que les jeux de résultats de requête retournés à partir de cette base de données ne seront pas mis en cache dans le stockage Azure SQL Data Warehouse.

Les utilisateurs peuvent indiquer si une requête a été exécutée avec une correspondance dans le cache de résultats ou absence dans le cache en interrogeant [sys.pdw_request_steps](/sql/relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql?view=azure-sqldw-latest) avec un request_id spécifique. S’il existe une correspondance dans le cache, le résultat de la requête aura une seule étape avec les détails suivants :

|**Nom de colonne**|**Opérateur**|**Value**|
|----|----|----|
|operation_type|=|ReturnOperation|
|step_index|=|0|
|location_type|=|Control|
|commande|Correspond à|%DWResultCacheDb%|
||||
  
## <a name="permissions"></a>Autorisations

Nécessite ces autorisations :

- Connexion au principal au niveau du serveur (celle créée par le processus de provisionnement) ou
- Membre du rôle de base de données dbmanager.

Le propriétaire de la base de données ne peut pas modifier la base de données à moins d'être membre du rôle dbmanager.
  
## <a name="examples"></a>Exemples

### <a name="enable-result-set-caching-for-a-database"></a>Activer la mise en cache d’un jeu de résultats pour une base de données

```sql
ALTER DATABASE myTestDW  
SET RESULT_SET_CACHING ON;
```

### <a name="disable-result-set-caching-for-a-database"></a>Désactiver la mise en cache d’un jeu de résultats pour une base de données

```sql
ALTER DATABASE myTestDW  
SET RESULT_SET_CACHING OFF;
```

### <a name="check-result-set-caching-setting-for-a-database"></a>Vérifier le paramètre de mise en cache d’un jeu de résultats pour une base de données

```sql
SELECT name, is_result_set_caching  
FROM sys.databases
```

### <a name="check-for-number-of-queries-with-result-set-cache-hit-and-cache-miss"></a>Vérifiez le nombre de requêtes avec correspondance dans le cache du jeu de résultats et absence dans le cache

```sql
SELECT  
Queries=CacheHits+CacheMisses,
CacheHits,
CacheMisses,
CacheHitPct=CacheHits*1.0/(CacheHits+CacheMisses)
FROM  
(SELECT  
CacheHits=count(distinct case when s.command like '%DWResultCacheDb%' and
r.resource_class IS NULL and s.operation_type = 'ReturnOperation' and  
s.step_index = 0 then s.request_id else null end) ,
CacheMisses=count(distinct case when r.resource_class IS NOT NULL then  
s.request_id else null end)
     FROM sys.dm_pdw_request_steps s  
     JOIN sys.dm_pdw_exec_requests r  
     ON s.request_id = r.request_id) A
```

### <a name="check-for-result-set-cache-hit-or-cache-miss-for-a-query"></a>Vérifiez la correspondance dans le cache ou l’absence dans le cache du jeu de résultats pour une requête

```sql
If
(SELECT step_index  
FROM sys.dm_pdw_request_steps  
WHERE request_id = 'QID58286'
      and operation_type = 'ReturnOperation'
      and command like '%DWResultCacheDb%') = 0
SELECT 1 as is_cache_hit  
ELSE
SELECT 0 as is_cache_hit
```

### <a name="check-for-all-queries-with-result-set-cache-hits"></a>Vérifiez toutes les requêtes avec correspondances dans le cache du jeu de résultats

```sql
SELECT *  
FROM sys.dm_pdw_request_steps  
WHERE command like '%DWResultCacheDb%' and step_index = 0
```

## <a name="see-also"></a> Voir aussi

[Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)</br>
[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql?view=azure-sqldw-latest)
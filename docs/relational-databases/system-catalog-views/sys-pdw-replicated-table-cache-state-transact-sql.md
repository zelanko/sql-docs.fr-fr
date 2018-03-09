---
title: sys.pdw_replicated_table_cache_state (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/03/2017
ms.prod: 
ms.prod_service: sql-data-warehouse
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff;barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a718827a478137a877b7b1130f3e80a5cbd05fc9
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="syspdwreplicatedtablecachestate-transact-sql"></a>sys.pdw_replicated_table_cache_state (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

  Retourne l’état du cache associé à une table répliquée par **object_id**.  
  
|Nom de la colonne|Type de données| Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|L’ID d’objet pour la table. Consultez [sys.objects &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).<br /><br /> **object_id** est la clé pour cette vue.||  
|state|**nvarchar(40)**|L’état du cache de table répliquée pour cette table.|« NotReady », « Prêt »|  
  
## <a name="example"></a>Exemple
Cet exemple joint sys.pdw_replicated_table_cache_state avec sys.tables pour récupérer le nom de table et l’état du cache de la table répliquée.

```sql
SELECT t.[name], p.[object_id], p.[state]
  FROM sys.pdw_replicated_table_cache_state p 
  JOIN sys.tables t ON t.object_id = p.object_id
```



## <a name="next-steps"></a>Étapes suivantes  
 Pour obtenir la liste de toutes les vues de catalogue pour SQL Data Warehouse et Parallel Data Warehouse, consultez [SQL Data Warehouse et les vues du catalogue Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md).   
  

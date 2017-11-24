---
title: Sys.pdw_replicated_table_cache_state (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/03/2017
ms.prod: 
ms.prod_service: sql-data-warehouse
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
author: ronortloff
ms.author: rortloff;barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 700ebe6ee06ebbcccf9c1388cb3a4f8015a26669
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwreplicatedtablecachestate-transact-sql"></a>Sys.pdw_replicated_table_cache_state (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

  Retourne l’état du cache associé à une table répliquée par **object_id**.  
  
|Nom de la colonne|Type de données| Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|L’ID d’objet pour la table. Consultez [sys.objects &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).<br /><br /> **object_id** est la clé pour cette vue.||  
|state|**nvarchar (40)**|L’état du cache de table répliquée pour cette table.|« NotReady », « Prêt »|  
  
## <a name="example"></a>Exemple
Cet exemple joint sys.pdw_replicated_table_cache_state avec sys.tables pour récupérer le nom de table et l’état du cache de la table répliquée.

```sql
SELECT t.[name], p.[object_id], p.[state]
  FROM sys.pdw_replicated_table_cache_state p 
  JOIN sys.tables t ON t.object_id = p.object_id
```



## <a name="next-steps"></a>Étapes suivantes  
 Pour obtenir la liste de toutes les vues de catalogue pour SQL Data Warehouse et Parallel Data Warehouse, consultez [SQL Data Warehouse et les vues du catalogue Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md).   
  

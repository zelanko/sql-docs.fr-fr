---
title: sys.pdw_replicated_table_cache_state (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2017
ms.prod: sql
ms.technology: data-warehousee"
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 02fa0d4efa6c90c2bfc5840971d8de7f50cb9a7c
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56016583"
---
# <a name="syspdwreplicatedtablecachestate-transact-sql"></a>sys.pdw_replicated_table_cache_state (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

  Retourne l’état du cache associé à une table répliquée par **object_id**.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**Int**|L’ID d’objet pour la table. See [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).<br /><br /> **object_id** est la clé pour cette vue.||  
|state|**nvarchar(40)**|L’état du cache de table répliquée pour cette table.|'NotReady','Ready'|  
  
## <a name="example"></a>Exemple
Cet exemple joint sys.pdw_replicated_table_cache_state avec sys.tables pour récupérer le nom de table et l’état du cache de la table répliquée.

```sql
SELECT t.[name], p.[object_id], p.[state]
  FROM sys.pdw_replicated_table_cache_state p 
  JOIN sys.tables t ON t.object_id = p.object_id
```



## <a name="next-steps"></a>Étapes suivantes  
 Pour obtenir la liste de toutes les vues de catalogue pour SQL Data Warehouse et Parallel Data Warehouse, consultez [SQL Data Warehouse et les vues du catalogue Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md).   
  

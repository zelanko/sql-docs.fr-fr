---
description: sys.pdw_replicated_table_cache_state (Transact-SQL)
title: sys.pdw_replicated_table_cache_state (Transact-SQL)
ms.custom: seo-dt-2019
ms.date: 07/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 19a5132bd78b3cc1cca48be193b34126a9f83c3e
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92036893"
---
# <a name="syspdw_replicated_table_cache_state-transact-sql"></a>sys.pdw_replicated_table_cache_state (Transact-SQL)
[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

  Retourne l’état du cache associé à une table répliquée par **object_id**.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|ID d’objet de la table. Consultez [sys. objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).<br /><br /> **object_id** est la clé de cette vue.||  
|state|**nvarchar(40)**|État du cache de la table répliquée pour cette table.|« Nochapy », « Ready »|  
  
## <a name="example"></a>Exemple
Cet exemple joint sys.pdw_replicated_table_cache_state avec sys. tables pour récupérer le nom de la table et l’état du cache de la table répliquée.

```sql
SELECT t.[name], p.[object_id], p.[state]
  FROM sys.pdw_replicated_table_cache_state p 
  JOIN sys.tables t ON t.object_id = p.object_id
```



## <a name="next-steps"></a>Étapes suivantes  
 Pour obtenir la liste de tous les affichages catalogue pour l’analyse Azure Synapse et les Data Warehouse parallèles, consultez [Azure Synapse Analytics et les affichages catalogue parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md).   
  

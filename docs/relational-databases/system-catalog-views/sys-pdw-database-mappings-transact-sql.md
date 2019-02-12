---
title: sys.pdw_database_mappings (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 4ae2c71e-dd56-41ea-a16b-64936175b459
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 1a07d8074c4d7de7ebe9fea214f4d00ea25d3a3e
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56012933"
---
# <a name="syspdwdatabasemappings-transact-sql"></a>sys.pdw_database_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Mappages le **database_id**s des bases de données pour le nom physique utilisé sur les nœuds de calcul et fournit le **id du principal** du propriétaire de base de données sur le système. Joindre **sys.pdw_database_mappings** à **sys.databases** et **sys.pdw_nodes_pdw_physical_databases**.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|physical_name|**nvarchar(36)**|Le nom physique de la base de données sur les nœuds de calcul.<br /><br /> **physical_name** et **database_id** forment la clé pour cette vue.||  
|database_id|**Int**|L’ID d’objet pour la base de données. Consultez [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).<br /><br /> **physical_name** et **database_id** forment la clé pour cette vue.||  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L’exemple suivant joint sys.pdw_database_mappings à d’autres tables système pour montrer comment les bases de données sont mappés.  
  
```  
SELECT DB.database_id, DB.name, Map.*, Phys.*   
FROM sys.databases AS DB  
JOIN sys.pdw_database_mappings AS Map  
    ON DB.database_id = Map.database_id  
JOIN sys.pdw_nodes_pdw_physical_databases AS Phys  
    ON Map.physical_name = Phys.physical_name  
ORDER BY DB.database_id, Phys.pdw_node_id;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et les vues de catalogue Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [sys.pdw_index_mappings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-index-mappings-transact-sql.md)   
 [sys.pdw_table_mappings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-table-mappings-transact-sql.md)   
 [sys.pdw_nodes_pdw_physical_databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-pdw-physical-databases-transact-sql.md)  
  
  


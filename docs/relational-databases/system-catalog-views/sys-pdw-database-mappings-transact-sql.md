---
title: Sys.pdw_database_mappings (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 10/17/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 4ae2c71e-dd56-41ea-a16b-64936175b459
caps.latest.revision: "9"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5a08d9b0fdb770918c1bb7c8b08e253af58be314
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwdatabasemappings-transact-sql"></a>Sys.pdw_database_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Mappe le **database_id**s des bases de données pour le nom physique utilisé sur les nœuds de calcul et fournit le **id du principal** du propriétaire de base de données sur le système. Joindre **sys.pdw_database_mappings** à **sys.databases** et **sys.pdw_nodes_pdw_physical_databases**.  
  
|Nom de la colonne|Type de données| Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|physical_name|**nvarchar(36)**|Le nom physique de la base de données sur les nœuds de calcul.<br /><br /> **physical_name** et **database_id** forment la clé pour cette vue.||  
|database_id|**int**|L’ID d’objet pour la base de données. Consultez [sys.databases &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).<br /><br /> **physical_name** et **database_id** forment la clé pour cette vue.||  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Exemples :[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L’exemple suivant joint sys.pdw_database_mappings à d’autres tables système pour afficher la façon dont les bases de données sont mappés.  
  
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
 [Entrepôt de données SQL et les vues de catalogue de l’entrepôt de données en parallèle](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [Sys.pdw_index_mappings &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-pdw-index-mappings-transact-sql.md)   
 [Sys.pdw_table_mappings &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-pdw-table-mappings-transact-sql.md)   
 [Sys.pdw_nodes_pdw_physical_databases &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-pdw-physical-databases-transact-sql.md)  
  
  


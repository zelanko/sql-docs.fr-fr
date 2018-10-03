---
title: Sys.pdw_nodes_partitions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: b4216752-4813-4b2c-b259-7d8ffc6cc190
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: aadbe305d7ad72858a46b1df2af4ef2cb0e940be
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47843357"
---
# <a name="syspdwnodespartitions-transact-sql"></a>Sys.pdw_nodes_partitions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient une ligne pour chaque partition de toutes les tables et la plupart des types d’index dans un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] base de données. Toutes les tables et index contiennent au moins une partition, s’ils sont explicitement partitionnés.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|partition_id|`bigint`|ID de la partition. Unique dans une base de données.|  
|object_id|`int`|ID de l’objet auquel appartient cette partition. Chaque table ou vue comporte au moins une partition.|  
|index_id|`int`|ID de l’index de l’objet auquel appartient cette partition.|  
|partition_number|`int`|numéro de partition de base 1 dans l’index ou le segment de mémoire propriétaire. Pour [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], la valeur de cette colonne est 1.|  
|hobt_id|`bigint`|ID du segment de données ou de l'arbre B qui contient les lignes de cette partition.|  
|lignes|`bigint`|Nombre approximatif de lignes dans cette partition. |  
|data_compression|`int`|Indique l'état de compression pour chaque partition :<br /><br /> 0 = AUCUN<br /><br /> 1 = LIGNE<br /><br /> 2 = PAGE<br /><br /> 3 = COLUMNSTORE|  
|data_compression_desc|`nvarchar(60)`|Indique l'état de compression pour chaque partition. Les valeurs possibles sont NONE, ROW et PAGE.|  
|pdw_node_id|`int`|Identificateur unique d’un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] nœud.|  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation CONTROL SERVER.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  

### <a name="example-a-display-rows-in-each-partition-within-each-distribution"></a>Exemple a : lignes d’affichage dans chaque partition dans chaque distribution 

S’applique à : [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]
 
Pour afficher le nombre de lignes dans chaque partition dans chaque distribution, utilisez [DBCC PDW_SHOWPARTITIONSTATS (SQL Server PDW)](../../t-sql/database-console-commands/dbcc-pdw-showpartitionstats-transact-sql.md) .

### <a name="example-b-uses-system-views-to-view-rows-in-each-partition-of-each-distribution-of-a-table"></a>L’exemple b : vues du système utilise pour afficher des lignes dans chaque partition de chaque distribution d’une table

S’applique à : [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]
 
Cette requête retourne le nombre de lignes dans chaque partition de chaque distribution de la table `myTable`.  
 
```  
SELECT o.name, pnp.index_id, pnp.partition_id, pnp.rows,   
    pnp.data_compression_desc, pnp.pdw_node_id  
FROM sys.pdw_nodes_partitions AS pnp  
JOIN sys.pdw_nodes_tables AS NTables  
    ON pnp.object_id = NTables.object_id  
AND pnp.pdw_node_id = NTables.pdw_node_id  
JOIN sys.pdw_table_mappings AS TMap  
    ON NTables.name = TMap.physical_name 
    AND substring(TMap.physical_name,40, 10) = pnp.distribution_id 
JOIN sys.objects AS o  
    ON TMap.object_id = o.object_id  
WHERE o.name = 'myTable'  
ORDER BY o.name, pnp.index_id, pnp.partition_id;  
```    
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et les vues de catalogue Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  


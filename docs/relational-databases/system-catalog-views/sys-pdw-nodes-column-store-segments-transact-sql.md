---
title: Sys.pdw_nodes_column_store_segments (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: e2fdf8e9-1b74-4682-b2d4-c62aca053d7f
caps.latest.revision: "9"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 79944f54d12681ab7a430362ec0204a8d54bf477
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwnodescolumnstoresegments-transact-sql"></a>Sys.pdw_nodes_column_store_segments (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient une ligne pour chaque colonne dans un index columnstore.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|Indique l'ID de partition. Unique dans une base de données.|  
|**hobt_id**|**bigint**|ID du segment ou de l'index d'arbre B (B-tree) pour la table ayant cet index columnstore.|  
|**column_id**|**int**|ID de la colonne columnstore.|  
|**segment_id**|**int**|Retourne le segment de la colonne.|  
|**version**|**int**|Version du format de segment de colonne.|  
|**encoding_type**|**int**|Type d'encodage utilisé pour ce segment.|  
|**row_count**|**int**|Nombre de lignes dans le groupe de lignes.|  
|**has_nulls**|**int**|1 si le segment de colonne a des valeurs NULL.|  
|**base_id**|**bigint**|Id de la valeur de base si le type d’encodage 1 est utilisé.  Si le type d’encodage 1 n'est pas utilisé, ID a la valeur 1.|  
|**ordre de grandeur**|**float**|Grandeur si le type d’encodage 1 est utilisé.  Si le type d’encodage 1 n'est pas utilisé, ordre de grandeur a la valeur 1.|  
|**primary__dictionary_id**|**int**|ID du dictionnaire principal.|  
|**secondary_dictionary_id**|**int**|ID du dictionnaire secondaire. Retourne -1 s'il n'y a aucun dictionnaire secondaire.|  
|**min_data_id**|**bigint**|ID de données minimum dans le segment de colonne.|  
|**max_data_id**|**bigint**|ID de données maximum dans le segment de colonne.|  
|**null_value**|**bigint**|Valeur utilisée pour représenter les valeurs NULL.|  
|**on_disk_size**|**bigint**|Taille de segment en octets.|  
|**pdw_node_id**|**int**|Identificateur unique d’un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Remarque.|  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 La requête suivante retourne des informations sur les segments d'un index columnstore.  
  
```tsql  
SELECT i.name, p.object_id, p.index_id, i.type_desc,   
    COUNT(*) AS number_of_segments  
FROM sys.column_store_segments AS s   
INNER JOIN sys.partitions AS p   
    ON s.hobt_id = p.hobt_id   
INNER JOIN sys.indexes AS i   
    ON p.object_id = i.object_id  
WHERE i.type = 6  
GROUP BY i.name, p.object_id, p.index_id, i.type_desc ;  
```  
  
 Joindre sys.pdw_nodes_column_store_segments avec d’autres tables système pour déterminer le nombre de lignes et de la taille des segments sur le disque.  
  
```  
SELECT o.name, css.hobt_id, css. column_id, css.pdw_node_id, css.row_count, css.on_disk_size  
FROM sys.pdw_nodes_column_store_segments AS css  
JOIN sys.pdw_nodes_partitions AS pnp  
    ON css.partition_id = pnp.partition_id  
JOIN sys.pdw_nodes_tables AS part  
    ON pnp.object_id = part.object_id   
    AND pnp.pdw_node_id = part.pdw_node_id  
JOIN sys.pdw_table_mappings AS TMap  
    ON part.name = TMap.physical_name  
JOIN sys.objects AS o  
    ON TMap.object_id = o.object_id  
ORDER BY css.hobt_id, css.column_id;  
```  
  
## <a name="permissions"></a>Permissions  
 Requiert **VIEW SERVER STATE** autorisation.  
  
## <a name="see-also"></a>Voir aussi  
 [Entrepôt de données SQL et les vues de catalogue de l’entrepôt de données en parallèle](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [CRÉER des INDEX COLUMNSTORE &#40; Transact-SQL &#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)   
 [Sys.pdw_nodes_column_store_row_groups &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-row-groups-transact-sql.md)   
 [Sys.pdw_nodes_column_store_dictionaries &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-dictionaries-transact-sql.md)  
  
  


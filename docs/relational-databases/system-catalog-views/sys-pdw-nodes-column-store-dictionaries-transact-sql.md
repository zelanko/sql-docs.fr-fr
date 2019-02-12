---
title: sys.pdw_nodes_column_store_dictionaries (Transact-SQL) | Microsoft Docs
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.custom: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 7ae1c2e4-45c0-4880-a692-1f299fbcfd19
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 53637fb3ae70cd73e1bbf1cb95a8a4ca3775b812
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56010930"
---
# <a name="syspdwnodescolumnstoredictionaries-transact-sql"></a>sys.pdw_nodes_column_store_dictionaries (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient une ligne pour chaque dictionnaire utilisé dans les index columnstore. Les dictionnaires sont utilisés pour encoder certains, mais pas tous les types de données, par conséquent, certaines colonnes d'un index columnstore n'ont pas de dictionnaires. Un dictionnaire peut exister en tant que dictionnaire principal (pour tous les segments) et éventuellement pour d'autres dictionnaires secondaires utilisés pour un sous-ensemble des segments de la colonne.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|Indique l'ID de partition. Unique dans une base de données.|  
|**hobt_id**|**bigint**|ID du segment ou de l'index d'arbre B (B-tree) pour la table ayant cet index columnstore.|  
|**column_id**|**Int**|ID de la colonne columnstore.|  
|**dictionary_id**|**Int**|ID du dictionnaire.|  
|**version**|**Int**|Version du format de dictionnaire.|  
|**type**|**Int**|Type de dictionnaire :<br /><br /> 1 - dictionnaire de hachage contenant **int** valeurs<br /><br /> 2 - non utilisé<br /><br /> 3 - dictionnaire de hachage contenant des valeurs de chaîne<br /><br /> 4 - dictionnaire de hachage contenant **float** valeurs|  
|**last_id**|**Int**|Dernier ID de données dans le dictionnaire.|  
|**entry_count**|**bigint**|Nombre d'entrées dans le dictionnaire.|  
|**on_disc_size**|**bigint**|Taille du dictionnaire en octets.|  
|**pdw_node_id**|**Int**|Identificateur unique d’un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] nœud.|  
  
## <a name="permissions"></a>Autorisations  
 Requiert l'autorisation VIEW SERVER STATE.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et les vues de catalogue Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)   
 [sys.pdw_nodes_column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-segments-transact-sql.md)   
 [sys.pdw_nodes_column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-row-groups-transact-sql.md)  
  
  

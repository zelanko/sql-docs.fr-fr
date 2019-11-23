---
title: sys. pdw_nodes_column_store_dictionaries (Transact-SQL) | Microsoft Docs
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
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 618a92cfd0f1602753b9fcfd61ac232eff5cecd4
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305184"
---
# <a name="syspdw_nodes_column_store_dictionaries-transact-sql"></a>sys.pdw_nodes_column_store_dictionaries (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient une ligne pour chaque dictionnaire utilisé dans les index ColumnStore. Les dictionnaires sont utilisés pour encoder certains, mais pas tous les types de données, par conséquent, certaines colonnes d'un index columnstore n'ont pas de dictionnaires. Un dictionnaire peut exister en tant que dictionnaire principal (pour tous les segments) et éventuellement pour d'autres dictionnaires secondaires utilisés pour un sous-ensemble des segments de la colonne.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|Indique l'ID de partition. Unique dans une base de données.|  
|**hobt_id**|**bigint**|ID de l’index de segment de mémoire ou arbre B (B-tree) (HoBT) pour la table qui contient cet index ColumnStore.|  
|**column_id**|**int**|ID de la colonne columnstore.|  
|**dictionary_id**|**int**|ID du dictionnaire.|  
|**version**|**int**|Version du format de dictionnaire.|  
|**type**|**int**|Type de dictionnaire :<br /><br /> 1-dictionnaire de hachage contenant des valeurs **int**<br /><br /> 2-non utilisé<br /><br /> 3-dictionnaire de hachage contenant des valeurs de chaîne<br /><br /> 4-dictionnaire de hachage contenant des valeurs **float**|  
|**last_id**|**int**|Dernier ID de données dans le dictionnaire.|  
|**entry_count**|**bigint**|Nombre d'entrées dans le dictionnaire.|  
|**on_disc_size**|**bigint**|Taille du dictionnaire en octets.|  
|**pdw_node_id**|**int**|Identificateur unique d’un nœud de [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation `VIEW SERVER STATE`.  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue SQL Data Warehouse et Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)   
 [sys.pdw_nodes_column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-segments-transact-sql.md)   
 [sys.pdw_nodes_column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-row-groups-transact-sql.md)  
  
  

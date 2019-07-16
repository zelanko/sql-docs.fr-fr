---
title: sys.pdw_nodes_indexes (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 261bcb7f-a906-4979-b274-bc5f1aa66426
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 2eb13830f666d6fbec67566d26abc7614d317f4d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68059309"
---
# <a name="syspdwnodesindexes-transact-sql"></a>sys.pdw_nodes_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Retourne l’index pour [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**Int**|ID de l’objet auquel appartient cet index.||  
|name|**sysname**|Nom de l’index. Nom est unique seulement dans l’objet. NULL = Segment||  
|index_id|**Int**|ID de l’index. index_id est unique seulement dans l’objet.<br /><br /> 0 = Segment de mémoire<br /><br /> 1 = index cluster<br /><br /> > 1 = index Non cluster||  
|type|**tinyint**|Type de l'index :<br /><br /> 0 = Segment de mémoire<br /><br /> 1 = ordonné en clusters<br /><br /> 2 = Non cluster<br /><br /> 5 = index columnstore optimisé en mémoire xVelocity Clustered|  
|type_desc|**nvarchar(60)**|Description du type d'index :<br /><br /> HEAP<br /><br /> CLUSTERED<br /><br /> NONCLUSTERED<br /><br /> CLUSTER COLUMNSTORE||  
|is_unique|**bit**|0 = L'index n'est pas unique.|Toujours 0.|  
|data_space_id|**int**|ID de l’espace de données pour cet index. L'espace de données est soit un groupe de fichiers, soit un schéma de partition.<br /><br /> 0 = object_id est une fonction table.||  
|ignore_dup_key|**bit**|0 = IGNORE_DUP_KEY est OFF.|Toujours 0.|  
|is_primary_key|**bit**|1 = L'index fait partie d'une contrainte PRIMARY KEY.|Toujours 0.|  
|is_unique_constraint|**bit**|1 = L'index fait partie d'une contrainte UNIQUE.|Toujours 0.|  
|fill_factor|**tinyint**|> 0 = pourcentage FILLFACTOR utilisé lorsque l’index a été créé ou reconstruit.<br /><br /> 0 = Valeur par défaut|Toujours 0.|  
|is_padded|**bit**|0 = PADINDEX est OFF.|Toujours 0.|  
|is_disabled|**bit**|1 = L'index est désactivé.<br /><br /> 0 = L'index n'est pas désactivé.||  
|is_hypothetical|**bit**|0 = L'index n'est pas hypothétique.|Toujours 0.|  
|allow_row_locks|**bit**|1 = Index autorisant les verrous de ligne|Toujours 1.|  
|allow_page_locks|**bit**|1 = Index autorisant les verrous de page|Toujours 1.|  
|has_filter|**bit**|0 = Index ne disposant pas de filtre.|Toujours 0.|  
|filter_definition|**nvarchar(max)**|Expression pour le sous-ensemble de lignes inclus dans l'index filtré.|Toujours NULL.|  
|pdw_node_id|**int**|Identificateur unique d’un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] nœud.|NOT NULL|  
  
## <a name="permissions"></a>Autorisations  
 Requiert l'autorisation CONTROL SERVER.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et les vues de catalogue Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  

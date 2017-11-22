---
title: Sys.pdw_nodes_indexes (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/04/2017
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
ms.assetid: 261bcb7f-a906-4979-b274-bc5f1aa66426
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a9dcf0c5cc21d01359c13f13b33914d73a0a7b5f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwnodesindexes-transact-sql"></a>Sys.pdw_nodes_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Retourne l’index pour [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
|Nom de la colonne|Type de données| Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|ID de l’objet auquel appartient cet index.||  
|name|**sysname**|Nom de l’index. Nom est unique que dans l’objet. NULL = Segment||  
|index_id|**int**|ID de l’index. index_id est unique que dans l’objet.<br /><br /> 0 = Segment de mémoire<br /><br /> 1 = index cluster<br /><br /> > 1 = index Non cluster||  
|Type|**tinyint**|Type de l'index :<br /><br /> 0 = Segment de mémoire<br /><br /> 1 = ordonné en clusters<br /><br /> 2 = Non cluster<br /><br /> 5 = Clustered index columnstore optimisé en mémoire xVelocity|  
|type_desc|**nvarchar (60)**|Description du type d'index :<br /><br /> HEAP<br /><br /> CLUSTERED<br /><br /> NONCLUSTERED<br /><br /> COLUMNSTORE EN CLUSTER||  
|is_unique|**bit**|0 = L'index n'est pas unique.|Toujours 0.|  
|data_space_id|**int**|ID de l’espace de données pour cet index. L'espace de données est soit un groupe de fichiers, soit un schéma de partition.<br /><br /> 0 = object_id est une fonction table.||  
|ignore_dup_key|**bit**|0 = IGNORE_DUP_KEY est OFF.|Toujours 0.|  
|is_primary_key|**bit**|1 = L'index fait partie d'une contrainte PRIMARY KEY.|Toujours 0.|  
|is_unique_constraint|**bit**|1 = L'index fait partie d'une contrainte UNIQUE.|Toujours 0.|  
|fill_factor|**tinyint**|> 0 = Pourcentage FILLFACTOR utilisé lorsque l'index a été créé ou reconstruit.<br /><br /> 0 = Valeur par défaut|Toujours 0.|  
|is_padded|**bit**|0 = PADINDEX est OFF.|Toujours 0.|  
|is_disabled|**bit**|1 = L'index est désactivé.<br /><br /> 0 = L'index n'est pas désactivé.||  
|is_hypothetical|**bit**|0 = L'index n'est pas hypothétique.|Toujours 0.|  
|allow_row_locks|**bit**|1 = Index autorisant les verrous de ligne|Toujours 1.|  
|allow_page_locks|**bit**|1 = Index autorisant les verrous de page|Toujours 1.|  
|has_filter|**bit**|0 = Index ne disposant pas de filtre.|Toujours 0.|  
|filter_definition|**nvarchar(max)**|Expression pour le sous-ensemble de lignes inclus dans l'index filtré.|Toujours NULL.|  
|pdw_node_id|**int**|Identificateur unique d’un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] nœud.|NOT NULL|  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation CONTROL SERVER.  
  
## <a name="see-also"></a>Voir aussi  
 [Entrepôt de données SQL et les vues de catalogue de l’entrepôt de données en parallèle](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  

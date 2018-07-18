---
title: Sys.pdw_nodes_columns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-objects
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 268c77b7-1d71-4197-a2ed-5e2b2b8fc260
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 20bb25d3699a6fab734da0974bc0726da7e5cb96
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36875037"
---
# <a name="syspdwnodescolumns-transact-sql"></a>Sys.pdw_nodes_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Affiche les colonnes de tables définies par l’utilisateur et les vues définies par l’utilisateur.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**Int**|Identificateur de l'objet auquel appartient cette colonne.||  
|NAME|**sysname**|Nom de la colonne. Unique dans l’objet.||  
|column_id|**Int**|ID de la colonne. Unique dans l’objet.||  
|system_type_id|**tinyint**|ID du type de système de la colonne.||  
|user_type_id|**Int**|ID du type de colonne tel que défini par l'utilisateur.||  
|max_length|**smallint**|Longueur maximale (en octets) de la colonne.|Inclut -1 (non valide) pour les types de colonnes non pris en charge.|  
|precision|**tinyint**|Précision de la colonne si elle est numérique ; Sinon, 0.||  
|scale|**tinyint**|Échelle de la colonne si elle est numérique ; sinon, la valeur est 0.||  
|collation_name|**sysname**|Nom du classement de la colonne si elle est basée sur des caractères ; Sinon, NULL.||  
|is_nullable|**bit**|1 = La colonne accepte les valeurs NULL.||  
|is_ansi_padded|**bit**|1 = La colonne utilise le comportement ANSI_PADDING ON si elle est de type caractère, binaire ou variant.|Toujours 0.|  
|is_rowguidcol|**bit**|1 = La colonne est un ROWGUIDCOL déclaré.|Toujours 0.|  
|is_identity|**bit**|1 = La colonne comporte des valeurs d'identité.|Toujours 0.|  
|is_computed|**bit**|1 = La colonne est calculée.|Toujours 0.|  
|is_filestream|**bit**|1 = La colonne est une colonne FILESTREAM.|Toujours 0.|  
|is_replicated|**bit**|1 = La colonne est répliquée.|Toujours 0.|  
|is_non_sql_subscribed|**bit**|1 = colonne a un abonné non SQL.|Toujours 0.|  
|is_merge_published|**bit**|1 = La colonne est associée à une publication fusionnée.|Toujours 0.|  
|is_dts_replicated|**bit**|1 = colonne est répliquée à l’aide de SSIS.|Toujours 0.|  
|is_xml_document|**bit**|1 = Le contenu est un document XML complet.|Toujours 0.|  
|xml_collection_id|**Int**|0 = Aucune collection de schéma XML.|Toujours 0.|  
|default_object_id|**Int**|ID de l’objet par défaut ; 0 ne = aucune valeur par défaut.|Toujours 0.|  
|rule_object_id|**Int**|ID de la règle autonome liée à la colonne. <br />0 = Aucune règle autonome.|Toujours 0.|  
|is_sparse|**bit**|1 = La colonne est éparse.|Toujours 0.|  
|is_column_set|**bit**|1 = La colonne est un jeu de colonnes.|Toujours 0.|  
|pdw_node_id|**Int**|Identificateur unique d’un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] nœud.|NOT NULL|  
  
## <a name="permissions"></a>Autorisations  
 Requiert l'autorisation CONTROL SERVER.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et les vues de catalogue Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)  
  
  

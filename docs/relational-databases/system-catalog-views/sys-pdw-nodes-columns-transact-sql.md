---
title: sys. pdw_nodes_columns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 268c77b7-1d71-4197-a2ed-5e2b2b8fc260
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 201af9001703bb8f1dfbdaf2c41151697b945df3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68059404"
---
# <a name="syspdw_nodes_columns-transact-sql"></a>sys. pdw_nodes_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Affiche les colonnes pour les tables définies par l’utilisateur et les vues définies par l’utilisateur.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|Identificateur de l'objet auquel appartient cette colonne.||  
|name|**sysname**|Nom de la colonne. Unique dans l’objet.||  
|column_id|**int**|Identificateur de la colonne. Unique dans l’objet.||  
|system_type_id|**tinyint**|ID du type de système de la colonne.||  
|user_type_id|**int**|ID du type de colonne tel que défini par l'utilisateur.||  
|max_length|**smallint**|Longueur maximale (en octets) de la colonne.|Comprend-1 (non valide) pour les types de colonnes non pris en charge.|  
|precision|**tinyint**|Précision de la colonne si elle est numérique ; sinon, 0.||  
|scale|**tinyint**|Échelle de la colonne si elle est numérique ; sinon, la valeur est 0.||  
|collation_name|**sysname**|Nom du classement de la colonne si elle est basée sur des caractères ; sinon, NULL.||  
|is_nullable|**bit**|1 = La colonne accepte les valeurs NULL.||  
|is_ansi_padded|**bit**|1 = La colonne utilise le comportement ANSI_PADDING ON si elle est de type caractère, binaire ou variant.|Toujours 0.|  
|is_rowguidcol|**bit**|1 = La colonne est un ROWGUIDCOL déclaré.|Toujours 0.|  
|is_identity|**bit**|1 = La colonne comporte des valeurs d'identité.|Toujours 0.|  
|is_computed|**bit**|1 = La colonne est calculée.|Toujours 0.|  
|is_filestream|**bit**|1 = La colonne est une colonne FILESTREAM.|Toujours 0.|  
|is_replicated|**bit**|1 = La colonne est répliquée.|Toujours 0.|  
|is_non_sql_subscribed|**bit**|1 = la colonne a un abonné non-SQL.|Toujours 0.|  
|is_merge_published|**bit**|1 = La colonne est associée à une publication fusionnée.|Toujours 0.|  
|is_dts_replicated|**bit**|1 = la colonne est répliquée à l’aide de SSIS.|Toujours 0.|  
|is_xml_document|**bit**|1 = Le contenu est un document XML complet.|Toujours 0.|  
|xml_collection_id|**int**|0 = Aucune collection de schéma XML.|Toujours 0.|  
|default_object_id|**int**|ID de l’objet par défaut ; 0 = pas de valeur par défaut.|Toujours 0.|  
|rule_object_id|**int**|ID de la règle autonome liée à la colonne. <br />0 = Aucune règle autonome.|Toujours 0.|  
|is_sparse|**bit**|1 = La colonne est éparse.|Toujours 0.|  
|is_column_set|**bit**|1 = La colonne est un jeu de colonnes.|Toujours 0.|  
|pdw_node_id|**int**|Identificateur unique d’un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] nœud.|NOT NULL|  
  
## <a name="permissions"></a>Autorisations  
 Requiert l'autorisation CONTROL SERVER.  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue de la SQL Data Warehouse et des Data Warehouse parallèles](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [sys. all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)  
  
  

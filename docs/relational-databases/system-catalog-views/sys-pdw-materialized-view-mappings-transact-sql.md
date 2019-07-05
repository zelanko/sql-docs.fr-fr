---
title: sys.pdw_materialized_view_mappings (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d62b0e25-3226-4f87-a10a-b3a0d9555e19
author: XiaoyuL-Preview
ms.author: xiaoyul
manager: craigg
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 1dac4496a47b9b6b2beeef07e256805bc66b1e87
ms.sourcegitcommit: e4b241fd92689c2aa6e1f5e625874bd0b807dd01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/04/2019
ms.locfileid: "67566641"
---
# <a name="syspdwmaterializedviewmappings-transact-sql-preview"></a>Sys.pdw_materialized_view_mappings (Transact-SQL) (version préliminaire)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Lie la vue matérialisée pour les noms des objets internes par object_id.

Les colonnes physical_name object_id forment la clé pour cette vue de catalogue.
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|physical_name |**nvarchar(36)**|Le nom physique de la vue matérialisée.|  
|object_id  |**Int**|L’ID d’objet pour la vue matérialisée. Consultez [sys.objects (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql?view=azure-sqldw-latest).| 

## <a name="permissions"></a>Autorisations

Nécessite l’autorisation VIEW DATABASE STATE.
  
## <a name="see-also"></a>Voir aussi

[CRÉER MATERIALIZED VIEW AS SELECT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-materialized-view-as-select-transact-sql?view=azure-sqldw-latest)   
[ALTER MATERIALIZED VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-materialized-view-transact-sql?view=azure-sqldw-latest)   
[EXPLAIN &#40;Transact-SQL&#41;](/sql/t-sql/queries/explain-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_column_distribution_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-column-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_distribution_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-pdw-showmaterializedviewoverhead-transact-sql?view=azure-sqldw-latest)   
[SQL Data Warehouse et les vues de catalogue Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
[Vues système prises en charge dans Azure SQL Data Warehouse](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-system-views)   
[Instructions T-SQL pris en charge dans Azure SQL Data Warehouse](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-statements) 
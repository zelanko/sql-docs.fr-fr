---
description: sys.pdw_materialized_view_mappings (Transact-SQL)
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
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: = azure-sqldw-latest
ms.openlocfilehash: 5d09d97fe51acec8466bcff8f64c3edfbc9316e2
ms.sourcegitcommit: 370cab80fba17c15fb0bceed9f80cb099017e000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97642384"
---
# <a name="syspdw_materialized_view_mappings-transact-sql"></a>sys.pdw_materialized_view_mappings (Transact-SQL)  

[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

Lie la vue matérialisée aux noms d’objets internes en object_id.

Les colonnes physical_name et object_id forment la clé de cet affichage catalogue.
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|physical_name |**nvarchar (36)**|Nom physique de la vue matérialisée.|  
|object_id  |**int**|ID d’objet de la vue matérialisée. Consultez [sys. Objects (Transact-SQL)](./sys-objects-transact-sql.md?view=azure-sqldw-latest&preserve-view=true).| 

## <a name="permissions"></a>Autorisations

Requiert l'autorisation VIEW DATABASE STATE.
  
## <a name="see-also"></a>Voir aussi

[Réglage des performances avec une vue matérialisée](/azure/sql-data-warehouse/performance-tuning-materialized-views)   
[CREATE MATERIALIZED VIEW AS SELECT &#40;Transact-SQL&#41;](../../t-sql/statements/create-materialized-view-as-select-transact-sql.md?view=azure-sqldw-latest&preserve-view=true)   
[ALTER MATERIALIZED VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/alter-materialized-view-transact-sql.md?view=azure-sqldw-latest&preserve-view=true)   
[EXPLAIN &#40;Transact-SQL&#41;](../../t-sql/queries/explain-transact-sql.md?view=azure-sqldw-latest&preserve-view=true)   
[sys.pdw_materialized_view_column_distribution_properties &#40;Transact-SQL&#41;](./sys-pdw-materialized-view-column-distribution-properties-transact-sql.md?view=azure-sqldw-latest&preserve-view=true)   
[sys.pdw_materialized_view_distribution_properties &#40;Transact-SQL&#41;](./sys-pdw-materialized-view-distribution-properties-transact-sql.md?view=azure-sqldw-latest&preserve-view=true)   
[DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-pdw-showmaterializedviewoverhead-transact-sql.md?view=azure-sqldw-latest&preserve-view=true)   
[Vues de catalogue Azure Synapse Analytics et Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
[Vues système prises en charge dans Azure Synapse Analytics](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-system-views)   
[Instructions T-SQL prises en charge dans Azure Synapse Analytics](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-statements)
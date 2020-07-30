---
title: sys. pdw_materialized_view_distribution_properties (Transact-SQL)
ms.custom: seo-dt-2019
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
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: be817e164cfa26baf6264dc83e73fddba82ed435
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87395834"
---
# <a name="syspdw_materialized_view_distribution_properties-transact-sql-preview"></a>sys. pdw_materialized_view_distribution_properties (Transact-SQL) (version préliminaire)

[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

Affiche les vues matérialisées des informations de distribution.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------| 
|object_id|**int**|ID de la vue matérialisée pour laquelle les propriétés de la propriété sont spécifiées.| 
|distribution_policy |**tinyint**|2 = HACHAGE</br>4 = ROUND_ROBIN|  
|distribution_policy_desc |**nvarchar(60)**|HACHAGE, ROUND_ROBIN|  
 
## <a name="permissions"></a>Autorisations

Requiert l'autorisation VIEW DATABASE STATE.
 
## <a name="see-also"></a>Voir aussi

[CREATE MATERIALIZED VIEW AS SELECT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-materialized-view-as-select-transact-sql?view=azure-sqldw-latest)   
[ALTER MATERIALIZED VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-materialized-view-transact-sql?view=azure-sqldw-latest)   
[EXPLIQUER &#40;&#41;Transact-SQL](/sql/t-sql/queries/explain-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_mappings &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-mappings-transact-sql?view=azure-sqldw-latest)   
[DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-pdw-showmaterializedviewoverhead-transact-sql?view=azure-sqldw-latest)   
[Affichages catalogue SQL Data Warehouse et Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
[Affichages système pris en charge dans Azure SQL Data Warehouse](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-system-views)   
[Instructions SQL prises en charge dans Azure SQL Data Warehouse](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-statements)

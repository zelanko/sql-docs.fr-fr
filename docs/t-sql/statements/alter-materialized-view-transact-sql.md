---
title: ALTER MATERIALIZED VIEW (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: jrasnick
ms.technology: data-warehouse
ms.topic: language-reference
f1_keywords:
- ALTER_VIEW_TSQL
- ALTER VIEW
dev_langs:
- TSQL
helpviewer_keywords:
- indexed views [SQL Server], modifying
- views [SQL Server], modifying
- modifying views
- ALTER VIEW statement
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: b03515cb8fa6780f43927327b4afec21b3933acb
ms.sourcegitcommit: 495913aff230b504acd7477a1a07488338e779c6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68809744"
---
# <a name="alter-materialized-view-transact-sql-preview"></a>ALTER MATERIALIZED VIEW (Transact-SQL) (préversion)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Modifie un affichage matérialisé précédemment créé. ALTER VIEW n'affecte pas les procédures stockées ou déclencheurs dépendants et ne modifie pas les autorisations.  
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```
ALTER MATERIALIZED VIEW [ schema_name . ] view_name
{
      REBUILD | DISABLE
}
[;]
```  
  
## <a name="arguments"></a>Arguments

 *schema_name*     
 Nom du schéma auquel appartient la vue.  
  
 *view_name*     
 est l’affichage matérialisé à modifier.  
  
*RÉGÉNÉRER*   
Reprend l’affichage matérialisé.

*DÉSACTIVER*   
Suspend la maintenance sur l’affichage matérialisé tout en conservant les métadonnées et les autorisations.  Toutes les requêtes par rapport à l’affichage matérialisé dans un état désactivé sur les tables sous-jacentes.
  
## <a name="permissions"></a>Autorisations

L’autorisation ALTER sur la table ou l’affichage est requise.
  
## <a name="examples"></a>Exemples

Cet exemple désactive un affichage matérialisé et le place en mode suspendu.
  
```sql
ALTER MATERIALIZED VIEW My_Indexed_View DISABLE;  
```  
  
Cet exemple reprend l’affichage matérialisé en le régénérant.  
  
```sql
ALTER MATERIALIZED VIEW My_Indexed_View REBUILD;  
```  
  
## <a name="see-also"></a>Voir aussi

[CREATE MATERIALIZED VIEW AS SELECT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-materialized-view-as-select-transact-sql?view=azure-sqldw-latest)   
[EXPLAIN &#40;Transact-SQL&#41;](/sql/t-sql/queries/explain-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_column_distribution_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-column-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_distribution_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_mappings &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-mappings-transact-sql?view=azure-sqldw-latest)   
[DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-pdw-showmaterializedviewoverhead-transact-sql?view=azure-sqldw-latest)   
[Affichages catalogue SQL Data Warehouse et Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
[Affichages système pris en charge dans Azure SQL Data Warehouse](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-system-views)   
[Instructions SQL prises en charge dans Azure SQL Data Warehouse](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-statements)

---
title: CREATE MATERIALIZED VIEW AS SELECT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2019
ms.prod: sql
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.technology: data-warehouse
ms.topic: language-reference
f1_keywords:
- CREATE VIEW
- VIEW_TSQL
- VIEW
- CREATE_VIEW_TSQL
- SCHEMABINDING_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- table creation [SQL Server], CREATE VIEW
- views [SQL Server], creating
- CREATE VIEW statement
- updatable partitioned views
- tables [SQL Server], virtual
- updatable views
- modifying partitioned views
- virtual tables [SQL Server]
- number of columns per view
- partitioned views [SQL Server], creating
- WITH ENCRYPTION clause
- WITH CHECK OPTION clause
- partitioned views [SQL Server], modifying
- partitioned views [SQL Server], replication
- distributed partitioned views [SQL Server]
- views [SQL Server], indexed views
- maximum number of columns per view
ms.assetid: aecc2f73-2ab5-4db9-b1e6-2f9e3c601fb9
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: d841f7aa8a5aacfa684b984791a15128b306ab1d
ms.sourcegitcommit: 52d3902e7b34b14d70362e5bad1526a3ca614147
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70109761"
---
# <a name="create-materialized-view-as-select-transact-sql-preview"></a>CREATE MATERIALIZED VIEW AS SELECT (Transact-SQL) (préversion)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Cet article explique l’instruction SQL CREATE MATERIALIZED VIEW AS SELECT T dans Azure SQL Data Warehouse pour développer des solutions. L’article fournit également des exemples de code.

Un affichage matérialisé conserve les données retournées à partir de la requête de définition d’affichage et est automatiquement mis à jour lors des modifications de données dans les tables sous-jacentes.   Il améliore les performances des requêtes complexes (généralement des requêtes avec jointures et agrégations) tout en offrant des opérations de maintenance simple.   Avec sa capacité d’automatching du plan d’exécution, un affichage matérialisé ne devra pas être référencés dans la requête pour que l’optimiseur prenne en compte l’affichage pour substitution.  Ainsi, les ingénieurs de données peuvent implémenter des affichages matérialisés comme un mécanisme pour améliorer les temps de réponse de requête, sans avoir à modifier les requêtes.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CREATE MATERIALIZED VIEW [ schema_name. ] materialized_view_name
    WITH (  
      <distribution_option>
    )
    AS <select_statement>
[;]

<distribution_option> ::=
    {  
        DISTRIBUTION = HASH ( distribution_column_name )  
      | DISTRIBUTION = ROUND_ROBIN  
    }

<select_statement> ::=
    SELECT select_criteria
```  
  
## <a name="arguments"></a>Arguments

*schema_name*     
 Nom du schéma auquel appartient la vue.  
  
*materialized_view_name*   
Nom de la vue. Les noms des vues doivent se conformer aux règles applicables aux identificateurs. Vous n'êtes pas tenu de spécifier le nom du propriétaire de la vue.  

*option de distribution*     
Seules les distributions HASH et ROUND_ROBIN sont prises en charge.

*select_statement*   
La liste SELECT dans la définition de l’affichage matérialisé doit respecter au moins un de ces deux critères :
- La liste SELECT contient une fonction d’agrégation.
- GROUP BY est utilisé dans la définition de l’affichage matérialisé et toutes les colonnes dans GROUP BY sont incluses dans la liste SELECT.  

Les fonctions d’agrégation sont requises dans la liste SELECT de la définition de l’affichage matérialisé.  Les agrégations prises en charge incluent MAX, MIN, AVG, COUNT, COUNT_BIG, SUM, VAR, STDEV.

Lorsque les agrégats MIN/MAX sont utilisés dans la liste SELECT de la définition de l’affichage matérialisé, les conditions suivantes s’appliquent :
 
- FOR_APPEND est requis.  Par exemple :
  ```sql 
  CREATE MATERIALIZED VIEW mv_test2  
  WITH (distribution = hash(i_category_id), FOR_APPEND)  
  AS
  SELECT MAX(i.i_rec_start_date) as max_i_rec_start_date, MIN(i.i_rec_end_date) as min_i_rec_end_date, i.i_item_sk, i.i_item_id, i.i_category_id
  FROM syntheticworkload.item i  
  GROUP BY i.i_item_sk, i.i_item_id, i.i_category_id
  ```

- L’affichage matérialisé sera désactivé lorsque UPDATE ou DELETE se produit dans les tables de base référencées.  Cette restriction ne s’applique pas aux INSERT.  Pour réactiver l’affichage matérialisé, exécutez ALTER MATERIALIZED INDEX avec REBUILD.
  
## <a name="remarks"></a>Notes

Un affichage matérialisé dans l’entrepôt de données Azure est très similaire à une vue indexée dans SQL Server.  Il partage presque les mêmes restrictions que la vue indexée (consultez [Créer des vues indexées](/sql/relational-databases/views/create-indexed-views) pour plus d’informations), à ceci près qu’un affichage matérialisé prend en charge des fonctions d’agrégation.   Voici certaines remarques supplémentaires concernant l’affichage matérialisé.  
 
Seul CLUSTERED COLUMNSTORE INDEX est pris en charge par l’affichage matérialisé. 
 
Un affichage matérialisé peut être déposé par le biais de DROP VIEW.  Vous pouvez utiliser ALTER MATERIALIZED VIEW pour désactiver ou régénérer un affichage matérialisé.   
 
Les affichages matérialisés peuvent être créés sur les tables partitionnées.  Les opérations SPLIT/MERGE sont prises en charge sur les tables référencées dans les affichages matérialisés.  SWITCH n’est pas pris en charge sur les tables référencées dans les affichages matérialisés. Dans ce cas, l’utilisateur verra l’erreur,  `Msg 106104, Level 16, State 1, Line 9`
 
ALTER TABLE SWITCH n’est pas pris en charge sur les tables référencées dans les affichages matérialisés. Désactiver ou déposer les affichages matérialisés avant d’utiliser ALTER TABLE SWITCH. Dans les scénarios suivants, la création de l’affichage matérialisé nécessite l’ajout de nouvelles colonnes à l’affichage matérialisé :

|Scénario|Nouvelles colonnes à ajouter à l’affichage matérialisé|Commentaire|  
|-----------------|---------------|-----------------|
|COUNT_BIG() est manquant dans la liste SELECT d’une définition de l’affichage matérialisé| COUNT_BIG (*) |Ajouté automatiquement par la création de l’affichage matérialisé.  Aucune action de l'utilisateur n'est requise.|
|SUM(a) est spécifié par les utilisateurs dans la liste SELECT d’une définition de l’affichage matérialisé ET « a » est une expression Nullable |COUNT_BIG (a) |Les utilisateurs ont besoin d’ajouter l’expression « a » manuellement dans la définition de l’affichage matérialisé.|
|AVG(a) est spécifié par les utilisateurs dans la liste SELECT d’une définition de l’affichage matérialisé où « a » est une expression.|SUM(a), COUNT_BIG(a)|Ajouté automatiquement par la création de l’affichage matérialisé.  Aucune action de l'utilisateur n'est requise.|
|STDEV(a) est spécifié par les utilisateurs dans la liste SELECT d’une définition de l’affichage matérialisé où « a » est une expression.|SUM(a), COUNT_BIG(a), SUM(square(a))|Ajouté automatiquement par la création de l’affichage matérialisé.  Aucune action de l'utilisateur n'est requise. |
| | | |

Après la création, des affichages matérialisés sont visibles dans SQL Server Management Studio sous le dossier des affichages de l’instance Azure SQL Data Warehouse.

Les utilisateurs peuvent exécuter [SP_SPACEUSED](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql?view=azure-sqldw-latest) et [DBCC PDW_SHOWSPACEUSED](/sql/t-sql/database-console-commands/dbcc-pdw-showspaceused-transact-sql?view=azure-sqldw-latest) pour déterminer l’espace occupé par un affichage matérialisé.  

Le plan EXPLAIN et le Plan d’exécution graphique estimé dans SQL Server Management Studio peuvent indiquer si un affichage matérialisé est pris en compte par l’optimiseur de requête pour l’exécution des requêtes. et le Plan d’exécution graphique estimé dans SQL Server Management Studio peuvent indiquer si un affichage matérialisé est pris en compte par l’optimiseur de requête pour l’exécution des requêtes.

Pour déterminer si une instruction SQL peut bénéficier d’un nouvel affichage matérialisé, exécutez la commande `EXPLAIN` avec `WITH_RECOMMENDATIONS`.  Pour plus d’informations, consultez [EXPLAIN (Transact-SQL)](/sql/t-sql/queries/explain-transact-sql?view=azure-sqldw-latest).

## <a name="permissions"></a>Autorisations

Nécessite l'autorisation CREATE VIEW dans la base de données et l'autorisation ALTER sur le schéma dans lequel la vue est créée. 
  
## <a name="see-also"></a>Voir aussi

[ALTER MATERIALIZED VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-materialized-view-transact-sql?view=azure-sqldw-latest)   
[EXPLAIN &#40;Transact-SQL&#41;](/sql/t-sql/queries/explain-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_column_distribution_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-column-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_distribution_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_mappings &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-mappings-transact-sql?view=azure-sqldw-latest)   
[DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-pdw-showmaterializedviewoverhead-transact-sql?view=azure-sqldw-latest)   
[Affichages catalogue SQL Data Warehouse et Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
[Affichages système pris en charge dans Azure SQL Data Warehouse](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-system-views)   
[Instructions SQL prises en charge dans Azure SQL Data Warehouse](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-statements)

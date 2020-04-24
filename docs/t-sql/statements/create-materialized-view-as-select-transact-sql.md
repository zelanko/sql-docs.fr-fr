---
title: CREATE MATERIALIZED VIEW AS SELECT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2020
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
ms.openlocfilehash: 73fcf068c55b28448d87245b380281b461ef36b0
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81633609"
---
# <a name="create-materialized-view-as-select-transact-sql"></a>CREATE MATERIALIZED VIEW AS SELECT (Transact-SQL)  

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Cet article explique l’instruction SQL CREATE MATERIALIZED VIEW AS SELECT T dans Azure SQL Data Warehouse pour développer des solutions. L’article fournit également des exemples de code.

Une vue matérialisée conserve les données renvoyées par la requête de définition de vue et est automatiquement mise à jour à mesure que les données changent dans les tables sous-jacentes.   Elle améliore les performances des requêtes complexes (généralement des requêtes contenant des jointures et agrégations) tout en offrant des opérations de maintenance simples.   Avec sa capacité d’automatching du plan d’exécution, un affichage matérialisé ne devra pas être référencés dans la requête pour que l’optimiseur prenne en compte l’affichage pour substitution.  Cette fonctionnalité permet aux ingénieurs des données d’implémenter des vues matérialisées comme un mécanisme pour améliorer les temps de réponse des requêtes, sans devoir modifier les requêtes.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql
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
- GROUP BY est utilisé dans la définition de l’affichage matérialisé et toutes les colonnes dans GROUP BY sont incluses dans la liste SELECT.  Il est possible d’utiliser jusqu’à 32 colonnes dans la clause GROUP BY.

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

- L’affichage matérialisé sera désactivé lorsque UPDATE ou DELETE se produit dans les tables de base référencées.  Cette restriction ne s’applique pas aux instructions INSERT.  Pour réactiver l’affichage matérialisé, exécutez ALTER MATERIALIZED VIEW avec REBUILD.
  
## <a name="remarks"></a>Notes

Une vue matérialisée dans l’entrepôt de données Azure est similaire à une vue indexée dans SQL Server.  Il partage presque les mêmes restrictions que la vue indexée (consultez [Créer des vues indexées](/sql/relational-databases/views/create-indexed-views) pour plus d’informations), à ceci près qu’un affichage matérialisé prend en charge des fonctions d’agrégation.   

Seul CLUSTERED COLUMNSTORE INDEX est pris en charge par l’affichage matérialisé. 

Une vue matérialisée ne peut pas référencer d’autres vues.  

Une vue matérialisée ne peut pas être créée sur une table avec un masquage dynamique des données, même si la colonne avec masquage dynamique des données ne fait pas partie de la vue matérialisée.  Si une colonne de table fait partie d’une vue matérialisée active ou d’une vue matérialisée désactivée, le masquage dynamique des données ne peut pas être ajouté à cette colonne.  

Vous ne pouvez pas créer une vue matérialisée sur une table pour laquelle la sécurité au niveau des lignes est activée.

Les affichages matérialisés peuvent être créés sur les tables partitionnées.  Les opérations SPLIT/MERGE sur les partitions sont prises en charge sur les tables de base des vues matérialisées ; l’opération SWITCH sur des partitions n’est pas prise en charge.  
 
ALTER TABLE SWITCH n’est pas pris en charge sur les tables référencées dans les affichages matérialisés. Désactiver ou déposer les affichages matérialisés avant d’utiliser ALTER TABLE SWITCH. Dans les scénarios suivants, la création de l’affichage matérialisé nécessite l’ajout de nouvelles colonnes à l’affichage matérialisé :

|Scénario|Nouvelles colonnes à ajouter à l’affichage matérialisé|Commentaire|  
|-----------------|---------------|-----------------|
|COUNT_BIG() est manquant dans la liste SELECT d’une définition de vue matérialisée| COUNT_BIG (*) |Ajouté automatiquement par la création de l’affichage matérialisé.  Aucune action de l'utilisateur n'est requise.|
|SUM(a) est spécifié par les utilisateurs dans la liste SELECT d’une définition d’affichage matérialisé ET « a » est une expression nullable |COUNT_BIG (a) |Les utilisateurs doivent ajouter l’expression « a » manuellement dans la définition de l’affichage matérialisé.|
|AVG(a) est spécifié par les utilisateurs dans la liste SELECT d’une définition d’affichage matérialisé où « a » est une expression.|SUM(a), COUNT_BIG(a)|Ajouté automatiquement par la création de l’affichage matérialisé.  Aucune action de l'utilisateur n'est requise.|
|STDEV(a) est spécifié par les utilisateurs dans la liste SELECT d’une définition d’affichage matérialisé où « a » est une expression.|SUM(a), COUNT_BIG(a), SUM(square(a))|Ajouté automatiquement par la création de l’affichage matérialisé.  Aucune action de l'utilisateur n'est requise. |
| | | |

Après la création, des affichages matérialisés sont visibles dans SQL Server Management Studio sous le dossier des affichages de l’instance Azure SQL Data Warehouse.

Les utilisateurs peuvent exécuter [SP_SPACEUSED](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql?view=azure-sqldw-latest) et [DBCC PDW_SHOWSPACEUSED](/sql/t-sql/database-console-commands/dbcc-pdw-showspaceused-transact-sql?view=azure-sqldw-latest) pour déterminer l’espace consommé par une vue matérialisée.  

Un affichage matérialisé peut être déposé par le biais de DROP VIEW.  Vous pouvez utiliser ALTER MATERIALIZED VIEW pour désactiver ou régénérer un affichage matérialisé.   

Le plan EXPLAIN et le Plan d’exécution graphique estimé dans SQL Server Management Studio peuvent indiquer si un affichage matérialisé est pris en compte par l’optimiseur de requête pour l’exécution des requêtes. et le Plan d’exécution graphique estimé dans SQL Server Management Studio peuvent indiquer si un affichage matérialisé est pris en compte par l’optimiseur de requête pour l’exécution des requêtes.

Pour déterminer si une instruction SQL peut bénéficier d’un nouvel affichage matérialisé, exécutez la commande `EXPLAIN` avec `WITH_RECOMMENDATIONS`.  Pour plus d’informations, consultez [EXPLAIN (Transact-SQL)](/sql/t-sql/queries/explain-transact-sql?view=azure-sqldw-latest).

## <a name="permissions"></a>Autorisations

Nécessite l'autorisation CREATE VIEW dans la base de données et l'autorisation ALTER sur le schéma dans lequel la vue est créée. 
  
## <a name="see-also"></a>Voir aussi

[Réglage des performances avec une vue matérialisée](/azure/sql-data-warehouse/performance-tuning-materialized-views)   
[ALTER MATERIALIZED VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-materialized-view-transact-sql?view=azure-sqldw-latest)      
[DROP VIEW](/sql/t-sql/statements/drop-view-transact-sql?view=azure-sqldw-latest)  
[EXPLAIN &#40;Transact-SQL&#41;](/sql/t-sql/queries/explain-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_column_distribution_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-column-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_distribution_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_mappings &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-mappings-transact-sql?view=azure-sqldw-latest)   
[DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-pdw-showmaterializedviewoverhead-transact-sql?view=azure-sqldw-latest)   
[Affichages catalogue SQL Data Warehouse et Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
[Affichages système pris en charge dans Azure SQL Data Warehouse](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-system-views)   
[Instructions SQL prises en charge dans Azure SQL Data Warehouse](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-statements)

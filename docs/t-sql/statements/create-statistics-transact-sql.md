---
title: "CRÉER des statistiques (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STATISTICS
- STATISTICS_TSQL
- CREATE STATISTICS
- CREATE_STATISTICS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- query optimization statistics [SQL Server], creating
- indexed views [SQL Server], statistics
- FULLSCAN option
- CREATE STATISTICS statement
- filtered statistics [SQL Server]
- creating statistics [SQL Server]
- NORECOMPUTE clause
ms.assetid: b23e2f6b-076c-4e6d-9281-764bdb616ad2
caps.latest.revision: 105
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2e09604deac2b823243515c10398dc27c75941bd
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-statistics-transact-sql"></a>CREATE STATISTICS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Crée des statistiques d’optimisation de requête sur une ou plusieurs colonnes d’une table, une vue indexée ou une table externe. Pour la plupart des requêtes, l'optimiseur de requête génère déjà les statistiques utiles à un plan de requête de haute qualité ; dans certains cas, vous devez créer des statistiques supplémentaires avec CREATE STATISTICS ou modifier la conception des requêtes pour améliorer les performances des requêtes.  
  
 Pour plus d’informations, consultez [statistiques](../../relational-databases/statistics/statistics.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
-- Create statistics on an external table  
CREATE STATISTICS statistics_name   
ON { table_or_indexed_view_name } ( column [ ,...n ] )   
    [ WITH FULLSCAN ] ;  
  
-- Create statistics on a regular table or indexed view  
CREATE STATISTICS statistics_name   
ON { table_or_indexed_view_name } ( column [ ,...n ] )   
    [ WHERE <filter_predicate> ]  
    [ WITH   
        [ [ FULLSCAN   
            [ [ , ] PERSIST_SAMPLE_PERCENT = { ON | OFF } ]    
          | SAMPLE number { PERCENT | ROWS }   
            [ [ , ] PERSIST_SAMPLE_PERCENT = { ON | OFF } ]    
          | STATS_STREAM = stats_stream ] ]   
        [ [ , ] NORECOMPUTE ]   
        [ [ , ] INCREMENTAL = { ON | OFF } ]  
    ] ;  
  
<filter_predicate> ::=   
    <conjunct> [AND <conjunct>]  
  
<conjunct> ::=  
    <disjunct> | <comparison>  
  
<disjunct> ::=  
        column_name IN (constant ,…)  
  
<comparison> ::=  
        column_name <comparison_op> constant  
  
<comparison_op> ::=  
    IS | IS NOT | = | <> | != | > | >= | !> | < | <= | !<  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
CREATE STATISTICS statistics_name   
    ON [ database_name . [schema_name ] . | schema_name. ] table_name   
    ( column_name  [ ,...n ] )   
    [ WHERE <filter_predicate> ]  
    [ WITH {  
           FULLSCAN   
           | SAMPLE number PERCENT   
      }  
    ]  
[;]  
  
<filter_predicate> ::=   
    <conjunct> [AND <conjunct>]  
  
<conjunct> ::=  
    <disjunct> | <comparison>  
  
<disjunct> ::=  
        column_name IN (constant ,…)  
  
<comparison> ::=  
        column_name <comparison_op> constant  
  
<comparison_op> ::=  
    IS | IS NOT | = | <> | != | > | >= | !> | < | <= | !<  
```  
  
## <a name="arguments"></a>Arguments  
 *statistics_name*  
 Est le nom des statistiques à créer.  
  
 *table_or_indexed_view_name*  
 Est le nom de la table, une vue indexée ou une table externe sur lequel créer les statistiques. Pour créer des statistiques sur une autre base de données, spécifiez un nom de table qualifié.  
  
 *colonne [,... n]*  
 Une ou plusieurs colonnes à inclure dans les statistiques. Les colonnes doivent être dans l’ordre de priorité de gauche à droite. Seule la première colonne est utilisée pour la création de l’histogramme. Toutes les colonnes sont utilisées pour les statistiques de corrélation entre les colonnes appelées densités.  
  
 Vous pouvez indiquer comme base de calcul des statistiques toute colonne pouvant être spécifiée en tant que colonne de clé d'index, sauf pour les exceptions suivantes :  
  
-   **XML**, recherche en texte intégral, et des colonnes FILESTREAM ne peut pas être spécifiés.  
  
-   Les colonnes calculées ne peuvent être indiquées que si les paramètres de base de données ARITHABORT et QUOTED_IDENTIFIER ont la valeur ON.  
  
-   Toute colonne de type CLR définie par l'utilisateur peut être spécifiée si son type prend en charge l'ordre de tri binaire. Les colonnes calculées définies en tant qu'appels à des méthodes d'une colonne de type défini par l'utilisateur peuvent être précisées si les méthodes en question sont marquées comme étant déterministes.  
  
 OÙ \<filter_predicate > Spécifie une expression pour sélectionner un sous-ensemble de lignes à inclure lors de la création de l’objet de statistiques. Les statistiques créées avec un prédicat de filtre sont appelées des statistiques filtrées. Le prédicat de filtre utilise la logique de comparaison simple et ne peut pas faire référence à une colonne calculée, une colonne UDT, une colonne de type de données spatiales, ou un **hierarchyID** colonne de type de données. Les comparaisons à l'aide de littéraux NULL ne sont pas autorisées avec les opérateurs de comparaison. Utilisez les opérateurs IS NULL et IS NOT NULL à la place.  
  
 Voici quelques exemples de prédicats de filtre pour la table Production.BillOfMaterials :  
  
 `WHERE StartDate > '20000101' AND EndDate <= '20000630'`  
  
 `WHERE ComponentID IN (533, 324, 753)`  
  
 `WHERE StartDate IN ('20000404', '20000905') AND EndDate IS NOT NULL`  
  
 Pour plus d’informations sur les prédicats de filtre, consultez [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md).  
  
 FULLSCAN  
 Calcule les statistiques en analysant toutes les lignes. FULLSCAN et SAMPLE 100 PERCENT ont les mêmes résultats. Cette option ne peut pas être utilisée avec l'option SAMPLE.  
  
 Lorsque l’argument est omis, SQL Server utilise pour créer les statistiques de l’échantillonnage et détermine la taille d’échantillon est nécessaire pour créer un plan de requête de haute qualité  
  
 EXEMPLE *nombre* {% | LIGNES}  
 Spécifie le pourcentage ou nombre de lignes approximatif dans la table ou vue indexée devant être utilisé par l'optimiseur de requête lors de la création des statistiques. Pour PERCENT, *nombre* peut être comprise entre 0 et 100 et des lignes, *nombre* peut être comprise entre 0 et le nombre total de lignes. Le pourcentage ou nombre de lignes réel échantillonné par l'optimiseur de requête peut ne pas correspondre au pourcentage ou nombre spécifié. Par exemple, l'optimiseur de requête analyse toutes les lignes d'une page de données.  
  
 SAMPLE est utile pour les cas spéciaux dans lesquels le plan de requête, basé sur l'échantillonnage par défaut, n'est pas optimal. Dans la plupart des situations, il n'est pas nécessaire de spécifier SAMPLE, car l'optimiseur de requête utilise déjà l'échantillonnage et détermine la taille d'échantillon statistiquement significative par défaut, comme requis pour créer des plans de requête de haute qualité.  
  
 SAMPLE ne peut pas être utilisé avec l'option FULLSCAN. Lorsque ni SAMPLE ni FULLSCAN n'est spécifié, l'optimiseur de requête utilise les données échantillonnées et calcule la taille d'échantillon par défaut.  
  
 Il est déconseillé de spécifier 0 PERCENT ou 0 ROWS. Lorsque 0 PERCENT ou ROWS est spécifié, l'objet de statistiques est créé mais ne contient pas de données de statistiques.  
 
 PERSIST_SAMPLE_PERCENT = {ON | {OFF}  
 Lorsque **ON**, les statistiques conservera le pourcentage d’échantillonnage de création pour les mises à jour qui ne spécifient pas explicitement un pourcentage d’échantillonnage. Lorsque **OFF**, pourcentage d’échantillonnage des statistiques sera réinitialisée à échantillonnage par défaut dans les mises à jour qui ne spécifient pas explicitement un pourcentage d’échantillonnage. La valeur par défaut est **OFF**. 
 
 **S’applique aux**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 CU4.  
  
 STATS_STREAM  **=**  *stats_stream*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 NORECOMPUTE  
 Désactiver les statistiques automatiques mettre à jour l’option AUTO_UPDATE_STATISTICS, pour *statistics_name*. Si cette option est spécifiée, l’optimiseur de requête s’achève toutes les mises à jour les statistiques en cours pour *statistics_name* et désactiver les mises à jour ultérieures.  
  
 Pour réactiver les mises à jour des statistiques, supprimez les statistiques avec [DROP STATISTICS](../../t-sql/statements/drop-statistics-transact-sql.md) , puis exécutez CREATE STATISTICS sans l’option NORECOMPUTE.  
  
> [!WARNING]  
>  L'utilisation de cette option peut produire des plans de requête non optimaux. Nous recommandons d'utiliser cette option avec parcimonie et uniquement par un administrateur système qualifié.  
  
 Pour plus d’informations sur l’option AUTO_UPDATE_STATISTICS, consultez [Options ALTER DATABASE SET &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md). Pour plus d’informations sur la désactivation et réactivation des mises à jour des statistiques, consultez [statistiques](../../relational-databases/statistics/statistics.md).  
  
 INCREMENTAL = { ON | OFF }  
 Lorsque **ON**, les statistiques sont créées par partition. Lorsque **OFF**, les statistiques sont combinées pour toutes les partitions. La valeur par défaut est **OFF**.  
  
 Si les statistiques par partition ne sont pas prises en charge, une erreur est générée. Les statistiques incrémentielles ne sont pas prises en charge pour les types de statistiques suivants :  
  
-   statistiques créées avec des index qui ne sont pas alignés sur les partitions avec la table de base ;  
  
-   statistiques créées sur les bases de données secondaires lisibles Always On ;  
  
-   statistiques créées sur les bases de données en lecture seule ;  
  
-   statistiques créées sur les index filtrés ;  
  
-   statistiques créées sur les vues ;  
  
-   statistiques créées sur les tables internes ;  
  
-   Statistiques créées avec les index spatiaux ou les index XML.  
  
**S'applique à**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="permissions"></a>Permissions  
 Requiert l’une de ces autorisations :  
  
-   ALTER TABLE  
  
-   L’utilisateur est propriétaire de la table  
  
-   L’appartenance à la **db_ddladmin** rôle de base de données fixe  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tempdb permet de trier les lignes échantillonnées avant de générer des statistiques.  
  
### <a name="statistics-for-external-tables"></a>Statistiques pour les tables externes  
 Lors de la création des statistiques de table externe, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] importe la table externe dans un fichier temporaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de table, puis crée les statistiques. Pour les statistiques d’exemples, seules les lignes échantillonnées sont importés. Si vous avez une grande table externe, il sera beaucoup plus rapide d’utiliser l’échantillonnage par défaut au lieu de l’option d’analyse complète.  
  
### <a name="statistics-with-a-filtered-condition"></a>Statistiques avec une condition filtrée  
 Les statistiques filtrées peuvent améliorer les performances des requêtes qui effectuent des sélections dans des sous-ensembles bien définis de données. Elles utilisent un prédicat de filtre dans la clause WHERE pour sélectionner le sous-ensemble de données qui est inclus dans les statistiques.  
  
### <a name="when-to-use-create-statistics"></a>Quand utiliser CREATE STATISTICS  
 Pour plus d’informations sur l’utilisation de CREATE STATISTICS, consultez [statistiques](../../relational-databases/statistics/statistics.md).  
  
### <a name="referencing-dependencies-for-filtered-statistics"></a>Dépendances des références pour les statistiques filtrées  
 Le [sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md) affichage catalogue effectue le suivi de chaque colonne dans le prédicat de statistiques filtrées en tant que dépendance de référence. Réfléchissez aux opérations que vous effectuez sur les colonnes de table avant de créer des statistiques filtrées car vous ne pouvez pas supprimer, renommer, ni modifier la définition d'une colonne de table qui est définie dans un prédicat de statistiques filtrées.  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
*  Mise à jour des statistiques n’est pas pris en charge sur les tables externes. Pour mettre à jour des statistiques sur une table externe, supprimez et recréez les statistiques.  
*  Vous pouvez répertorier jusqu'à 64 colonnes par objet de statistiques.
  
## <a name="examples"></a>Exemples  

### <a name="examples-use-the-adventureworks-database"></a>Exemples utilisent la base de données AdventureWorks.  

### <a name="a-using-create-statistics-with-sample-number-percent"></a>A. Utilisation de CREATE STATISTICS avec SAMPLE number PERCENT  
 L'exemple suivant crée les statistiques `ContactMail1`, à l'aide d'un exemple aléatoire de 5 pour cent des colonnes `BusinessEntityID` et `EmailPromotion` de la table `Contact` de la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```t-sql  
CREATE STATISTICS ContactMail1  
    ON Person.Person (BusinessEntityID, EmailPromotion)  
    WITH SAMPLE 5 PERCENT;  
```  
  
### <a name="b-using-create-statistics-with-fullscan-and-norecompute"></a>B. Utilisation de CREATE STATISTICS avec FULLSCAN et NORECOMPUTE  
 L'exemple suivant crée les statistiques `ContactMail2` pour toutes les lignes des colonnes `BusinessEntityID` et `EmailPromotion` de la table `Contact` et désactive le recalcul automatique des statistiques.  
  
```t-sql  
CREATE STATISTICS NamePurchase  
    ON AdventureWorks2012.Person.Person (BusinessEntityID, EmailPromotion)  
    WITH FULLSCAN, NORECOMPUTE;  
```  
  
### <a name="c-using-create-statistics-to-create-filtered-statistics"></a>C. Utilisation de CREATE STATISTICS pour créer des statistiques filtrées  
 L'exemple suivant crée les statistiques filtrées `ContactPromotion1`. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] échantillonne 50 pour cent des données, puis sélectionne toutes les lignes pour lesquelles `EmailPromotion` est égal à 2.  
  
```t-sql  
CREATE STATISTICS ContactPromotion1  
    ON Person.Person (BusinessEntityID, LastName, EmailPromotion)  
WHERE EmailPromotion = 2  
WITH SAMPLE 50 PERCENT;  
GO  
```  
  
### <a name="d-create-statistics-on-an-external-table"></a>D. Créer des statistiques sur une table externe  
 La seule décision que vous devez faire lorsque vous créez des statistiques sur une table externe, en plus de fournir la liste des colonnes, consiste à créer les statistiques en échantillonnant les lignes ou en analysant toutes les lignes.  
  
 Étant donné que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] importe des données à partir de la table externe dans une table temporaire pour créer des statistiques, l’option d’analyse complète prendra beaucoup plus de temps. Pour une table volumineuse, la méthode d’échantillonnage par défaut est généralement suffisante.  
  
```t-sql  
--Create statistics on an external table and use default sampling.  
CREATE STATISTICS CustomerStats1 ON DimCustomer (CustomerKey, EmailAddress);  
  
--Create statistics on an external table and scan all the rows  
CREATE STATISTICS CustomerStats1 ON DimCustomer (CustomerKey, EmailAddress) WITH FULLSCAN;  
```  

### <a name="e-using-create-statistics-with-fullscan-and-persistsamplepercent"></a>E. Utilisation de CREATE STATISTICS avec FULLSCAN et PERSIST_SAMPLE_PERCENT  
 L’exemple suivant crée la `ContactMail2` des statistiques pour toutes les lignes de la `BusinessEntityID` et `EmailPromotion` les colonnes de la `Contact` de table et définit le pourcentage d’échantillonnage de 100 pour cent pour toutes les mises à jour ultérieures qui n'effectuent pas explicitement spécifient un pourcentage d’échantillonnage.  
  
```t-sql  
CREATE STATISTICS NamePurchase  
    ON AdventureWorks2012.Person.Person (BusinessEntityID, EmailPromotion)  
    WITH FULLSCAN, PERSIST_SAMPLE_PERCENT = ON;  
```  
  
### <a name="examples-using-adventureworksdw-database"></a>Exemples d’utilisation de base de données AdventureWorksDW. 
  
### <a name="f-create-statistics-on-two-columns"></a>F. Créer des statistiques sur les deux colonnes  
 L’exemple suivant crée la `CustomerStats1` des statistiques, en fonction de la `CustomerKey` et `EmailAddress` les colonnes de la `DimCustomer` table. Les statistiques sont créées d’après un échantillon statistiquement significatif des lignes dans la `Customer` table.  
  
```t-sql  
CREATE STATISTICS CustomerStats1 ON DimCustomer (CustomerKey, EmailAddress);  
```  
  
### <a name="g-create-statistics-by-using-a-full-scan"></a>G. Créer des statistiques à l’aide d’une analyse complète  
 L’exemple suivant crée la `CustomerStatsFullScan` des statistiques, en fonction de l’analyse de toutes les lignes dans la `DimCustomer` table.  
  
```t-sql  
CREATE STATISTICS CustomerStatsFullScan 
ON DimCustomer (CustomerKey, EmailAddress) WITH FULLSCAN;  
```  
  
### <a name="h-create-statistics-by-specifying-the-sample-percentage"></a>H. Créer des statistiques en spécifiant le pourcentage d’échantillonnage  
 L’exemple suivant crée la `CustomerStatsSampleScan` des statistiques, en fonction de l’analyse de 50 pour cent des lignes dans la `DimCustomer` table.  
  
```t-sql  
CREATE STATISTICS CustomerStatsSampleScan 
ON DimCustomer (CustomerKey, EmailAddress) WITH SAMPLE 50 PERCENT;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Statistiques](../../relational-databases/statistics/statistics.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [sp_updatestats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-updatestats-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)   
 [Sys.stats_columns &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-stats-columns-transact-sql.md)  
  
  



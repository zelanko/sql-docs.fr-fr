---
title: FROM (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- JOIN
- FROM_TSQL
- FROM
- JOIN_TSQL
- CROSS_TSQL
- CROSS_APPLY_TSQL
- APPLY_TSQL
- CROSS_JOIN_TSQL
dev_langs: TSQL
helpviewer_keywords:
- OUTER APPLY operator
- hints [SQL Server], FROM clause
- SELECT statement [SQL Server], FROM clause
- ISO syntax
- DELETE statement [SQL Server], FROM clause
- CROSS APPLY operator
- FROM clause
- APPLY operator
- joins [SQL Server], FROM clause
- UPDATE statement [SQL Server], FROM clause
- derived tables
ms.assetid: 36b19e68-94f6-4539-aeb1-79f5312e4263
caps.latest.revision: "97"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: c1abc4a060dd275ba2f8500e88d634a5ba9244ee
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="from-transact-sql"></a>FROM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Spécifie les tables, les vues, les tables dérivées et les tables jointes utilisées dans les instructions DELETE, SELECT et UPDATE dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Dans l'instruction SELECT, la clause FROM est obligatoire sauf lorsque la liste de sélection ne contient que des constantes, des variables et des expressions arithmétiques (aucun nom de colonne).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
[ FROM { <table_source> } [ ,...n ] ]   
<table_source> ::=   
{  
    table_or_view_name [ [ AS ] table_alias ]   
        [ <tablesample_clause> ]   
        [ WITH ( < table_hint > [ [ , ]...n ] ) ]   
    | rowset_function [ [ AS ] table_alias ]   
        [ ( bulk_column_alias [ ,...n ] ) ]   
    | user_defined_function [ [ AS ] table_alias ]  
    | OPENXML <openxml_clause>   
    | derived_table [ [ AS ] table_alias ] [ ( column_alias [ ,...n ] ) ]   
    | <joined_table>   
    | <pivoted_table>   
    | <unpivoted_table>  
    | @variable [ [ AS ] table_alias ]  
    | @variable.function_call ( expression [ ,...n ] )   
        [ [ AS ] table_alias ] [ (column_alias [ ,...n ] ) ]  
    | FOR SYSTEM_TIME <system_time>   
}  
<tablesample_clause> ::=  
    TABLESAMPLE [SYSTEM] ( sample_number [ PERCENT | ROWS ] )   
        [ REPEATABLE ( repeat_seed ) ]   
  
<joined_table> ::=   
{  
    <table_source> <join_type> <table_source> ON <search_condition>   
    | <table_source> CROSS JOIN <table_source>   
    | left_table_source { CROSS | OUTER } APPLY right_table_source   
    | [ ( ] <joined_table> [ ) ]   
}  
<join_type> ::=   
    [ { INNER | { { LEFT | RIGHT | FULL } [ OUTER ] } } [ <join_hint> ] ]  
    JOIN  
  
<pivoted_table> ::=  
    table_source PIVOT <pivot_clause> [ [ AS ] table_alias ]  
  
<pivot_clause> ::=  
        ( aggregate_function ( value_column [ [ , ]...n ])   
        FOR pivot_column   
        IN ( <column_list> )   
    )   
  
<unpivoted_table> ::=  
    table_source UNPIVOT <unpivot_clause> [ [ AS ] table_alias ]  
  
<unpivot_clause> ::=  
    ( value_column FOR pivot_column IN ( <column_list> ) )   
  
<column_list> ::=  
    column_name [ ,...n ]   
  
<system_time> ::=  
{  
       AS OF <date_time>  
    |  FROM <start_date_time> TO <end_date_time>  
    |  BETWEEN <start_date_time> AND <end_date_time>  
    |  CONTAINED IN (<start_date_time> , <end_date_time>)   
    |  ALL  
}  
  
    <date_time>::=  
        <date_time_literal> | @date_time_variable  
  
    <start_date_time>::=  
        <date_time_literal> | @date_time_variable  
  
    <end_date_time>::=  
        <date_time_literal> | @date_time_variable  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
FROM { <table_source> [ ,...n ] }  
  
<table_source> ::=   
{  
    [ database_name . [ schema_name ] . | schema_name . ] table_or_view_name [ AS ] table_or_view_alias  
    | derived_table [ AS ] table_alias [ ( column_alias [ ,...n ] ) ]  
    | <joined_table>  
}  
  
<joined_table> ::=   
{  
    <table_source> <join_type> <table_source> ON search_condition   
    | <table_source> CROSS JOIN <table_source> 
    | left_table_source { CROSS | OUTER } APPLY right_table_source   
    | [ ( ] <joined_table> [ ) ]   
}  
  
<join_type> ::=   
    [ INNER ] [ <join hint> ] JOIN  
    | LEFT  [ OUTER ] JOIN  
    | RIGHT [ OUTER ] JOIN  
    | FULL  [ OUTER ] JOIN  
  
<join_hint> ::=   
    REDUCE  
    | REPLICATE  
    | REDISTRIBUTE  
```  
  
## <a name="arguments"></a>Arguments  
\<table_source>  
 Spécifie une table, une vue, une variable de table ou une source de table dérivée, avec ou sans alias, à utiliser dans l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)]. Vous pouvez utiliser jusqu'à 256 sources de table dans une instruction, bien que cette limite varie en fonction de la mémoire disponible et de la complexité des autres expressions constituant la requête. Les requêtes individuelles peuvent ne pas prendre en charge 256 sources de table.  
  
> [!NOTE]  
>  Les performances des requêtes risquent de baisser si le nombre des tables référencées dans une requête est élevé. Les durées de compilation et d'optimisation sont également affectées par d'autres facteurs. Celles-ci incluent la présence d’index et vues indexées sur chaque \<table_source > et la taille de la \<select_list > dans l’instruction SELECT.  
  
 L'ordre des sources de table après le mot clé FROM n'a aucune incidence sur le jeu de résultats retourné. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne des erreurs lorsque des noms dupliqués apparaissent dans la clause FROM.  
  
 *table_or_view_name*  
 Nom d'une table ou d'une vue.  
  
 Si la table ou la vue existe dans une autre base de données sur la même instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], utilisez un nom complet sous la forme *base de données*. *schéma*. *nom_objet*.  
  
 Si la table ou la vue existe en dehors de l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]l, utilisez un nom en quatre parties sous la forme *linked_server*. *catalogue*. *schéma*. *objet*. Pour plus d’informations, consultez [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md). Un nom en quatre parties qui est construit à l’aide de la [OPENDATASOURCE](../../t-sql/functions/opendatasource-transact-sql.md) fonctionne comme la partie serveur du nom de peut également être utilisée pour spécifier la source de la table distante. Lorsque OPENDATASOURCE est spécifiée, *nom_base_de_données* et *schema_name* ne peuvent pas s’appliquer à toutes les sources de données et est soumise aux capacités du fournisseur OLE DB qui accède à l’objet distant.  
  
 [EN] *alias_de_table*  
 Est un alias de *table_source* qui peut être utilisé soit pour des raisons pratiques, soit pour distinguer une table ou une vue dans une jointure réflexive ou une sous-requête. Un alias correspond souvent au raccourci du nom de table utilisé pour faire référence aux colonnes spécifiques des tables dans une jointure. Si le même nom de colonne existe dans plusieurs tables de la jointure, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] exige que le nom de la colonne soit qualifié par un nom de table, un nom de vue ou un alias. Le nom de table ne peut pas être utilisé si un alias est défini.  
  
 Lorsqu’une table dérivée, ensemble de lignes ou une fonction table ou une clause d’opérateur (par exemple, PIVOT ou UNPIVOT) est utilisée, le texte requis *alias_de_la_table* à la fin de la clause est le nom de la table associée pour toutes les colonnes, y compris les colonnes de regroupement retournées.  
  
 AVEC (\<indicateur de table >)  
 Spécifie que l'optimiseur de requête utilise une stratégie d'optimisation ou de verrouillage avec cette table et pour cette instruction. Pour plus d’informations, consultez [Indicateurs de table &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-table.md).  
  
 *rowset_function*  

**S’applique aux**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  

  
 Spécifie l'une des fonctions d'ensemble de lignes, par exemple OPENROWSET, qui retourne un objet pouvant être utilisé à la place d'une référence de table. Pour plus d’informations sur une liste de fonctions d’ensemble de lignes, consultez [fonctions Rowset &#40; Transact-SQL &#41; ](../../t-sql/functions/rowset-functions-transact-sql.md).  
  
 L'utilisation des fonctions OPENROWSET et OPENQUERY pour spécifier un objet distant dépend des fonctionnalités du fournisseur OLE DB qui accède à l'objet.  
  
 *bulk_column_alias*  

**S’applique aux**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  

  
 Alias facultatif qui peut remplacer un nom de colonne dans le jeu de résultats. Les alias de colonne sont autorisés uniquement dans les instructions SELECT qui utilisent la fonction OPENROWSET avec l'option BULK. Lorsque vous utilisez *bulk_column_alias*, spécifiez un alias pour chaque colonne de table dans le même ordre que les colonnes dans le fichier.  
  
> [!NOTE]  
>  Cet alias remplace l'attribut NAME dans les éléments COLUMN d'un fichier XML, le cas échéant.  
  
 *user_defined_function*  
 Spécifie une fonction table.  
  
 OPENXML \<openxml_clause>  

**S’applique aux**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  

  
 Fournit une vue de l'ensemble de lignes d'un document XML. Pour plus d’informations, consultez [OPENXML &#40; Transact-SQL &#41; ](../../t-sql/functions/openxml-transact-sql.md).  
  
 *derived_table*  
 Sous-requête qui récupère les lignes de la base de données. *table_dérivée* est utilisé en tant qu’entrée à la requête externe.  
  
 *dérivés* *_table* pouvez utiliser la [!INCLUDE[tsql](../../includes/tsql-md.md)] fonctionnalité de constructeur de valeur de table pour spécifier plusieurs lignes. Par exemple, `SELECT * FROM (VALUES (1, 2), (3, 4), (5, 6), (7, 8), (9, 10) ) AS MyTable(a, b);`. Pour plus d’informations, consultez [constructeur de valeurs de Table &#40; Transact-SQL &#41; ](../../t-sql/queries/table-value-constructor-transact-sql.md).  
  
 *column_alias*  
 Alias facultatif qui peut remplacer un nom de colonne dans le jeu de résultats de la table dérivée. Utilisez un alias de colonne pour chaque colonne de la liste de sélection et placez l'intégralité de la liste d'alias de colonnes entre parenthèses.  
  
 *table_or_view_name* FOR SYSTEM_TIME \<system_time>  

**S’applique aux**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  

  
 Spécifie qu’une version spécifique de données est retournée à partir de la table temporelle spécifiée et sa table d’historique avec version système lié  
  
\<tablesample_clause>  
 Spécifie qu'un exemple de données est retourné à partir de la table. L'exemple peut être approximatif. Cette clause peut être utilisée sur toute table primaire ou jointe dans une instruction SELECT, UPDATE ou DELETE. TABLESAMPLE ne peut pas être spécifié avec des vues.  
  
> [!NOTE]  
>  Lorsque vous utilisez TABLESAMPLE sur des bases de données mises à niveau vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le niveau de compatibilité de la base de données est défini à 110 ou plus, PIVOT n'est pas autorisé dans une requête d'expression de table commune récursive (CTE). Pour plus d’informations, consultez [Niveau de compatibilité ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
 SYSTEM  
 Méthode d'échantillonnage dépendante de l'implémentation et spécifiée par les normes ISO. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il s'agit de la seule méthode d'échantillonnage disponible et elle s'applique par défaut. SYSTEM applique une méthode d'échantillonnage basée sur des pages, dans laquelle un jeu de pages aléatoire est choisi pour l'exemple ; toutes les lignes de ces pages sont retournées comme exemple de sous-ensemble.  
  
 *sample_number*  
 Expression numérique constante exacte ou approximative qui représente le pourcentage ou le nombre de lignes. Lorsque spécifié avec PERCENT, *sample_number* est implicitement converti en un **float** valeur ; sinon, elle est convertie en **bigint**. PERCENT est la valeur par défaut.  
  
 PERCENT  
 Spécifie qu’un *sample_number* pour cent des lignes de la table doit être récupérés à partir de la table. Lorsque PERCENT est spécifié, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne une approximation du pourcentage spécifié. Lorsque PERCENT est spécifié la *sample_number* expression doit correspondre à une valeur comprise entre 0 et 100.  
  
 ROWS  
 Spécifie qu’environ *sample_number* de lignes sont récupérées. Lorsque ROWS est spécifié, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne une valeur approximative du nombre de lignes indiqué. Lorsque ROWS est spécifié, le *sample_number* expression doit correspondre à une valeur entière supérieure à zéro.  
  
 REPEATABLE  
 Indique que l'exemple sélectionné peut être retourné à nouveau. Lorsque spécifié avec le même *repeat_seed* valeur, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retournera le même sous-ensemble de lignes en tant que sans modifications ont été apportées aux lignes de la table. Lorsque spécifié par une autre *repeat_seed* valeur, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sera retour susceptible d’autres exemples de lignes de la table. Les actions suivantes effectuées sur la table sont considérées comme des modifications : insertion, mise à jour, suppression, reconstruction ou défragmentation d'index, restauration ou attachement de base de données.  
  
 *repeat_seed*  
 Expression d'un entier de type constante utilisée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour générer un nombre aléatoire. *repeat_seed* est **bigint**. Si *repeat_seed* n’est pas spécifié, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affecte une valeur aléatoire. Pour un spécifique *repeat_seed* valeur, le résultat de l’échantillonnage est toujours le même si aucune modification n’ont été appliquées à la table. Le *repeat_seed* expression doit correspondre à un entier supérieur à zéro.  
  
 \<joined_table>  
 Jeu de résultats correspondant au produit de deux ou plusieurs tables. Pour plusieurs jointures, utilisez des parenthèses afin de modifier l'ordre naturel des jointures.  
  
\<join_type>  
 Spécifie le type d'opération de jointure.  
  
 **INNER**  
 Spécifie que toutes les paires correspondantes de lignes sont retournées. Supprime les lignes n'ayant pas de correspondance dans les deux tables. Lorsqu'aucun type de jointure n'est spécifié, cet argument est la valeur par défaut.  
  
 FULL [ OUTER ]  
 Spécifie qu'une ligne de la table de gauche ou de droite qui ne respecte pas la condition de jointure est incluse dans le jeu de résultats et que les colonnes de sortie qui correspondent à l'autre table ont des valeurs NULL. Cela s'ajoute à toutes les lignes généralement retournées par INNER JOIN.  
  
 LEFT [ OUTER ]  
 Spécifie que toutes les lignes de la table de gauche qui ne respectent pas la condition de jointure sont incluses dans le jeu de résultats et que les colonnes de sortie de l'autre table ont des valeurs NULL en plus de toutes les lignes retournées par la jointure interne.  
  
 RIGHT [OUTER]  
 Spécifie que toutes les lignes de la table de droite qui ne respectent pas la condition de jointure sont incluses dans le jeu de résultats et que les colonnes de sortie qui correspondent à l'autre table ont des valeurs NULL en plus de toutes les lignes retournées par la jointure interne.  
  
\<join_hint>  
 Pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssSDS](../../includes/sssds-md.md)], qui spécifie le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requête optimiseur utilise un indicateur de jointure ou un algorithme d’exécution par jointure spécifiée dans la clause FROM de la requête. Pour plus d’informations, consultez [indicateurs de jointure &#40; Transact-SQL &#41; ](../../t-sql/queries/hints-transact-sql-join.md).  
  
 Pour [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], ces indicateurs de jointure s’appliquent aux jointures INNER sur deux colonnes incompatibles de distribution. Ils peuvent améliorer les performances en limitant la quantité de déplacement des données qui se produit pendant le traitement des requêtes. Indicateurs de la jointure autorisée pour [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] sont les suivantes :  
  
 RÉDUIRE  
 Réduit le nombre de lignes à déplacer sur le côté droit de la jointure de la table afin que les deux tables incompatible de distribution compatible. L’indicateur de réduction est également appelé un semi join (indicateur).  
  
 REPLICATE  
 Entraîne les valeurs dans la colonne de jointure de la table sur le côté gauche de la jointure à être répliquées sur tous les nœuds. La table de droite est jointe à la version dupliquée de ces colonnes.  
  
 REDISTRIBUER  
 Sources de données force deux doit être distribuée sur les colonnes spécifiées dans la clause JOIN. Pour une table distribuée, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] effectue un déplacement aléatoire. Pour une table répliquée, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] effectue un déplacement de découpage. Pour comprendre ces types déplacent, consultez la section « Requête planifier les opérations DMS » dans la rubrique « Présentation des Plans de requête » dans la [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]. Cet indicateur peut améliorer les performances lorsque le plan de requête utilise un déplacement de diffusion pour résoudre une jointure incompatible de distribution.  
  
 JOIN  
 Indique que l'opération de jointure spécifiée doit avoir lieu entre les sources de table ou les vues spécifiées.  
  
 ON \<search_condition>  
 Spécifie la condition sur laquelle se base la jointure. Celle-ci peut spécifier n'importe quel prédicat, bien que les colonnes et les opérateurs de comparaison soient souvent utilisés, par exemple :  
  
```sql
SELECT p.ProductID, v.BusinessEntityID  
FROM Production.Product AS p   
JOIN Purchasing.ProductVendor AS v  
ON (p.ProductID = v.ProductID);  
  
```  
  
 Lorsque la condition spécifie des colonnes, celles-ci ne doivent pas nécessairement avoir le même nom ou le même type de données. Toutefois, si les types de données sont différents, ils doivent être compatibles ou pouvoir être convertis implicitement par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si les types de données ne peuvent pas être convertis implicitement, la condition doit convertir explicitement le type de données à l'aide de la fonction CONVERT.  
  
 Il se peut que des prédicats n'impliquent qu'une seule des tables jointes dans la clause ON. Ces prédicats peuvent également figurer dans la clause WHERE de la requête. Bien que la position de ces prédicats soit sans importance dans le cas de jointures INNER, ils peuvent aboutir à un résultat différent dans le cas de jointures OUTER. En effet, les prédicats figurant dans la clause ON sont appliqués à la table avant de l'être à la jointure, tandis que la clause WHERE est sémantiquement appliquée au résultat de la jointure.  
  
 Pour plus d’informations sur les conditions de recherche et les prédicats, consultez [Condition de recherche &#40; Transact-SQL &#41; ](../../t-sql/queries/search-condition-transact-sql.md).  
  
 CROSS JOIN  
 Spécifie le produit croisé de deux tables. Retourne les mêmes lignes comme si aucune clause WHERE n'avait été spécifiée dans une ancienne jointure d'un style différent de SQL-92.  
  
 *left_table_source* {CROSS | APPLIQUER de OUTER} *right_table_source*  
 Spécifie que le *right_table_source* du appliquer l’opérateur est évalué par rapport à chaque ligne de la *left_table_source*. Cette fonctionnalité est utile lorsque le *right_table_source* contient une fonction table qui prend la valeur de colonne de la *left_table_source* comme l’un de ses arguments.  
  
 Soit CROSS, soit OUTER doit être spécifié avec APPLY. Lorsque CROSS est spécifié, aucune ligne n’est produites lors de la *right_table_source* est évaluée par rapport à une ligne spécifique de la *left_table_source* et retourne un jeu de résultats vide.  
  
 Lorsque OUTER est spécifié, une ligne est produite pour chaque ligne de la *left_table_source* même lorsque le *right_table_source* évalue par rapport à cette ligne et retourne un jeu de résultats vide.  
  
 Pour plus d'informations, consultez la section Notes.  
  
 *left_table_source*  
 Source de table, telle qu'elle est définie dans l'argument précédent. Pour plus d'informations, consultez la section Notes.  
  
 *right_table_source*  
 Source de table, telle qu'elle est définie dans l'argument précédent. Pour plus d'informations, consultez la section Notes.  
  
 *table_source* PIVOT \<pivot_clause>  
 Spécifie que le *table_source* est croisé dynamiquement sur la *pivot_column*. *table_source* est une table ou une expression de table. La sortie est une table qui contient toutes les colonnes de la *table_source* , sauf le *pivot_column* et *value_column*. Les colonnes de la *table_source*, sauf le *pivot_column* et *value_column*, sont appelées colonnes de regroupement de l’opérateur pivot. Pour plus d’informations sur les opérateurs PIVOT et UNPIVOT, consultez [à l’aide de PIVOT et UNPIVOT](../../t-sql/queries/from-using-pivot-and-unpivot.md).  
  
 PIVOT opère un regroupement sur la table d'entrée par rapport aux colonnes de regroupement et retourne une ligne par groupe. En outre, la sortie contient une colonne pour chaque valeur spécifiée dans le *column_list* qui s’affiche dans le *pivot_column* de la *input_table*.  
  
 Pour plus d'informations, consultez les remarques qui suivent.  
  
 *aggregate_function*  
 Fonction d'agrégation système ou définie par l'utilisateur qui accepte une ou plusieurs entrées. Cette fonction doit être indifférente aux valeurs Null. Une fonction d'agrégation indifférente aux valeurs Null ne prend pas en considération les valeurs Null dans le groupe lors de l'évaluation de la valeur d'agrégation.  
  
 La fonction d'agrégation système COUNT(*) n'est pas autorisée.  
  
 *value_column*  
 Colonne de valeur de l'opérateur PIVOT. Lorsqu’il est utilisé avec UNPIVOT, *value_column* ne peut pas être le nom d’une colonne existante dans l’entrée *table_source*.  
  
 FOR *pivot_column*  
 Colonne de tableau croisé dynamique de l'opérateur PIVOT. *pivot_column* doit être d’un type implicitement ou explicitement convertible en **nvarchar()**. Cette colonne ne peut pas être **image** ou **rowversion**.  
  
 Lorsque l’opérateur UNPIVOT est utilisé, *pivot_column* est le nom de la colonne de sortie qui est réduite à partir de la *table_source*. Il ne peut pas être une colonne existante de *table_source* portant ce nom.  
  
 IN (*column_list* )  
 Dans la clause PIVOT, répertorie les valeurs dans le *pivot_column* qui deviennent les noms de colonne de la table de sortie. La liste ne peut pas spécifier des noms de colonnes qui existent déjà dans l’entrée *table_source* qui est croisé dynamiquement.  
  
 Dans la clause UNPIVOT, répertorie les colonnes de *table_source* qui doivent être réduites à une seule *pivot_column*.  
  
 *table_alias*  
 Nom d'alias de la table de sortie. *pivot_table_alias* doit être spécifié.  
  
 UNPIVOT \< unpivot_clause >  
 Spécifie que la table d’entrée est réduite de plusieurs colonnes dans *column_list* en une seule colonne appelée *pivot_column*. Pour plus d’informations sur les opérateurs PIVOT et UNPIVOT, consultez [à l’aide de PIVOT et UNPIVOT](../../t-sql/queries/from-using-pivot-and-unpivot.md).  
  
 AS OF \<date_time>  

**S’applique aux**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  

  
 Renvoie une table avec un seul enregistrement par ligne contenant les valeurs qui étaient réelles (actuelles) au moment dans le passé spécifié. En interne, une union est effectuée entre la table temporelle et sa table d’historique et les résultats sont filtrés pour renvoyer les valeurs de la ligne qui était valide au point dans le temps spécifié par le  *\<date_heure >* paramètre. La valeur d’une ligne est considérée comme valide si le *system_start_time_column_name* la valeur est inférieure ou égale à la  *\<date_heure >* la valeur du paramètre et le *system_end_time_column_name* valeur est supérieure à la  *\<date_heure >* la valeur du paramètre.   
  
 FROM \<start_date_time> TO \<end_date_time>

**S’applique aux**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].

  
 Retourne une table avec les valeurs de toutes les versions d’enregistrement qui étaient actives pendant l’intervalle de temps spécifié, indépendamment de si elles devenues actives avant la  *\<start_date_time >* paramètre de valeur pour l’argument FROM ou qui ont cessé d’être actives après la  *\<end_date_time >* valeur de paramètre pour l’argument TO. En interne, une union est effectuée entre la table temporelle et sa table d’historique. Les résultats sont filtrés de manière à renvoyer les valeurs de toutes les versions de ligne qui étaient actives à tout moment de l’intervalle spécifié. Les lignes qui sont devenus actifs exactement sur la limite inférieure définie par le point de terminaison FROM sont incluses et les lignes qui sont devenus actifs exactement sur la limite supérieure définie par le point de terminaison TO ne sont pas inclus.  
  
 ENTRE \<start_date_time > AND \<end_date_time >  

**S’applique aux**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
 Identique à celle ci-dessus dans le **FROM \<start_date_time > à \<end_date_time >** description, mais il inclut des lignes qui sont devenues actives sur la limite supérieure définie par le \<end_date_time > point de terminaison.  
  
 CONTAINED IN (\<start_date_time> , \<end_date_time>)  

**S’applique aux**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  

  
 Renvoie une table avec les valeurs de toutes les versions d’enregistrement qui ont été ouvertes et fermées dans l’intervalle de temps spécifié défini par les deux valeurs datetime de l’argument CONTAINED IN. Les lignes qui sont devenues actives exactement sur la limite inférieure ou qui ont cessé d’être actives exactement sur la limite supérieure sont incluses.  
  
 ALL  
 Retourne une table avec les valeurs de toutes les lignes de la table actuelle et la table d’historique.  
  
## <a name="remarks"></a>Notes  
 La clause FROM prend en charge la syntaxe SQL-92 pour les tables jointes et les tables dérivées. La syntaxe SQL-92 fournit les opérateurs de jointure INNER, LEFT OUTER, RIGHT OUTER, FULL OUTER et CROSS.  
  
 UNION et JOIN à l'intérieur d'une clause FROM sont pris en charge aussi bien dans les vues que dans les tables dérivées et les sous-requêtes.  
  
 Une jointure réflexive est une table qui effectue une jointure avec elle-même. Les insertions ou les mises à jour basées sur une jointure réflexive suivent l'ordre de la clause FROM.  
  
 Sachant que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en compte les statistiques de distribution et de cardinalité à partir des serveurs liés qui fournissent les statistiques de distribution des colonnes, l'indicateur de jointure REMOTE n'est pas nécessaire pour forcer l'évaluation d'une jointure à distance. Le processeur de requêtes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en considération les statistiques distantes et détermine l'opportunité ou non d'une stratégie de jointure distante. L'indicateur de jointure REMOTE est utile pour les fournisseurs qui ne produisent pas de statistiques de distribution des colonnes.  
  
## <a name="using-apply"></a>Utilisation de l'opérateur APPLY  
 Les opérandes de gauche et de droite de l'opérateur APPLY sont des expressions de table. La principale différence entre ces opérandes est que le *right_table_source* peut utiliser une fonction table qui prend une colonne à partir de la *left_table_source* comme l’un des arguments de la fonction. Le *left_table_source* peut inclure des fonctions table, mais il ne peut pas contenir d’arguments qui sont des colonnes à partir de la *right_table_source*.  
  
 L'opérateur APPLY fonctionne de la même façon pour produire la source de table pour la clause FROM :  
  
1.  Prend la valeur *right_table_source* par rapport à chaque ligne de la *left_table_source* pour produire des ensembles de lignes.  
  
     Les valeurs dans le *right_table_source* dépendent *left_table_source*. *right_table_source* peut être représenté approximativement de cette façon : `TVF(left_table_source.row)`, où `TVF` est une fonction table.  
  
2.  Combine les jeux de résultats qui est générés pour chaque ligne dans l’évaluation de *right_table_source* avec la *left_table_source* en effectuant une opération UNION.  
  
     La liste des colonnes produites par le résultat de l’opérateur APPLY est l’ensemble de colonnes à partir de la *left_table_source* qui est associé à la liste des colonnes à partir de la *right_table_source*.  
  
## <a name="using-pivot-and-unpivot"></a>Utilisation des opérateurs PIVOT et UNPIVOT  
 Le *pivot_column* et *value_column* sont des colonnes de regroupement sont utilisées par l’opérateur PIVOT. PIVOT suit le processus ci-après pour obtenir le jeu de résultats de sortie :  
  
1.  Effectue un GROUP BY sur son *input_table* sur le regroupement colonnes et génère une ligne de sortie pour chaque groupe.  
  
     Les colonnes de regroupement dans la ligne de sortie obtiennent les valeurs de colonne correspondante pour ce groupe dans le *input_table*.  
  
2.  Il génère des valeurs pour les colonnes dans la liste de colonnes pour chaque ligne de sortie en effectuant les opérations suivantes :  
  
    1.  Regroupement supplémentaire des lignes générées dans GROUP BY à l’étape précédente par rapport à la *pivot_column*.  
  
         Pour chaque colonne de sortie dans le *column_list*, en sélectionnant un sous-groupe qui satisfait la condition :  
  
         `pivot_column = CONVERT(<data type of pivot_column>, 'output_column')`  
  
    2.  *aggregate_function* est évalué par rapport à la *value_column* sur ce sous-groupe et son résultat est retourné en tant que la valeur correspondantes *output_column*. Si le sous-groupe est vide, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère une valeur null pour cette *output_column*. Si la fonction d'agrégation est COUNT et si le sous-groupe est vide, la valeur zéro (0) est retournée.  

> [!NOTE]
> Les identificateurs de colonne dans la `UNPIVOT` clause suivre le classement de catalogue. Pour [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], le classement est toujours `SQL_Latin1_General_CP1_CI_AS`. Pour [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] contenant-contenus partielle des bases de données, le classement est toujours `Latin1_General_100_CI_AS_KS_WS_SC`. Si la colonne est combinée avec d’autres colonnes, puis une clause collate (`COLLATE DATABASE_DEFAULT`) est nécessaire pour éviter les conflits.   
  
 Pour plus d’informations sur les opérateurs PIVOT et UNPIVOT, y compris des exemples, consultez [à l’aide de PIVOT et UNPIVOT](../../t-sql/queries/from-using-pivot-and-unpivot.md).  
  
## <a name="permissions"></a>Autorisations  
 Nécessite les autorisations appropriées pour l'instruction DELETE, SELECT ou UPDATE.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-a-simple-from-clause"></a>A. Utilisation d'une clause FROM simple  
 L'exemple suivant récupère les colonnes `TerritoryID` et `Name` à partir de la table `SalesTerritory` dans l'exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```sql    
SELECT TerritoryID, Name  
FROM Sales.SalesTerritory  
ORDER BY TerritoryID ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
TerritoryID Name                            
----------- ------------------------------  
1           Northwest                       
2           Northeast                       
3           Central                         
4           Southwest                       
5           Southeast                       
6           Canada                          
7           France                          
8           Germany                         
9           Australia                       
10          United Kingdom                  
(10 row(s) affected)  
```  
  
### <a name="b-using-the-tablock-and-holdlock-optimizer-hints"></a>B. Utilisation des indicateurs d'optimiseur TABLOCK et HOLDLOCK  
 La transaction partielle suivante illustre le mode de placement d'un verrou de table partagé explicite sur `Employee` et le mode de lecture de l'index. Le verrou est conservé pendant toute la transaction.  
  
```sql    
BEGIN TRAN  
SELECT COUNT(*)   
FROM HumanResources.Employee WITH (TABLOCK, HOLDLOCK) ;  
```  
  
### <a name="c-using-the-sql-92-cross-join-syntax"></a>C. Utilisation de la syntaxe SQL-92 CROSS JOIN  
 L'exemple suivant retourne le produit croisé des deux tables `Employee` et `Department` dans la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Une liste de toutes les combinaisons possibles des `BusinessEntityID` lignes et tous les `Department` est retournée.  
  
```wql    
SELECT e.BusinessEntityID, d.Name AS Department  
FROM HumanResources.Employee AS e  
CROSS JOIN HumanResources.Department AS d  
ORDER BY e.BusinessEntityID, d.Name ;  
```  
  
### <a name="d-using-the-sql-92-full-outer-join-syntax"></a>D. Utilisation de la syntaxe SQL-92 FULL OUTER JOIN  
 L'exemple suivant retourne le nom de produit et les commandes correspondantes dans la table `SalesOrderDetail` de la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Il retourne également les commandes dont les produits ne sont pas répertoriés dans la table `Product`, ainsi que tous les produits dont la commande est différente de celle répertoriée dans la table `Product`.  
  
```sql  
-- The OUTER keyword following the FULL keyword is optional.  
SELECT p.Name, sod.SalesOrderID  
FROM Production.Product AS p  
FULL OUTER JOIN Sales.SalesOrderDetail AS sod  
ON p.ProductID = sod.ProductID  
ORDER BY p.Name ;  
```  
  
### <a name="e-using-the-sql-92-left-outer-join-syntax"></a>E. Utilisation de la syntaxe SQL-92 LEFT OUTER JOIN  
 L'exemple suivant joint deux tables sur `ProductID` et conserve les lignes sans correspondance de la table de gauche. La table `Product` correspond à la table `SalesOrderDetail` sur les colonnes `ProductID` de chaque table. Tous les produits, qu'ils soient commandés ou non, apparaissent dans le jeu de résultats.  
  
```sql    
SELECT p.Name, sod.SalesOrderID  
FROM Production.Product AS p  
LEFT OUTER JOIN Sales.SalesOrderDetail AS sod  
ON p.ProductID = sod.ProductID  
ORDER BY p.Name ;  
```  
  
### <a name="f-using-the-sql-92-inner-join-syntax"></a>F. Utilisation de la syntaxe SQL-92 INNER JOIN  
 L'exemple suivant retourne tous les noms de produits et tous les ID de commandes.  
  
```sql    
-- By default, SQL Server performs an INNER JOIN if only the JOIN   
-- keyword is specified.  
SELECT p.Name, sod.SalesOrderID  
FROM Production.Product AS p  
INNER JOIN Sales.SalesOrderDetail AS sod  
ON p.ProductID = sod.ProductID  
ORDER BY p.Name ;  
```  
  
### <a name="g-using-the-sql-92-right-outer-join-syntax"></a>G. Utilisation de la syntaxe SQL-92 RIGHT OUTER JOIN  
 L'exemple suivant joint deux tables sur `TerritoryID` et conserve les lignes sans correspondance de la table de droite. La table `SalesTerritory` correspond à la table `SalesPerson` sur la colonne `TerritoryID` de chaque table. Tous les vendeurs apparaissent dans le jeu de résultats, qu'un secteur leur ait été attribué ou non.  
  
```sql    
SELECT st.Name AS Territory, sp.BusinessEntityID  
FROM Sales.SalesTerritory AS st   
RIGHT OUTER JOIN Sales.SalesPerson AS sp  
ON st.TerritoryID = sp.TerritoryID ;  
```  
  
### <a name="h-using-hash-and-merge-join-hints"></a>H. Utilisation des indicateurs de jointure HASH et MERGE  
 L'exemple suivant effectue une jointure sur trois tables parmi les tables `Product`, `ProductVendor` et `Vendor` afin de produire une liste de produits et de leurs fournisseurs. L'optimiseur de requête joint `Product` et `ProductVendor` (`p` et `pv`) à l'aide d'une jointure MERGE. Ensuite, les résultats de la jointure MERGE `Product` et `ProductVendor` (`p` et `pv`) sont joints à l'aide de HASH à la table `Vendor` pour produire (`p` et `pv`) et `v`.  
  
> [!IMPORTANT]  
>  Lorsqu'un indicateur de jointure est spécifié, le mot clé INNER n'est plus facultatif et doit être déclaré de manière explicite pour l'exécution d'une jointure INNER JOIN.  
  
```sql    
SELECT p.Name AS ProductName, v.Name AS VendorName  
FROM Production.Product AS p   
INNER MERGE JOIN Purchasing.ProductVendor AS pv   
ON p.ProductID = pv.ProductID  
INNER HASH JOIN Purchasing.Vendor AS v  
ON pv.BusinessEntityID = v.BusinessEntityID  
ORDER BY p.Name, v.Name ;  
```  
  
### <a name="i-using-a-derived-table"></a>I. Utilisation d'une table dérivée  
 L'exemple suivant se sert d'une table dérivée, d'une instruction `SELECT` après la clause `FROM`, pour retourner les prénoms et noms de tous les employés ainsi que leur ville de résidence.  
  
```sql    
SELECT RTRIM(p.FirstName) + ' ' + LTRIM(p.LastName) AS Name, d.City  
FROM Person.Person AS p  
INNER JOIN HumanResources.Employee e ON p.BusinessEntityID = e.BusinessEntityID   
INNER JOIN  
   (SELECT bea.BusinessEntityID, a.City   
    FROM Person.Address AS a  
    INNER JOIN Person.BusinessEntityAddress AS bea  
    ON a.AddressID = bea.AddressID) AS d  
ON p.BusinessEntityID = d.BusinessEntityID  
ORDER BY p.LastName, p.FirstName;  
```  
  
### <a name="j-using-tablesample-to-read-data-from-a-sample-of-rows-in-a-table"></a>J. Utilisation de TABLESAMPLE pour lire des données à partir d'un exemple de lignes dans une table  
 L'exemple suivant utilise `TABLESAMPLE` dans la clause `FROM` pour retourner environ `10` % de toutes les lignes de la table `Customer`.  
  
```sql    
SELECT *  
FROM Sales.Customer TABLESAMPLE SYSTEM (10 PERCENT) ;  
```  
  
### <a name="k-using-apply"></a>K. Utilisation de l'opérateur APPLY  
 L'exemple suivant suppose que les tables ci-après associées au schéma suivant existent dans la base de données :  
  
-   `Departments`: `DeptID`, `DivisionID`, `DeptName`, `DeptMgrID`  
  
-   `EmpMgr`: `MgrID`, `EmpID`  
  
-   `Employees`: `EmpID`, `EmpLastName`, `EmpFirstName`, `EmpSalary`  
  
 Il existe également une fonction table, `GetReports(MgrID)`, qui retourne la liste de tous les employés (`EmpID`, `EmpLastName`, `EmpSalary`) qui rendent directement ou indirectement compte au `MgrID` spécifié.  
  
 L'exemple utilise `APPLY` pour retourner tous les services et tous les employés qui en font partie. Si un service particulier est dépourvu d'employés, aucune ligne n'est retournée pour celui-ci.  
  
```sql
SELECT DeptID, DeptName, DeptMgrID, EmpID, EmpLastName, EmpSalary  
FROM Departments d CROSS APPLY dbo.GetReports(d.DeptMgrID) ;  
```  
  
 Si vous souhaitez que la requête génère des lignes pour ces services sans employés, ce qui produira des valeurs NULL pour les colonnes `EmpID`, `EmpLastName` et `EmpSalary`, utilisez `OUTER APPLY` à la place.  
  
```sql
SELECT DeptID, DeptName, DeptMgrID, EmpID, EmpLastName, EmpSalary  
FROM Departments d OUTER APPLY dbo.GetReports(d.DeptMgrID) ;  
```  
  
### <a name="l-using-cross-apply"></a>L. Utilisation de l'opérateur CROSS APPLY  
 L'exemple suivant récupère un instantané de tous les plans de requête résidant dans la mémoire cache des plans, en interrogeant la vue de gestion dynamique `sys.dm_exec_cached_plans` pour récupérer les descripteurs de plan de tous les plans de requête dans le cache. L'opérateur `CROSS APPLY` est spécifié pour transmettre les descripteurs de plan à `sys.dm_exec_query_plan`. La sortie du plan d'exécution de requêtes XML pour chaque plan actuellement dans la mémoire cache des plans se trouve dans la colonne `query_plan` de la table retournée.  
  
```sql
USE master;  
GO  
SELECT dbid, object_id, query_plan   
FROM sys.dm_exec_cached_plans AS cp   
CROSS APPLY sys.dm_exec_query_plan(cp.plan_handle);   
GO  
```  
  
### <a name="m-using-for-systemtime"></a>M. À l’aide de l’instruction FOR SYSTEM_TIME  
  
**S’applique aux**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] via [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].  
  
 L’exemple suivant utilise l’argument de date_time_literal_or_variable FOR SYSTEM_TIME AS OF pour retourner les lignes de la table qui étaient réelles (actuelles) à compter du 1er janvier 2014.  
  
```sql
SELECT DepartmentNumber,   
    DepartmentName,   
    ManagerID,   
    ParentDepartmentNumber   
FROM DEPARTMENT  
FOR SYSTEM_TIME AS OF '2014-01-01'  
WHERE ManagerID = 5;
```  
  
 L’exemple suivant utilise le FOR SYSTEM_TIME FROM date_time_literal_or_variable date_time_literal_or_variable argument TO renvoie toutes les lignes qui étaient actives pendant la période définie en tant qu’à compter du 1er janvier 2013 et se terminant par le 1er janvier 2014, à l’exclusion de la limite supérieure.  
  
```sql
SELECT DepartmentNumber,   
    DepartmentName,   
    ManagerID,   
    ParentDepartmentNumber   
FROM DEPARTMENT  
FOR SYSTEM_TIME FROM '2013-01-01' TO '2014-01-01'  
WHERE ManagerID = 5;
```  
  
 L’exemple suivant utilise le date_time_literal_or_variable pour SYSTEM_TIME entre et argument date_time_literal_or_variable pour retourner toutes les lignes qui étaient actives pendant la période définie en tant qu’à compter du 1er janvier 2013 et en terminant par le 1er janvier 2014, qui inclut la limite supérieure.  
  
```sql
SELECT DepartmentNumber,   
    DepartmentName,   
    ManagerID,   
    ParentDepartmentNumber   
FROM DEPARTMENT  
FOR SYSTEM_TIME BETWEEN '2013-01-01' AND '2014-01-01'  
WHERE ManagerID = 5;
```  
  
 L’exemple suivant utilise le pour argument SYSTEM_TIME CONTAINED IN (date_time_literal_or_variable, date_time_literal_or_variable) pour retourner toutes les lignes qui ont été ouvertes et fermées pendant la période définie en tant qu’à compter du 1er janvier 2013 et se terminant par le 1er janvier 2014.  
  
```sql
SELECT DepartmentNumber,   
    DepartmentName,   
    ManagerID,   
    ParentDepartmentNumber   
FROM DEPARTMENT  
FOR SYSTEM_TIME CONTAINED IN ( '2013-01-01', '2014-01-01' )  
WHERE ManagerID = 5;
```  
  
 L’exemple suivant utilise une variable, plutôt qu’un littéral pour fournir les valeurs limites de date pour la requête.  
  
```sql
DECLARE @AsOfFrom datetime2 = dateadd(month,-12, sysutcdatetime());
DECLARE @AsOfTo datetime2 = dateadd(month,-6, sysutcdatetime());
  
SELECT DepartmentNumber,   
    DepartmentName,   
    ManagerID,   
    ParentDepartmentNumber   
FROM DEPARTMENT  
FOR SYSTEM_TIME FROM @AsOfFrom TO @AsOfTo  
WHERE ManagerID = 5;
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="n-using-the-inner-join-syntax"></a>N. À l’aide de la syntaxe INNER JOIN  
 L’exemple suivant retourne le `SalesOrderNumber`, `ProductKey`, et `EnglishProductName` colonnes à partir de la `FactInternetSales` et `DimProduct` tables où la clé de jointure, `ProductKey`, correspond à dans les deux tables. Le `SalesOrderNumber` et `EnglishProductName` colonnes chaque existent dans une des tables uniquement, donc il n’est pas nécessaire de spécifier l’alias de table avec ces colonnes, comme le montre ; ces alias sont inclus pour une meilleure lisibilité. Le mot **AS** avant un alias de nom n’est pas obligatoire, mais est recommandé pour une meilleure lisibilité et pour se conformer à la norme ANSI.  
  
```sql
-- Uses AdventureWorks  
  
SELECT fis.SalesOrderNumber, dp.ProductKey, dp.EnglishProductName  
FROM FactInternetSales AS fis 
INNER JOIN DimProduct AS dp  
    ON dp.ProductKey = fis.ProductKey;  
```  
  
 Étant donné que le `INNER` mot clé n’est pas requis pour les jointures internes, cette même requête peut être écrite en tant que :  
  
```sql
-- Uses AdventureWorks  
  
SELECT fis.SalesOrderNumber, dp.ProductKey, dp.EnglishProductName  
FROM FactInternetSales AS fis 
JOIN DimProduct AS dp  
ON dp.ProductKey = fis.ProductKey;  
```  
  
 A `WHERE` clause peut également être utilisée avec cette requête pour limiter les résultats. Cet exemple limite les résultats aux `SalesOrderNumber` valeurs supérieures à 'SO5000' :  
  
```sql
-- Uses AdventureWorks  
  
SELECT fis.SalesOrderNumber, dp.ProductKey, dp.EnglishProductName  
FROM FactInternetSales AS fis 
JOIN DimProduct AS dp  
    ON dp.ProductKey = fis.ProductKey  
WHERE fis.SalesOrderNumber > 'SO50000'  
ORDER BY fis.SalesOrderNumber;  
```  
  
### <a name="o-using-the-left-outer-join-and-right-outer-join-syntax"></a>O. À l’aide de la syntaxe LEFT OUTER JOIN et RIGHT OUTER JOIN  
 L’exemple suivant joint le `FactInternetSales` et `DimProduct` des tables sur la `ProductKey` colonnes. La syntaxe de jointure externe gauche conserve les lignes sans correspondance à partir de la gauche (`FactInternetSales`) table. Étant donné que la `FactInternetSales` table ne contient pas de `ProductKey` les valeurs qui ne correspondent pas à la `DimProduct` table, cette requête renvoie les mêmes lignes que le premier exemple de jointure interne ci-dessus.  
  
```sql
-- Uses AdventureWorks  
  
SELECT fis.SalesOrderNumber, dp.ProductKey, dp.EnglishProductName  
FROM FactInternetSales AS fis 
LEFT OUTER JOIN DimProduct AS dp  
    ON dp.ProductKey = fis.ProductKey;  
```  
  
 Cette requête peut aussi être écrite sans la `OUTER` (mot clé).  
  
 Dans les jointures externes droites, les lignes sans correspondance à partir de la table de droite sont conservés. L’exemple suivant retourne les mêmes lignes que l’exemple de jointure externe gauche ci-dessus.  
  
```sql
-- Uses AdventureWorks  
  
SELECT fis.SalesOrderNumber, dp.ProductKey, dp.EnglishProductName  
FROM DimProduct AS dp 
RIGHT OUTER JOIN FactInternetSales AS fis  
    ON dp.ProductKey = fis.ProductKey;  
```  
  
 La requête suivante utilise le `DimSalesTerritory` table en tant que la table de gauche dans une jointure externe gauche. Il récupère le `SalesOrderNumber` les valeurs à partir de la `FactInternetSales` table. Si aucune commande pour un particulier `SalesTerritoryKey`, la requête retournera une valeur NULL pour le `SalesOrderNumber` pour cette ligne. Cette requête est triée par la `SalesOrderNumber` colonne, afin que les valeurs NULL dans cette colonne s’affiche en haut des résultats.  
  
```sql
-- Uses AdventureWorks  
  
SELECT dst.SalesTerritoryKey, dst.SalesTerritoryRegion, fis.SalesOrderNumber  
FROM DimSalesTerritory AS dst 
LEFT OUTER JOIN FactInternetSales AS fis  
    ON dst.SalesTerritoryKey = fis.SalesTerritoryKey  
ORDER BY fis.SalesOrderNumber;  
```  
  
 Cette requête peut être réécrit avec une jointure externe droite pour extraire les mêmes résultats :  
  
```sql
-- Uses AdventureWorks  
  
SELECT dst.SalesTerritoryKey, dst.SalesTerritoryRegion, fis.SalesOrderNumber  
FROM FactInternetSales AS fis 
RIGHT OUTER JOIN DimSalesTerritory AS dst  
    ON fis.SalesTerritoryKey = dst.SalesTerritoryKey  
ORDER BY fis.SalesOrderNumber;  
```  
  
### <a name="p-using-the-full-outer-join-syntax"></a>P. À l’aide de la syntaxe FULL OUTER JOIN  
 L’exemple suivant montre une jointure externe complète, qui retourne toutes les lignes des deux tables jointes, mais retourne la valeur NULL pour les valeurs qui ne correspondent pas à partir de l’autre table.  
  
```sql
-- Uses AdventureWorks  
  
SELECT dst.SalesTerritoryKey, dst.SalesTerritoryRegion, fis.SalesOrderNumber  
FROM DimSalesTerritory AS dst 
FULL OUTER JOIN FactInternetSales AS fis  
    ON dst.SalesTerritoryKey = fis.SalesTerritoryKey  
ORDER BY fis.SalesOrderNumber;  
```  
  
 Cette requête peut aussi être écrite sans la `OUTER` (mot clé).  
  
```sql
-- Uses AdventureWorks  
  
SELECT dst.SalesTerritoryKey, dst.SalesTerritoryRegion, fis.SalesOrderNumber  
FROM DimSalesTerritory AS dst 
FULL JOIN FactInternetSales AS fis  
    ON dst.SalesTerritoryKey = fis.SalesTerritoryKey  
ORDER BY fis.SalesOrderNumber;  
```  
  
### <a name="q-using-the-cross-join-syntax"></a>Q. À l’aide de la syntaxe CROSS JOIN  
 L’exemple suivant retourne le produit croisé de la `FactInternetSales` et `DimSalesTerritory` tables. Une liste de toutes les combinaisons possibles des `SalesOrderNumber` et `SalesTerritoryKey` sont retournées. Notez l’absence de la `ON` clause dans la requête de jointure croisée.  
  
```sql
-- Uses AdventureWorks  
  
SELECT dst.SalesTerritoryKey, fis.SalesOrderNumber  
FROM DimSalesTerritory AS dst 
CROSS JOIN FactInternetSales AS fis  
ORDER BY fis.SalesOrderNumber;  
```  
  
### <a name="r-using-a-derived-table"></a>R. Utilisation d'une table dérivée  
 L’exemple suivant utilise une table dérivée (un `SELECT` instruction après le `FROM` clause) pour retourner le `CustomerKey` et `LastName` colonnes de tous les clients dans le `DimCustomer` table avec `BirthDate` valeurs au plus tard le 1er janvier 1970 et le dernier nom de « Smith ».  
  
```sql
-- Uses AdventureWorks  
  
SELECT CustomerKey, LastName  
FROM  
   (SELECT * FROM DimCustomer  
    WHERE BirthDate > '01/01/1970') AS DimCustomerDerivedTable  
WHERE LastName = 'Smith'  
ORDER BY LastName;  
```  
  
### <a name="s-reduce-join-hint-example"></a>S. RÉDUIRE l’exemple d’indicateur de jointure  
 L’exemple suivant utilise le `REDUCE` indicateur de jointure à modifier le traitement de la table dérivée dans la requête. Lorsque vous utilisez la `REDUCE` indicateur de jointure dans cette requête, le `fis.ProductKey` est projetée, répliquées et apportées distinctes, puis attachées à `DimProduct` lors de la lecture aléatoire de `DimProduct` sur `ProductKey`. La table dérivée qui en résulte est distribuée sur `fis.ProductKey`.  
  
```sql
-- Uses AdventureWorks  
  
EXPLAIN SELECT SalesOrderNumber  
FROM  
   (SELECT fis.SalesOrderNumber, dp.ProductKey, dp.EnglishProductName  
    FROM DimProduct AS dp   
      INNER REDUCE JOIN FactInternetSales AS fis   
          ON dp.ProductKey = fis.ProductKey  
   ) AS dTable  
ORDER BY SalesOrderNumber;  
```  
  
### <a name="t-replicate-join-hint-example"></a>T. Exemple d’indicateur de jointure de réplication  
 L’exemple suivant montre la même requête que l’exemple précédent, à ceci près qu’un `REPLICATE` indicateur de jointure est utilisée au lieu du `REDUCE` indicateur de jointure. Utiliser le `REPLICATE` indicateur entraîne les valeurs dans le `ProductKey` colonne (jointure) à partir de la `FactInternetSales` table être répliquée vers tous les nœuds. Le `DimProduct` table est jointe à la version dupliquée de ces valeurs.  
  
```sql
-- Uses AdventureWorks  
  
EXPLAIN SELECT SalesOrderNumber  
FROM  
   (SELECT fis.SalesOrderNumber, dp.ProductKey, dp.EnglishProductName  
    FROM DimProduct AS dp   
      INNER REPLICATE JOIN FactInternetSales AS fis  
          ON dp.ProductKey = fis.ProductKey  
   ) AS dTable  
ORDER BY SalesOrderNumber;  
```  
  
### <a name="u-using-the-redistribute-hint-to-guarantee-a-shuffle-move-for-a-distribution-incompatible-join"></a>U. À l’aide de l’indicateur REDISTRIBUTE afin de garantir un déplacement de la réorganisation d’une jointure incompatible de distribution  
 La requête suivante utilise l’indicateur de requête redistribuer sur une jointure incompatible de distribution. Cela garantit que l’optimiseur de requête utilise un déplacement de lire de façon aléatoire dans le plan de requête. Cela garantit également que le plan de requête n’utilise pas un déplacement de diffusion qui déplace une table distribuée à une table répliquée.  
  
 Dans l’exemple suivant, l’indicateur REDISTRIBUTE force un déplacement aléatoire sur la table FactInternetSales car ProductKey est la colonne de distribution pour DimProduct et n’est pas la colonne de distribution pour FactInternetSales.  
  
```sql
-- Uses AdventureWorks  
  
EXPLAIN  
SELECT dp.ProductKey, fis.SalesOrderNumber, fis.TotalProductCost  
FROM DimProduct AS dp 
INNER REDISTRIBUTE JOIN FactInternetSales AS fis  
    ON dp.ProductKey = fis.ProductKey;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [FREETEXTTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [INSÉRER une &#40; Transact-SQL &#41;](../../t-sql/statements/insert-transact-sql.md)   
 [OPENQUERY &#40;Transact-SQL&#41;](../../t-sql/functions/openquery-transact-sql.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)   
 [Operators &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)   
 [WHERE &#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)  

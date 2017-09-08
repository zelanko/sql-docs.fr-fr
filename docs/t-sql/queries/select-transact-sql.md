---
title: SELECT (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SELECT_TSQL
- SELECT
dev_langs:
- TSQL
helpviewer_keywords:
- retrieving rows
- SELECT statement [SQL Server]
- SELECT statement [SQL Server], about SELECT statement
- row retrieval [SQL Server], SELECT statement
- DML [SQL Server], SELECT statement
- data manipulation language [SQL Server], SELECT statement
- row retrieval [SQL Server]
- queries [SQL Server], results
ms.assetid: dc85caea-54d1-49af-b166-f3aa2f3a93d0
caps.latest.revision: 51
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3cebbb09ffbc437ebdb4c0d0f5fdc5cf5a59adea
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="select-transact-sql"></a>SELECT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Récupère des lignes de la base de données et permet de sélectionner une ou plusieurs lignes ou colonnes à partir d’une ou plusieurs tables dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La syntaxe complète de l'instruction SELECT est complexe mais en voici les principales clauses :  
  
[Avec {[XMLNAMESPACES], [ \<common_table_expression >]}]
  
 Sélectionnez *select_list* [INTO *nouvelle_table* ]  
  
 [À partir de *table_source* ] [où *search_condition* ]  
  
 [GROUP BY *group_by_expression* ]  
  
 [Ayant *search_condition* ]  
  
 [ORDER BY *expression_trier_par* [ASC | DESC]]  
  
 L’UNION, EXCEPT et INTERSECT opérateurs peuvent être utilisés entre les requêtes pour combiner ou comparer leurs résultats dans le jeu de résultats.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
<SELECT statement> ::=    
    [ WITH { [ XMLNAMESPACES ,] [ <common_table_expression> [,...n] ] } ]  
    <query_expression>   
    [ ORDER BY { order_by_expression | column_position [ ASC | DESC ] }   
  [ ,...n ] ]   
    [ <FOR Clause>]   
    [ OPTION ( <query_hint> [ ,...n ] ) ]   
<query_expression> ::=   
    { <query_specification> | ( <query_expression> ) }   
    [  { UNION [ ALL ] | EXCEPT | INTERSECT }  
        <query_specification> | ( <query_expression> ) [...n ] ]   
<query_specification> ::=   
SELECT [ ALL | DISTINCT ]   
    [TOP ( expression ) [PERCENT] [ WITH TIES ] ]   
    < select_list >   
    [ INTO new_table ]   
    [ FROM { <table_source> } [ ,...n ] ]   
    [ WHERE <search_condition> ]   
    [ <GROUP BY> ]   
    [ HAVING < search_condition > ]   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
[ WITH <common_table_expression> [ ,...n ] ]  
SELECT <select_criteria>  
[;]  
  
<select_criteria> ::=  
    [ TOP ( top_expression ) ]   
    [ ALL | DISTINCT ]   
    { * | column_name | expression } [ ,...n ]   
    [ FROM { table_source } [ ,...n ] ]  
    [ WHERE <search_condition> ]   
    [ GROUP BY <group_by_clause> ]   
    [ HAVING <search_condition> ]   
    [ ORDER BY <order_by_expression> ]  
    [ OPTION ( <query_option> [ ,...n ] ) ]  
  
```  
  
## <a name="remarks"></a>Notes  
 En raison de la complexité de l'instruction SELECT, les éléments et les arguments de la syntaxe sont détaillés par clause :  
  
|||  
|-|-|  
|[WITH XMLNAMESPACES](../../t-sql/xml/with-xmlnamespaces.md)<br /><br /> [WITH common_table_expression](../../t-sql/queries/with-common-table-expression-transact-sql.md)|[AVOIR](../../t-sql/queries/select-having-transact-sql.md)|  
|[SELECT (Clause)](../../t-sql/queries/select-clause-transact-sql.md)|[UNION](../../t-sql/language-elements/set-operators-union-transact-sql.md)|  
|[Clause INTO](../../t-sql/queries/select-into-clause-transact-sql.md)|[EXCEPT et INTERSECT](../../t-sql/language-elements/set-operators-except-and-intersect-transact-sql.md)|  
|[FROM](../../t-sql/queries/from-transact-sql.md)|[TRIER PAR](../../t-sql/queries/select-order-by-clause-transact-sql.md)|  
|[WHERE](../../t-sql/queries/where-transact-sql.md)|[Clause FOR](../../t-sql/queries/select-for-clause-transact-sql.md)|  
|[REGROUPER PAR](../../t-sql/queries/select-group-by-transact-sql.md)|[OPTION, clause](../../t-sql/queries/option-clause-transact-sql.md)|  
  
 L'ordre des clauses dans une instruction SELECT est de première importance. Vous pouvez omettre n'importe quelle clause facultative mais, lorsque vous employez les clauses facultatives, elles doivent apparaître dans l'ordre adéquat.  
  
 Les instructions SELECT sont autorisées dans les fonctions définies par l'utilisateur uniquement si les listes de sélection de ces instructions contiennent des expressions qui attribuent des valeurs aux variables qui sont locales aux fonctions.  
  
 Un nom en quatre parties est construit avec la fonction OPENDATASOURCE comme la partie nom de serveur peut être utilisé comme source de table, partout où un nom de table peut apparaître dans une instruction SELECT. Impossible de spécifier un nom en quatre parties pour [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Certaines restrictions syntaxiques s'appliquent aux instructions SELECT impliquant des tables distantes.  
  
## <a name="logical-processing-order-of-the-select-statement"></a>Ordre de traitement logique de l'instruction SELECT  
 Les étapes suivantes indiquent l'ordre de traitement logique, ou ordre de liaison, d'une instruction SELECT. Cet ordre détermine à quel moment les objets définis au cours d'une étape deviennent disponibles pour les clauses des étapes suivantes. Par exemple, si le processeur de requêtes peut se lier (accéder) aux tables ou vues définies dans la clause FROM, ces objets et leurs colonnes deviennent disponibles pour toutes les étapes suivantes. À l'inverse, puisque la clause SELECT correspond à l'étape 8, aucun alias de colonne ni aucune colonne dérivée défini(e) dans cette clause ne peut être référencé(e) par les clauses précédentes. Cependant, ils peuvent être référencés par les clauses suivantes telles que la clause ORDER BY. L’exécution physique réelle de l’instruction est déterminée par le processeur de requêtes et l’ordre peut différer de cette liste.  
  
1.  FROM  
2.  ON  
3.  JOIN  
4.  WHERE  
5.  GROUP BY  
6.  WITH CUBE ou WITH ROLLUP  
7.  HAVING  
8.  SELECT  
9. DISTINCT  
10. ORDER BY  
11. HAUT  
  
## <a name="permissions"></a>Permissions  
 La sélection de données requiert l'autorisation **SELECT** sur la table ou la vue, qui pourrait être héritée d'une étendue supérieure telle que l'autorisation **SELECT** sur le schéma ou l'autorisation **CONTROL** sur la table. Ou nécessite l’appartenance dans le **db_datareader** ou **db_owner** rôles de base de données fixes ou le **sysadmin** rôle serveur fixe. Création d’une table à l’aide **SELECTINTO** requiert également le **CREATETABLE** autorisation et la **ALTERSCHEMA** autorisation sur le schéma qui possède la nouvelle table.  
  
## <a name="examples"></a>Exemples :   
Les exemples suivants utilisent la base de données [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)].
  
### <a name="a-using-select-to-retrieve-rows-and-columns"></a>A. Utilisation de SELECT pour extraire des lignes et des colonnes  
 Cette section présente trois exemples de code. Ce premier exemple de code retourne toutes les lignes (aucune clause WHERE n’est spécifié) et toutes les colonnes (à l’aide de la `*`) à partir de la `DimEmployee` table.  
  
```sql  
SELECT *  
FROM DimEmployee  
ORDER BY LastName;  
```  
  
 Exemple suivant à l’aide d’alias de table pour obtenir le même résultat.  
  
```sql  
SELECT e.*  
FROM DimEmployee AS e  
ORDER BY LastName;  
```  
  
 Cet exemple retourne toutes les lignes (aucune clause WHERE n’est spécifié) et un sous-ensemble des colonnes (`FirstName`, `LastName`, `StartDate`) à partir de la `DimEmployee` de table dans le `AdventureWorksPDW2012` base de données. La troisième colonne est renommée `FirstDay`.  
  
```sql  
SELECT FirstName, LastName, StartDate AS FirstDay  
FROM DimEmployee   
ORDER BY LastName;  
```  
  
 Cet exemple retourne uniquement les lignes de `DimEmployee` qui ont un `EndDate` qui n’est pas NULL et une `MaritalStatus` d’am » (marié).  
  
```sql  
SELECT FirstName, LastName, StartDate AS FirstDay  
FROM DimEmployee   
WHERE EndDate IS NOT NULL   
AND MaritalStatus = 'M'  
ORDER BY LastName;  
```  
  
### <a name="b-using-select-with-column-headings-and-calculations"></a>B. Utilisation de SELECT avec des en-têtes de colonne et des calculs  
 L’exemple suivant retourne toutes les lignes de la `DimEmployee` table et calcule le salaire brut de chaque employé en fonction de leur `BaseRate` et une semaine de 40 heures de travail.  
  
```sql  
SELECT FirstName, LastName, BaseRate, BaseRate * 40 AS GrossPay  
FROM DimEmployee  
ORDER BY LastName;  
```  
  
### <a name="c-using-distinct-with-select"></a>C. Utilisation de DISTINCT avec SELECT  
 L’exemple suivant utilise `DISTINCT` pour générer une liste de tous les titres uniques dans le `DimEmployee` table.  
  
```sql  
SELECT DISTINCT Title  
FROM DimEmployee  
ORDER BY Title;  
```  
  
### <a name="d-using-group-by"></a>D. Utilisation de GROUP BY  
 L’exemple suivant recherche la quantité totale de toutes les ventes chaque jour.  
  
```sql  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales  
FROM FactInternetSales  
GROUP BY OrderDateKey  
ORDER BY OrderDateKey;  
```  
  
 Raison de le `GROUP BY` clause, qu’une seule ligne contenant la somme de toutes les ventes est retournée pour chaque jour.  
  
### <a name="e-using-group-by-with-multiple-groups"></a>E. Utilisation de GROUP BY avec plusieurs groupes  
 L’exemple suivant recherche le prix moyen et la somme des ventes sur Internet pour chaque jour, regroupées par date de commande et la clé de la promotion.  
  
```sql  

SELECT OrderDateKey, PromotionKey, AVG(SalesAmount) AS AvgSales, SUM(SalesAmount) AS TotalSales  
FROM FactInternetSales  
GROUP BY OrderDateKey, PromotionKey  
ORDER BY OrderDateKey;   
```  
  
### <a name="f-using-group-by-and-where"></a>F. Utilisation de GROUP BY et WHERE  
 L’exemple suivant place les résultats en groupes après n’avoir extrait uniquement les lignes avec des dates de commande au plus tard le 1er août 2002.  
  
```sql  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales  
FROM FactInternetSales  
WHERE OrderDateKey > '20020801'  
GROUP BY OrderDateKey  
ORDER BY OrderDateKey;  
```  
  
### <a name="g-using-group-by-with-an-expression"></a>G. Utilisation de GROUP BY avec une expression  
 L'exemple suivant effectue un regroupement en fonction d'une expression. Vous pouvez spécifier un regroupement en fonction d'une expression à condition qu'elle ne contienne pas de fonction d'agrégation.  
  
```sql  
SELECT SUM(SalesAmount) AS TotalSales  
FROM FactInternetSales  
GROUP BY (OrderDateKey * 10);  
```  
  
### <a name="h-using-group-by-with-order-by"></a>H. Utilisation de GROUP BY avec ORDER BY  
 L’exemple suivant calcule la somme des ventes par jour et les commandes en fonction du jour.  
  
```sql  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales  
FROM FactInternetSales  
GROUP BY OrderDateKey  
ORDER BY OrderDateKey;  
```  
  
### <a name="i-using-the-having-clause"></a>I. Utilisation de la clause HAVING  
 Cette requête utilise le `HAVING` clause pour limiter les résultats.  
  
```sql  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales  
FROM FactInternetSales  
GROUP BY OrderDateKey  
HAVING OrderDateKey > 20010000  
ORDER BY OrderDateKey;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples SELECT &#40; Transact-SQL &#41;](../../t-sql/queries/select-examples-transact-sql.md)  
 [Indicateurs de &#40; Transact-SQL &#41;](../../t-sql/queries/hints-transact-sql.md)
  



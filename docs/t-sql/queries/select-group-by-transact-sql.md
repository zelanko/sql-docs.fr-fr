---
title: GROUP BY (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GROUP
- CUBE
- ROLLUP
- GROUPING_SETS_TSQL
- GROUP BY
- GROUPING SETS
- GROUP_BY_TSQL
- GROUP_TSQL
- CUBE_TSQL
- ROLLUP_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GROUP BY clause, about GROUP BY clause
- dividing tables into groups
- GROUPING SETS
- GROUP BY clause
- table groups [SQL Server]
- groups [SQL Server], tables divided into groups
- summary values [SQL Server]
ms.assetid: 40075914-6385-4692-b4a5-62fe44ae6cb6
caps.latest.revision: 80
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 01e2c02cade5b84f3560fe5cb415cece4f815abf
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="select---group-by--transact-sql"></a>Sélectionnez - GROUP - BY Transact-SQL
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Une clause de l’instruction SELECT qui divise le résultat de la requête en groupes de lignes, généralement afin d’exécuter une ou plusieurs agrégations sur chaque groupe. L’instruction SELECT renvoie une ligne par groupe.  
  
## <a name="syntax"></a>Syntaxe  

 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "icône lien de rubrique") [Conventions de syntaxe Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
```  
-- Syntax for SQL Server and Azure SQL Database   
-- ISO-Compliant Syntax  
  
GROUP BY {
      column-expression  
    | ROLLUP ( <group_by_expression> [ ,...n ] )  
    | CUBE ( <group_by_expression> [ ,...n ] )  
    | GROUPING SETS ( <grouping_set> [ ,...n ]  )  
    | () --calculates the grand total 
} [ ,...n ] 
 
<group_by_expression> ::=  
      column-expression  
    | ( column-expression [ ,...n ] )    
   
<grouping_set> ::=  
      () --calculates the grand total  
    | <grouping_set_item>  
    | ( <grouping_set_item> [ ,...n ] )  
  
<grouping_set_item> ::=  
      <group_by_expression>  
    | ROLLUP ( <group_by_expression> [ ,...n ] )  
    | CUBE ( <group_by_expression> [ ,...n ] )  
  

-- For backward compatibility only.
-- Non-ISO-Compliant Syntax for SQL Server and Azure SQL Database 
  
GROUP BY 
      [ ALL ] column-expression [ ,...n ] 
    | column-expression [ ,...n ] [ WITH { CUBE | ROLLUP } ]   

```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
GROUP BY {
      column-name [ WITH (DISTRIBUTED_AGG) ]  
    | column-expression
} [ ,...n ]

```  
  
## <a name="arguments"></a>Arguments 
 
### <a name="column-expression"></a>*expression de colonne*  
Spécifie une colonne ou un calcul non agrégées sur une colonne. Cette colonne peut appartenir à une table, une table dérivée ou une vue. La colonne doit apparaître dans la clause FROM de l’instruction SELECT, mais n’est pas nécessaire pour s’affichent dans la liste de sélection. 

Pour les expressions valides, consultez [expression](~/t-sql/language-elements/expressions-transact-sql.md).    

La colonne doit apparaître dans la clause FROM de l’instruction SELECT, mais n’est pas nécessaire pour s’affichent dans la liste de sélection. Toutefois, chaque table ou vue, colonne dans toute expression de non-agrégation le \<sélectionnez > liste doit être incluse dans la liste GROUP BY :  
  
Les instructions suivantes sont autorisées :  
  
    ```  
    SELECT ColumnA, ColumnB FROM T GROUP BY ColumnA, ColumnB;  
    SELECT ColumnA + ColumnB FROM T GROUP BY ColumnA, ColumnB;  
    SELECT ColumnA + ColumnB FROM T GROUP BY ColumnA + ColumnB;  
    SELECT ColumnA + ColumnB + constant FROM T GROUP BY ColumnA, ColumnB;  
    ```  
  
Les instructions suivantes ne sont pas autorisées :  
  
    ```  
    SELECT ColumnA, ColumnB FROM T GROUP BY ColumnA + ColumnB;  
    SELECT ColumnA + constant + ColumnB FROM T GROUP BY ColumnA + ColumnB;  
    ```  
L’expression de colonne ne peut pas contenir :

- Un alias de colonne défini dans la liste de sélection. Elle peut utiliser un alias de colonne pour une table dérivée qui est définie dans la clause FROM.
- Une colonne de type **texte**, **ntext**, ou **image**. Toutefois, vous pouvez utiliser une colonne de texte, ntext ou image en tant qu’argument à une fonction qui retourne une valeur d’un type de données valide. Par exemple, l’expression peut utiliser SUBSTRING() et CAST(). Cela s’applique également aux expressions dans la clause HAVING.
- méthodes de type de données XML. Il peut inclure une fonction définie par l’utilisateur qui utilise les méthodes de type de données xml. Il peut inclure une colonne calculée qui utilise les méthodes de type de données xml. 
- Une sous-requête. Erreur 144 est retournée. 
- Une colonne d’une vue indexée. 
 
### <a name="group-by-column-expression--n-"></a>GROUP BY *expression de colonne* [,.. .n] 

Regroupe les résultats de l’instruction SELECT en fonction des valeurs dans une liste d’une ou plusieurs expressions de colonne. 

Par exemple, cette requête crée une table de ventes avec des colonnes pour le pays, région et les ventes. Il insère les quatre lignes et deux lignes ont des valeurs correspondantes pour le pays et région.  

```
CREATE TABLE Sales ( Country varchar(50), Region varchar(50), Sales int );

INSERT INTO sales VALUES (N'Canada', N'Alberta', 100);
INSERT INTO sales VALUES (N'Canada', N'British Columbia', 200);
INSERT INTO sales VALUES (N'Canada', N'British Columbia', 300);
INSERT INTO sales VALUES (N'United States', N'Montana', 100);
```
La table Sales contient ces lignes :

| Pays | Région | Ventes |
|---------|--------|-------|
| Canada | Alberta | 100 |
| Canada | Colombie-britannique | 200 |
| Canada | Colombie-britannique | 300 |
| United States | Montana | 100 |

Cette requête suivante regroupe les pays et par région et retourne la somme agrégée pour chaque combinaison de valeurs.  
 
``` 
SELECT Country, Region, SUM(sales) AS TotalSales
FROM Sales
GROUP BY Country, Region;
```
Le résultat de la requête a 3 lignes, car il existe 3 combinaisons de valeurs pour le pays et par région. La TotalSales pour le Canada et la Colombie-britannique est la somme de deux lignes. 

| Pays | Région | TotalSales |
|---------|--------|-------|
| Canada | Alberta | 100 |
| Canada | Colombie-britannique | 500 |
| United States | Montana | 100 |

### <a name="group-by-rollup"></a>GROUP BY ROLLUP

Crée un groupe pour chaque combinaison d’expressions de colonne. En outre, il « reporté » les résultats dans les sous-totaux et les totaux généraux. Pour ce faire, il déplace de droite à gauche en diminuant le nombre d’expressions de colonne sur laquelle il crée des groupes de l’aggregation(s). 

L’ordre des colonnes affecte la sortie ROLLUP et peut affecter le nombre de lignes dans le jeu de résultats.  

Par exemple, `GROUP BY ROLLUP (col1, col2, col3, col4)` crée des groupes pour chaque combinaison d’expressions de colonne dans les listes suivantes.  

- col1, col2, col3, col4 
- col1, col2, col3, NULL
- col1, col2, NULL, NULL
- col1, NULL, NULL, NULL
- NULL, NULL, NULL, NULL--il s’agit du total général

À l’aide de la table à partir de l’exemple précédent, ce code s’exécute une opération GROUP BY ROLLUP au lieu d’une clause GROUP BY simple.

```
SELECT Country, Region, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY ROLLUP (Country, Region);
```

Le résultat de la requête a les agrégations de mêmes que la clause GROUP BY simple sans le cumul. En outre, il crée des sous-totaux pour chaque valeur du pays. Enfin, il donne un total général pour toutes les lignes. Le résultat ressemble à ceci :

| Pays | Région | TotalSales |
| :------ | :----- | ---------: |
| Canada | Alberta | 100 |
| Canada | Colombie-britannique | 500 |
| Canada | NULL | 600 |
| United States | Montana | 100 |
| United States | NULL | 100 |
| NULL | NULL | 700 |

### <a name="group-by-cube--"></a>GROUP BY (DE CUBE)  

GROUP BY CUBE crée des groupes pour toutes les combinaisons possibles de colonnes. Pour GROUP BY CUBE (a, b) les résultats possède des groupes de valeurs uniques (a, b), (NULL, b), (a, NULL) et (NULL, NULL).

À l’aide de la table dans les exemples précédents, ce code s’exécute une opération GROUP BY CUBE sur le pays et par région. 

```
SELECT Country, Region, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY CUBE (Country, Region);
```

Le résultat de requête possède des groupes de valeurs uniques de (Country, Region), (NULL, région), (pays, NULL) et (NULL, NULL). Les résultats se présenter comme suit :

| Pays | Région | TotalSales |
|---------|--------|-------|
| Canada | Alberta | 100 |
| NULL | Alberta | 100 |
| Canada | Colombie-britannique | 500 |
| NULL | Colombie-britannique | 500 |
| United States | Montana | 100 |
| NULL | Montana | 100 |
| NULL | NULL | 700
| Canada | NULL | 600 |
| United States | NULL | 100 |
   
 ### <a name="group-by-grouping-sets--"></a>GROUP BY () DES JEUX DE REGROUPEMENT  
 
L’option de GROUPING SETS vous donne la possibilité de combiner plusieurs clauses GROUP BY dans une clause GROUP BY. Les résultats sont l'équivalent de l'opération UNION ALL des groupes spécifiés. 

Par exemple, `GROUP BY ROLLUP (Country, Region)` et `GROUP BY GROUPING SETS ( ROLLUP (Country, Region) )` retournent les mêmes résultats. 

Lorsque les jeux de regroupement comporte deux ou plusieurs éléments, les résultats sont une union des éléments. Cet exemple retourne l’union des résultats ROLLUP et CUBE pour le pays et par région.

```
SELECT Country, Region, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY GROUPING SETS ( ROLLUP (Country, Region), CUBE (Country, Region) );
```

Les résultats sont les mêmes que cette requête qui retourne une union de deux instructions GROUP BY.

```
SELECT Country, Region, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY ROLLUP (Country, Region)
UNION ALL
SELECT Country, Region, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY CUBE (Country, Region)
;
```

SQL ne consolident pas les groupes en double générés pour une liste GROUPING SETS. Par exemple, dans `GROUP BY ( (), CUBE (Country, Region) )`, les deux éléments de retournent une ligne pour le total général et les deux lignes sont répertoriés dans les résultats. 

 ### <a name="group-by-"></a>GROUP BY ()  
Spécifie le groupe vide, ce qui génère le total général. Cela est utile en tant qu’un des éléments d’un jeu de regroupement. Par exemple, cette instruction donne le total des ventes pour chaque pays, puis donne le grand total pour tous les pays.

```
SELECT Country, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY GROUPING SETS ( Country, () );
```

### <a name="group-by--all--column-expression--n-"></a>GROUP BY [ALL]-expression de colonne [,.. .n] 

S’applique à : SQL Server et la base de données SQL Azure

Remarque : Cette syntaxe est fournie pour la compatibilité descendante uniquement. Il sera supprimé dans une future version. Évitez d’utiliser cette syntaxe dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette syntaxe.

Spécifie d’inclure tous les groupes dans les résultats qu’ils respectent les critères de recherche dans la clause WHERE. Les groupes qui ne répondent pas aux critères de recherche ont la valeur NULL pour l’agrégation. 

GROUPE PAR TOUTES LES :
- N’est pas pris en charge dans les requêtes qui accèdent aux tables distantes si une clause WHERE est également dans la requête.
- Échoue sur les colonnes qui ont l’attribut FILESTREAM.
  
### <a name="with-distributedagg"></a>AVEC (DISTRIBUTED_AGG)
S’applique à : Azure SQL Data Warehouse et Parallel Data Warehouse

L’indicateur de requête DISTRIBUTED_AGG force le système de traitement parallèle massif (MPP) afin de redistribuer une table sur une colonne spécifique avant d’effectuer une agrégation. Qu’une seule colonne dans la clause GROUP BY peut avoir un indicateur de requête DISTRIBUTED_AGG. Une fois que la requête est terminée, la table redistribuée est supprimée. La table d’origine n’est pas modifiée.  

Remarque : L’indicateur de requête DISTRIBUTED_AGG est fourni pour compatibilité descendante avec les versions antérieures de Parallel Data Warehouse et n’améliore pas les performances pour la plupart des requêtes. Par défaut, MPP redistribue déjà les données selon les besoins pour améliorer les performances pour les agrégations. 
  
## <a name="general-remarks"></a>Remarques d'ordre général

### <a name="how-group-by-interacts-with-the-select-statement"></a>GROUP BY interaction avec l’instruction SELECT
Liste de sélection :
- Agrégations vectorielles. Si les fonctions d’agrégation sont incluses dans la liste de sélection, GROUP BY calcule une valeur de synthèse pour chaque groupe. Ces expressions sont dites agrégations vectorielles. 
- Fonctions d’agrégation distinctes. Les fonctions d’agrégation AVG (DISTINCT *column_name*), COUNT (DISTINCT *column_name*) et SUM (DISTINCT *column_name*) sont pris en charge avec ROLLUP, CUBE et GROUPING SETS.
  
Clause WHERE :
- SQL supprime des lignes qui ne respectent pas les conditions dans la clause WHERE avant toute opération de regroupement.  
  
Clause HAVING :
- SQL utilise la clause pour filtrer des groupes dans le jeu de résultats. 
  
Clause ORDER BY :
- Utilisez la clause ORDER BY pour classer le jeu de résultats. La clause GROUP BY ne classe pas le jeu de résultats. 
  
Valeurs NULL :
- Si une colonne de regroupement contient des valeurs NULL, toutes les valeurs NULL sont considérées comme égales et ils sont collectés dans un seul groupe.   
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions

S’applique à : SQL Server (à partir de 2008) et Azure SQL Data Warehouse

### <a name="maximum-capacity"></a>Capacité maximale

Pour une clause GROUP BY qui utilise ROLLUP, CUBE ou GROUPING SETS, le nombre maximal d’expressions est 32. Le nombre maximal de groupes est 4096 (2<sup>12</sup>). Les exemples suivants échouent, car la clause GROUP BY compose plus de 4096 groupes.  
 
-   L’exemple suivant génère 4097 (2<sup>12</sup> + 1) jeux de regroupement et échoue.  
  
    ```  
    GROUP BY GROUPING SETS( CUBE(a1, ..., a12), b )  
    ```  
  
-   L’exemple suivant génère 4097 (2<sup>12</sup> + 1) regroupe et échoue. `CUBE ()` et le jeu de regroupement `()` produisent une ligne de total global et les jeux de regroupement en double ne sont pas éliminés.  
  
    ```  
    GROUP BY GROUPING SETS( CUBE(a1, ..., a12), ())  
    ```  

-   Cet exemple utilise la syntaxe à compatibilité descendante. Il génère 8192 (2<sup>13</sup>) jeux de regroupement et échoue.  
  
    ```  
    GROUP BY CUBE (a1, ..., a13)   
    GROUP BY a1, ..., a13 WITH CUBE   
    ```    
    Pour la compatibilité descendante avec clauses GROUP BY qui ne contiennent pas de CUBE ou ROLLUP, le nombre de regrouper des éléments est limité par les tailles de colonne GROUP BY, aux colonnes d’agrégation et les valeurs d’agrégation impliquées dans la requête. Cette limite provient de la limite de 8 060 octets de la table de travail intermédiaire requise pour stocker les résultats de requêtes intermédiaires. Un maximum de 12 expressions de regroupement est autorisé quand CUBE ou ROLLUP est spécifié.

### <a name="support-for-iso-and-ansi-sql-2006-group-by-features"></a>Prise en charge des fonctionnalités GROUP BY ISO et ANSI SQL-2006

La clause GROUP BY prend en charge toutes les fonctionnalités GROUP BY qui sont incluses dans la norme SQL-2006, avec les exceptions de syntaxe suivantes :  
  
-   Les jeux de regroupement ne sont pas autorisés dans la clause GROUP BY, à moins de faire partie d'une liste GROUPING SETS explicite. Par exemple, `GROUP BY Column1, (Column2, ...ColumnN`) est autorisé dans la norme, mais pas dans Transact-SQL.  Prend en charge de Transact-SQL `GROUP BY C1, GROUPING SETS ((Column2, ...ColumnN))` et `GROUP BY Column1, Column2, ... ColumnN`, qui sont sémantiquement équivalentes. Ils sont sémantiquement équivalents à l'exemple `GROUP BY` précédent. Il s’agit d’éviter le risque que `GROUP BY Column1, (Column2, ...ColumnN`) peut être interprété à tort comme `GROUP BY C1, GROUPING SETS ((Column2, ...ColumnN))`, qui ne sont pas sémantiquement équivalentes.  
  
-   Les jeux de regroupement ne sont pas autorisés à l'intérieur des jeux de regroupement. Par exemple, `GROUP BY GROUPING SETS (A1, A2,…An, GROUPING SETS (C1, C2, ...Cn))` est autorisé dans la norme SQL-2006, mais pas dans Transact-SQL. Transact-SQL permet `GROUP BY GROUPING SETS( A1, A2,...An, C1, C2, ...Cn )` ou `GROUP BY GROUPING SETS( (A1), (A2), ... (An), (C1), (C2), ... (Cn) )`, qui sont sémantiquement équivalent au premier exemple GROUP BY et ont une syntaxe plus claire.  
  
-   GROUP BY [ALL/DISTINCT] est uniquement autorisée dans une clause de GROUP BY de simple qui contient des expressions de colonne. Il n’est pas autorisée avec les constructions GROUPING SETS, ROLLUP, CUBE, WITH CUBE ou WITH ROLLUP. ALL est la valeur par défaut et est implicite. Il est uniquement autorisée dans la syntaxe à compatibilité descendante.
  
### <a name="comparison-of-supported-group-by-features"></a>Comparaison des fonctionnalités GROUP BY prises en charge  
 Le tableau suivant décrit les fonctionnalités GROUP BY sont pris en charge en fonction des versions de SQL et le niveau de compatibilité de base de données.  
  
|Fonctionnalité|SQL Server Integration Services|Niveau de compatibilité SQL Server 100 ou supérieur|SQL Server 2008 ou version ultérieure avec niveau de compatibilité 90.|  
|-------------|-------------------------------------|--------------------------------------------------|-----------------------------------------------------------|  
|Agrégats DISTINCT|Non pris en charge pour WITH CUBE ou WITH ROLLUP.|Pris en charge pour WITH CUBE, WITH ROLLUP, GROUPING SETS, CUBE ou ROLLUP.|Identique au niveau de comptabilité 100.|  
|Fonction définie par l'utilisateur avec nom CUBE ou ROLLUP dans la clause GROUP BY|Fonction définie par l’utilisateur **dbo.cube (***arg1***,***.. .argN***)** ou **dbo.rollup (***arg1***,**... *argN***)** dans la clause GROUP BY clause est autorisée.<br /><br /> Par exemple : `SELECT SUM (x) FROM T  GROUP BY dbo.cube(y);`|Fonction définie par l’utilisateur **dbo.cube (***arg1***,**.. .argN**)** ou **dbo.rollup (**arg1**,***.. .argN***)** dans la clause GROUP BY clause n’est pas autorisée.<br /><br /> Par exemple : `SELECT SUM (x) FROM T  GROUP BY dbo.cube(y);`<br /><br /> Le message d’erreur suivant est retourné : « syntaxe incorrecte près du cube' mot clé' &#124;' correctif cumulatif «. »<br /><br /> Pour éviter ce problème, remplacez `dbo.cube` par `[dbo].[cube]` ou `dbo.rollup` par `[dbo].[rollup]`.<br /><br /> L’exemple suivant est autorisé :`SELECT SUM (x) FROM T  GROUP BY [dbo].[cube](y);`|Fonction définie par l’utilisateur **dbo.cube (***arg1***,***.. .argN*) ou **dbo.rollup (***arg1***,***.. .argN***)** dans la clause GROUP BY clause est autorisée.<br /><br /> Par exemple : `SELECT SUM (x) FROM T  GROUP BY dbo.cube(y);`|  
|GROUPING SETS|Non pris en charge|Pris en charge|Pris en charge|  
|CUBE|Non pris en charge|Pris en charge|Non pris en charge|  
|ROLLUP|Non pris en charge|Pris en charge|Non pris en charge|  
|Total global, tel que GROUP BY ()|Non pris en charge|Pris en charge|Pris en charge|  
|GROUPING_ID, fonction|Non pris en charge|Pris en charge|Pris en charge|  
|GROUPING (fonction)|Pris en charge|Pris en charge|Pris en charge|  
|WITH CUBE|Pris en charge|Pris en charge|Pris en charge|  
|WITH ROLLUP|Pris en charge|Pris en charge|Pris en charge|  
|Suppression de regroupement WITH CUBE ou WITH ROLLUP « en double »|Pris en charge|Pris en charge|Pris en charge| 
 
  
## <a name="examples"></a>Exemples  
  
### <a name="a-use-a-simple-group-by-clause"></a>A. Utilisez une clause GROUP BY simple  
 L'exemple suivant extrait le total pour chaque `SalesOrderID` de la table `SalesOrderDetail`. Cet exemple utilise AdventureWorks.  
  
```  
SELECT SalesOrderID, SUM(LineTotal) AS SubTotal  
FROM Sales.SalesOrderDetail AS sod  
GROUP BY SalesOrderID  
ORDER BY SalesOrderID;  
```  
  
### <a name="b-use-a-group-by-clause-with-multiple-tables"></a>B. Utilisez une clause GROUP BY avec plusieurs tables  
 L'exemple suivant extrait le nombre d'employés pour chaque `City` de la table `Address` en conjonction avec la table `EmployeeAddress`. Cet exemple utilise AdventureWorks. 
  
```  
SELECT a.City, COUNT(bea.AddressID) EmployeeCount  
FROM Person.BusinessEntityAddress AS bea   
    INNER JOIN Person.Address AS a  
        ON bea.AddressID = a.AddressID  
GROUP BY a.City  
ORDER BY a.City;  
```  
  
### <a name="c-use-a-group-by-clause-with-an-expression"></a>C. Utiliser une clause GROUP BY avec une expression  
 L'exemple suivant récupère le total des ventes pour chaque année en utilisant la fonction `DATEPART`. La même expression doit être présente dans la liste `SELECT` et dans la clause `GROUP BY`.  
  
```  
SELECT DATEPART(yyyy,OrderDate) AS N'Year'  
    ,SUM(TotalDue) AS N'Total Order Amount'  
FROM Sales.SalesOrderHeader  
GROUP BY DATEPART(yyyy,OrderDate)  
ORDER BY DATEPART(yyyy,OrderDate);  
```  
  
### <a name="d-use-a-group-by-clause-with-a-having-clause"></a>D. Utilisez une clause GROUP BY avec une clause HAVING  
 L'exemple suivant utilise la clause `HAVING` pour spécifier lequel des groupes générés dans la clause `GROUP BY` doit être inclus dans le jeu de résultats.  
  
```  
SELECT DATEPART(yyyy,OrderDate) AS N'Year'  
    ,SUM(TotalDue) AS N'Total Order Amount'  
FROM Sales.SalesOrderHeader  
GROUP BY DATEPART(yyyy,OrderDate)  
HAVING DATEPART(yyyy,OrderDate) >= N'2003'  
ORDER BY DATEPART(yyyy,OrderDate);  
```  
  
## <a name="examples-sql-data-warehouse-and-parallel-data-warehouse"></a>Exemples : SQL Data Warehouse et Parallel Data Warehouse  
  
### <a name="e-basic-use-of-the-group-by-clause"></a>E. Utilisation de base de la clause GROUP BY  
 L’exemple suivant recherche la quantité totale de toutes les ventes chaque jour. Une ligne contenant la somme de toutes les ventes est retournée pour chaque jour.  
  
```  
-- Uses AdventureWorksDW  
  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales FROM FactInternetSales  
GROUP BY OrderDateKey ORDER BY OrderDateKey;  
```  
  
### <a name="f-basic-use-of-the-distributedagg-hint"></a>F. Utilisation de base de l’indicateur DISTRIBUTED_AGG  
 Cet exemple utilise l’indicateur de requête DISTRIBUTED_AGG pour forcer l’application de la réorganisation de la table sur la `CustomerKey` colonne avant d’effectuer l’agrégation.  
  
```  
-- Uses AdventureWorksDW  
  
SELECT CustomerKey, SUM(SalesAmount) AS sas  
FROM FactInternetSales  
GROUP BY CustomerKey WITH (DISTRIBUTED_AGG)  
ORDER BY CustomerKey DESC;  
```  
  
### <a name="g-syntax-variations-for-group-by"></a>G. Variantes de syntaxe pour grouper par  
 Lorsque la liste de sélection possède pas d’agrégations, chaque colonne dans la liste de sélection doit être inclus dans la liste GROUP BY. Les colonnes calculées dans la liste de sélection peuvent être répertoriés, mais ne sont pas requis, dans la liste GROUP BY. Voici des exemples d’instructions SELECT valides :  
  
```  
-- Uses AdventureWorks  
  
SELECT LastName, FirstName FROM DimCustomer GROUP BY LastName, FirstName;  
SELECT NumberCarsOwned FROM DimCustomer GROUP BY YearlyIncome, NumberCarsOwned;  
SELECT (SalesAmount + TaxAmt + Freight) AS TotalCost FROM FactInternetSales GROUP BY SalesAmount, TaxAmt, Freight;  
SELECT SalesAmount, SalesAmount*1.10 SalesTax FROM FactInternetSales GROUP BY SalesAmount;  
SELECT SalesAmount FROM FactInternetSales GROUP BY SalesAmount, SalesAmount*1.10;  
```  
  
### <a name="h-using-a-group-by-with-multiple-group-by-expressions"></a>H. À l’aide de GROUP BY avec plusieurs expressions GROUP BY  
 L’exemple suivant regroupe les résultats à l’aide de plusieurs `GROUP BY` critères. If, dans chaque `OrderDateKey` groupe, il existe des sous-groupes peuvent être différenciés par `DueDateKey`, un nouveau regroupement sera défini pour le jeu de résultats.  
  
```  
-- Uses AdventureWorks  
  
SELECT OrderDateKey, DueDateKey, SUM(SalesAmount) AS TotalSales   
FROM FactInternetSalesGROUP BY OrderDateKey, DueDateKey   
ORDER BY OrderDateKey;  
```  
  
### <a name="i-using-a-group-by-clause-with-a-having-clause"></a>I. Utilisation d'une clause GROUP BY avec une clause HAVING  
 L’exemple suivant utilise le `HAVING` clause pour spécifier des groupes générés dans le `GROUP BY` clause qui doit être inclus dans le jeu de résultats. Uniquement les groupes avec des dates de commande dans 2004 ou version ultérieure seront inclus dans les résultats.  
  
```  
-- Uses AdventureWorks  
  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales   
FROM FactInternetSales  
GROUP BY OrderDateKey   
HAVING OrderDateKey > 20040000   
ORDER BY OrderDateKey;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [GROUPING_ID &#40; Transact-SQL &#41;](~/t-sql/functions/grouping-id-transact-sql.md)   
 [REGROUPEMENT &#40; Transact-SQL &#41;](~/t-sql/functions/grouping-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](~/t-sql/queries/select-transact-sql.md)   
 [Clause SELECT &#40; Transact-SQL &#41;](~/t-sql/queries/select-clause-transact-sql.md)  
  
  






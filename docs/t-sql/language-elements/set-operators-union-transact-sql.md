---
title: UNION (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- UNION
- UNION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- UNION queries
- combining query results
- UNION operator [SQL Server]
ms.assetid: 607c296f-8a6a-49bc-975a-b8d0c0914df7
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 7c71b2eae1c0c3e55d09cdc5af2dfd7740df143f
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="set-operators---union-transact-sql"></a>Définir des opérateurs - UNION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Associe les résultats de plusieurs requêtes en un seul jeu de résultats qui inclut toutes les lignes appartenant aux requêtes de l'union. Cette opération diffère de l'utilisation des jointures combinant les colonnes des deux tables.  
  
 Voici les règles de base pour combiner les jeux de résultats de deux requêtes à l'aide de la procédure UNION :  
  
-   Le nombre et l'ordre des colonnes doivent être identiques dans toutes les requêtes.  
  
-   Les types de données doivent être compatibles.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
    { <query_specification> | ( <query_expression> ) }   
  UNION [ ALL ]   
  <query_specification | ( <query_expression> )   
 [ UNION [ ALL ] <query_specification> | ( <query_expression> )   
    [ ...n ] ]   
```  
  
## <a name="arguments"></a>Arguments  
\<query_specification > | ( \<query_expression >) est une spécification de requête ou une expression de requête qui retourne des données à combiner avec les données à partir d’une autre requête spécification ou expression de requête. Les définitions des colonnes faisant partie d'une opération UNION ne doivent pas forcément être identiques, mais elles doivent être compatibles via une conversion implicite. Lorsque les types de données diffèrent, le type de données est déterminé selon les règles pour [priorité des types de données](../../t-sql/data-types/data-type-precedence-transact-sql.md). Si les types sont les mêmes mais diffèrent en terme de précision, d'échelle ou de longueur, le résultat se détermine d'après les mêmes règles de combinaison d'expressions. Pour plus d’informations, consultez [Précision, échelle et longueur &#40;Transact-SQL&#41;](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
 Colonnes de la **xml** type de données doit être équivalent. Toutes les colonnes doivent être typées selon un schéma XML ou être non typées. Si elles sont typées, elles doivent l'être par rapport à la même collection de schémas XML.  
  
 UNION  
 Indique que les jeux de résultats multiples doivent être associés et retournés dans un seul jeu de résultats.  
  
 ALL  
 Incorpore toutes les lignes dans les résultats, y compris les doublons. S'il n'est pas spécifié, tous les doublons de lignes sont supprimés.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-a-simple-union"></a>A. Utilisation de l'opérateur UNION simple  
 Dans l'exemple suivant, le jeu de résultats comprend le contenu des colonnes `ProductModelID` et `Name` des deux tables `ProductModel` et `Gloves`.  
  
```  
-- Uses AdventureWorks  
  
IF OBJECT_ID ('dbo.Gloves', 'U') IS NOT NULL  
DROP TABLE dbo.Gloves;  
GO  
-- Create Gloves table.  
SELECT ProductModelID, Name  
INTO dbo.Gloves  
FROM Production.ProductModel  
WHERE ProductModelID IN (3, 4);  
GO  
  
-- Here is the simple union.  
-- Uses AdventureWorks  
  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID NOT IN (3, 4)  
UNION  
SELECT ProductModelID, Name  
FROM dbo.Gloves  
ORDER BY Name;  
GO  
```  
  
### <a name="b-using-select-into-with-union"></a>B. Utilisation de SELECT INTO avec UNION  
 Dans l'exemple suivant, la clause `INTO` de la seconde instruction `SELECT` indique que la table nommée `ProductResults` contient le jeu de résultats final de l'union des colonnes désignées des tables `ProductModel` et `Gloves`. Notez que la table `Gloves` est créée dans la première instruction `SELECT`.  
  
```  
-- Uses AdventureWorks  
  
IF OBJECT_ID ('dbo.ProductResults', 'U') IS NOT NULL  
DROP TABLE dbo.ProductResults;  
GO  
IF OBJECT_ID ('dbo.Gloves', 'U') IS NOT NULL  
DROP TABLE dbo.Gloves;  
GO  
-- Create Gloves table.  
SELECT ProductModelID, Name  
INTO dbo.Gloves  
FROM Production.ProductModel  
WHERE ProductModelID IN (3, 4);  
GO  
  
-- Uses AdventureWorks  
  
SELECT ProductModelID, Name  
INTO dbo.ProductResults  
FROM Production.ProductModel  
WHERE ProductModelID NOT IN (3, 4)  
UNION  
SELECT ProductModelID, Name  
FROM dbo.Gloves;  
GO  
  
SELECT ProductModelID, Name   
FROM dbo.ProductResults;  
  
```  
  
### <a name="c-using-union-of-two-select-statements-with-order-by"></a>C. Utilisation de l'opérateur UNION dans deux instructions SELECT avec ORDER BY  
 L'ordre de certains paramètres utilisés avec la clause UNION est important. L'exemple suivant illustre l'utilisation incorrecte et correcte de `UNION` dans deux instructions `SELECT` où une colonne doit être renommée dans le résultat.  
  
```  
-- Uses AdventureWorks  
  
IF OBJECT_ID ('dbo.Gloves', 'U') IS NOT NULL  
DROP TABLE dbo.Gloves;  
GO  
-- Create Gloves table.  
SELECT ProductModelID, Name  
INTO dbo.Gloves  
FROM Production.ProductModel  
WHERE ProductModelID IN (3, 4);  
GO  
  
/* INCORRECT */  
-- Uses AdventureWorks  
  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID NOT IN (3, 4)  
ORDER BY Name  
UNION  
SELECT ProductModelID, Name  
FROM dbo.Gloves;  
GO  
  
/* CORRECT */  
-- Uses AdventureWorks  
  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID NOT IN (3, 4)  
UNION  
SELECT ProductModelID, Name  
FROM dbo.Gloves  
ORDER BY Name;  
GO  
  
```  
  
### <a name="d-using-union-of-three-select-statements-to-show-the-effects-of-all-and-parentheses"></a>D. Utilisation de l'opérateur UNION dans trois instructions SELECT pour illustrer les effets de ALL et des parenthèses  
 Les exemples suivants utilisent `UNION` pour combiner les résultats de trois tables, ayant chacune les 5 lignes de données identiques. Le premier exemple utilise `UNION ALL` pour montrer les doublons d'enregistrement et retourne l'ensemble des 15 lignes. Le deuxième exemple utilise `UNION` sans `ALL` pour éliminer les doublons de ligne des résultats combinés des trois instructions `SELECT` et retourne 5 lignes.  
  
 Le troisième exemple utilise `ALL` avec la première clause `UNION` et met entre parenthèses la seconde clause `UNION` qui n'utilise pas `ALL`. La seconde clause `UNION` est traitée en premier, car elle est entre parenthèses. Elle retourne 5 lignes car l'option `ALL` n'est pas utilisée et les doublons sont supprimés. Ces 5 lignes sont combinées avec les résultats de la première instruction `SELECT` à l'aide des mots clés `UNION ALL`. Cela ne supprime pas les doublons entre les deux ensembles de 5 lignes. Le résultat final contient 10 lignes.  
  
```  
-- Uses AdventureWorks  
  
IF OBJECT_ID ('dbo.EmployeeOne', 'U') IS NOT NULL  
DROP TABLE dbo.EmployeeOne;  
GO  
IF OBJECT_ID ('dbo.EmployeeTwo', 'U') IS NOT NULL  
DROP TABLE dbo.EmployeeTwo;  
GO  
IF OBJECT_ID ('dbo.EmployeeThree', 'U') IS NOT NULL  
DROP TABLE dbo.EmployeeThree;  
GO  
  
SELECT pp.LastName, pp.FirstName, e.JobTitle   
INTO dbo.EmployeeOne  
FROM Person.Person AS pp JOIN HumanResources.Employee AS e  
ON e.BusinessEntityID = pp.BusinessEntityID  
WHERE LastName = 'Johnson';  
GO  
SELECT pp.LastName, pp.FirstName, e.JobTitle   
INTO dbo.EmployeeTwo  
FROM Person.Person AS pp JOIN HumanResources.Employee AS e  
ON e.BusinessEntityID = pp.BusinessEntityID  
WHERE LastName = 'Johnson';  
GO  
SELECT pp.LastName, pp.FirstName, e.JobTitle   
INTO dbo.EmployeeThree  
FROM Person.Person AS pp JOIN HumanResources.Employee AS e  
ON e.BusinessEntityID = pp.BusinessEntityID  
WHERE LastName = 'Johnson';  
GO  
-- Union ALL  
SELECT LastName, FirstName, JobTitle  
FROM dbo.EmployeeOne  
UNION ALL  
SELECT LastName, FirstName ,JobTitle  
FROM dbo.EmployeeTwo  
UNION ALL  
SELECT LastName, FirstName,JobTitle   
FROM dbo.EmployeeThree;  
GO  
  
SELECT LastName, FirstName,JobTitle  
FROM dbo.EmployeeOne  
UNION   
SELECT LastName, FirstName, JobTitle   
FROM dbo.EmployeeTwo  
UNION   
SELECT LastName, FirstName, JobTitle   
FROM dbo.EmployeeThree;  
GO  
  
SELECT LastName, FirstName,JobTitle   
FROM dbo.EmployeeOne  
UNION ALL  
(  
SELECT LastName, FirstName, JobTitle   
FROM dbo.EmployeeTwo  
UNION  
SELECT LastName, FirstName, JobTitle   
FROM dbo.EmployeeThree  
);  
GO  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-a-simple-union"></a>E. Utilisation de l'opérateur UNION simple  
 Dans l’exemple suivant, le jeu de résultats inclut le contenu de la `CustomerKey` des deux colonnes de la `FactInternetSales` et `DimCustomer` tables. Étant donné que le mot clé ALL n’est pas utilisée, les doublons sont exclues des résultats.  
  
```  
-- Uses AdventureWorks  
  
SELECT CustomerKey   
FROM FactInternetSales    
UNION   
SELECT CustomerKey   
FROM DimCustomer   
ORDER BY CustomerKey;  
```  
  
### <a name="f-using-union-of-two-select-statements-with-order-by"></a>F. Utilisation de l'opérateur UNION dans deux instructions SELECT avec ORDER BY  
 Lorsqu’une instruction SELECT dans une instruction UNION comprend une clause ORDER BY, cette clause doit être placée après toutes les instructions SELECT. L’exemple suivant montre l’utilisation incorrecte et correcte de `UNION` dans deux `SELECT` instructions dans laquelle une colonne est triée avec ORDER BY.  
  
```  
-- Uses AdventureWorks  
  
-- INCORRECT  
SELECT CustomerKey   
FROM FactInternetSales    
ORDER BY CustomerKey  
UNION   
SELECT CustomerKey   
FROM DimCustomer  
ORDER BY CustomerKey;  
  
-- CORRECT   
USE AdventureWorksPDW2012;  
  
SELECT CustomerKey   
FROM FactInternetSales    
UNION   
SELECT CustomerKey   
FROM DimCustomer   
ORDER BY CustomerKey;  
```  
  
### <a name="g-using-union-of-two-select-statements-with-where-and-order-by"></a>G. À l’aide de l’UNION de deux instructions SELECT avec WHERE et ORDER BY  
 L’exemple suivant montre l’utilisation incorrecte et correcte de `UNION` dans deux `SELECT` instructions où où et ORDER BY sont nécessaires.  
  
```  
-- Uses AdventureWorks  
  
-- INCORRECT   
SELECT CustomerKey   
FROM FactInternetSales   
WHERE CustomerKey >= 11000  
ORDER BY CustomerKey   
UNION   
SELECT CustomerKey   
FROM DimCustomer   
ORDER BY CustomerKey;  
  
-- CORRECT  
USE AdventureWorksPDW2012;  
  
SELECT CustomerKey   
FROM FactInternetSales   
WHERE CustomerKey >= 11000  
UNION   
SELECT CustomerKey   
FROM DimCustomer   
ORDER BY CustomerKey;  
```  
  
### <a name="h-using-union-of-three-select-statements-to-show-effects-of-all-and-parentheses"></a>H. À l’aide de l’UNION de trois instructions SELECT pour afficher les effets de ALL et des parenthèses  
 Les exemples suivants utilisent `UNION` pour combiner les résultats de **la même table** afin d’illustrer les effets de ALL et des parenthèses lorsque vous utilisez `UNION`.  
  
 Le premier exemple utilise `UNION ALL` à afficher en double enregistrements et renvoie chaque ligne dans la table source trois fois. Le deuxième exemple utilise `UNION` sans `ALL` pour éliminer les doublons de lignes à partir des résultats combinés des trois `SELECT` instructions et retourne uniquement les lignes reliés à partir de la table source.  
  
 Le troisième exemple utilise `ALL` avec la première `UNION` et les parenthèses entourant la seconde `UNION` qui n’utilise pas `ALL`. La seconde `UNION` est traitée en premier, car elle est entre parenthèses. Il retourne uniquement les lignes reliés à partir de la table, car la `ALL` option n’est pas utilisée et les doublons sont supprimés. Ces lignes sont combinées avec les résultats de la première `SELECT` à l’aide de la `UNION ALL` mots clés. Cela ne supprime pas les doublons entre les deux ensembles.  
  
```  
-- Uses AdventureWorks  
  
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION ALL   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION ALL   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer;  
  
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer;  
  
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION ALL  
(  
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [SELECT Examples &#40;Transact-SQL&#41;](../../t-sql/queries/select-examples-transact-sql.md)  
  
  


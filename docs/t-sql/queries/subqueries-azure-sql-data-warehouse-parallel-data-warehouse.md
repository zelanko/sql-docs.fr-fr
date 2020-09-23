---
title: Sous-requêtes
description: Sous-requêtes dans Azure SQL Data Warehouse et Parallel Data Warehouse
ms.custom: seo-lt-2019
titleSuffix: Azure SQL Data Warehouse
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
ms.assetid: 0e8ebd60-1936-48c9-b2b9-e099c8269fcf
author: shkale-msft
ms.author: shkale
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 946a36987b72f145af5e9c34eecaed9e8853033c
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91115422"
---
# <a name="subqueries-azure-sql-data-warehouse-parallel-data-warehouse"></a>Sous-requêtes (Azure SQL Data Warehouse, Parallel Data Warehouse)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Cette rubrique fournit des exemples d’utilisation des sous-requêtes dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
 Pour l’instruction SELECT, consultez [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)  
  
## <a name="contents"></a>Contents  
  
-   [Concepts de base](#Basics)  
  
-   [Exemples : SQL Data Warehouse et Parallel Data Warehouse](#Examples)  
  
##  <a name="basics"></a><a name="Basics"></a> Principes de base  
 Sous-requête  
 Une sous-requête est une requête qui est imbriquée dans une instruction SELECT, INSERT, UPDATE ou DELETE, ou dans une autre sous-requête. Elle est également désignée sous le nom de requête interne ou sélection interne.  
  
 Requête externe  
 Instruction contenant la sous-requête. Elle est également appelée sélection externe.  
  
 Sous-requête corrélée  
 Sous-requête qui fait référence à une table dans la requête externe.  
  
##  <a name="examples-sssdw-and-sspdw"></a><a name="Examples"></a> Exemples : [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Cette section fournit des exemples de sous-requêtes prises en charge dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
### <a name="a-top-and-order-by-in-a-subquery"></a>R. TOP et ORDER BY dans une sous-requête  
  
```sql
SELECT * FROM tblA  
WHERE col1 IN  
    (SELECT TOP 100 col1 FROM tblB ORDER BY col1);
```  
  
### <a name="b-having-clause-with-a-correlated-subquery"></a>B. Clause HAVING avec une sous-requête corrélée  
  
```sql
SELECT dm.EmployeeKey, dm.FirstName, dm.LastName   
FROM DimEmployee AS dm   
GROUP BY dm.EmployeeKey, dm.FirstName, dm.LastName  
HAVING 5000 <=   
(SELECT sum(OrderQuantity)  
FROM FactResellerSales AS frs  
WHERE dm.EmployeeKey = frs.EmployeeKey)  
ORDER BY EmployeeKey;
```  
  
### <a name="c-correlated-subqueries-with-analytics"></a>C. Sous-requêtes corrélées avec analytique  
  
```sql
SELECT * FROM ReplA AS A   
WHERE A.ID IN   
    (SELECT sum(B.ID2) OVER() FROM ReplB AS B WHERE A.ID2 = B.ID);  
```  
  
### <a name="d-correlated-union-statements-in-a-subquery"></a>D. Instructions d’union corrélées dans une sous-requête  
  
```sql
SELECT * FROM RA   
WHERE EXISTS   
    (SELECT 1 FROM RB WHERE RB.b1 = RA.a1   
     UNION ALL SELECT 1 FROM RC);  
```  
  
### <a name="e-join-predicates-in-a-subquery"></a>E. Prédicats de jointure dans une sous-requête  
  
```sql
SELECT * FROM RA INNER JOIN RB   
    ON RA.a1 = (SELECT COUNT(*) FROM RC);  
```  
  
### <a name="f-correlated-join-predicates-in-a-subquery"></a>F. Prédicats de jointure corrélés dans une sous-requête  
  
```sql
SELECT * FROM RA   
    WHERE RA.a2 IN   
    (SELECT 1 FROM RB INNER JOIN RC ON RA.a1=RB.b1+RC.c1);  
```  
  
### <a name="g-correlated-subselects-as-data-sources"></a>G. Sous-sélections corrélées comme sources de données  
  
```sql
SELECT * FROM RA   
    WHERE 3 = (SELECT COUNT(*)   
        FROM (SELECT b1 FROM RB WHERE RB.b1 = RA.a1) X);  
```  
  
### <a name="h-correlated-subqueries-in-the-data-values--used-with-aggregates"></a>H. Sous-requêtes corrélées dans les valeurs de données utilisées avec des agrégats  
  
```sql
SELECT Rb.b1, (SELECT RA.a1 FROM RA WHERE RB.b1 = RA.a1) FROM RB GROUP BY RB.b1;  
```  
  
### <a name="i-using-in-with-a-correlated-subquery"></a>I. Utilisation du mot clé IN avec une sous-requête corrélée  
 L'exemple suivant utilise `IN` dans une sous-requête en corrélation ou répétitive. Il s'agit d'une requête dont les valeurs dépendent de la requête externe. La requête interne est exécutée de manière répétitive, à raison d’une fois par ligne sélectionnable par la requête externe. Cette requête récupère une instance de `EmployeeKey` plus le prénom et le nom de chaque employé pour lequel la valeur `OrderQuantity` dans la table `FactResellerSales` est égale à `5` et dont le numéro d’identification d’employé figure dans les tables `DimEmployee` et `FactResellerSales`.  
  
```sql
SELECT DISTINCT dm.EmployeeKey, dm.FirstName, dm.LastName   
FROM DimEmployee AS dm   
WHERE 5 IN   
    (SELECT OrderQuantity  
    FROM FactResellerSales AS frs  
    WHERE dm.EmployeeKey = frs.EmployeeKey)  
ORDER BY EmployeeKey;  
```  
  
### <a name="j-using-exists-versus-in-with-a-subquery"></a>J. Utilisation du mot clé EXISTS ou IN dans une sous-requête  
 Les exemples suivants montrent des requêtes sémantiquement équivalentes pour illustrer la différence entre l’utilisation du mot clé `EXISTS` et celle du mot clé `IN`. Ces deux exemples de sous-requête récupèrent une instance de chaque nom de produit pour lequel la sous-catégorie de produit est `Road Bikes`. La sous-catégorie `ProductSubcategoryKey` figure dans les tables `DimProduct` et `DimProductSubcategory`.  
  
```sql
SELECT DISTINCT EnglishProductName  
FROM DimProduct AS dp   
WHERE EXISTS  
    (SELECT *  
     FROM DimProductSubcategory AS dps   
     WHERE dp.ProductSubcategoryKey = dps.ProductSubcategoryKey  
           AND dps.EnglishProductSubcategoryName = 'Road Bikes')  
ORDER BY EnglishProductName;  
```  
  
 ou  
  
```sql
SELECT DISTINCT EnglishProductName  
FROM DimProduct AS dp   
WHERE dp.ProductSubcategoryKey IN  
    (SELECT ProductSubcategoryKey  
     FROM DimProductSubcategory   
     WHERE EnglishProductSubcategoryName = 'Road Bikes')  
ORDER BY EnglishProductName;  
```  
  
### <a name="k-using-multiple-correlated-subqueries"></a>K. Utilisation de sous-requêtes corrélées multiples  
 Cet exemple utilise deux sous-requêtes corrélées pour rechercher les noms des employés ayant vendu un produit spécifique.  
  
```sql
SELECT DISTINCT LastName, FirstName, e.EmployeeKey  
FROM DimEmployee e JOIN FactResellerSales s ON e.EmployeeKey = s.EmployeeKey  
WHERE ProductKey IN  
(SELECT ProductKey FROM DimProduct WHERE ProductSubcategoryKey IN  
(SELECT ProductSubcategoryKey FROM DimProductSubcategory   
 WHERE EnglishProductSubcategoryName LIKE '%Bikes'))  
ORDER BY LastName;  
```  
  
  

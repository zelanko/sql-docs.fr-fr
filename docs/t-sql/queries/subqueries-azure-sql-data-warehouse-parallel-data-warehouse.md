---
title: "Les sous-requêtes (entrepôt de données SQL Azure, Parallel Data Warehouse) | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e8ebd60-1936-48c9-b2b9-e099c8269fcf
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 351d559bde6300d9f746d68a802ae0a61202f8b8
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="subqueries-azure-sql-data-warehouse-parallel-data-warehouse"></a>Sous-requêtes (entrepôt de données SQL Azure, entrepôt de données en parallèle)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Cette rubrique fournit des exemples d’utilisation de sous-requêtes dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
 Pour l’instruction SELECT, consultez [SELECT &#40; Transact-SQL &#41;](../../t-sql/queries/select-transact-sql.md)  
  
## <a name="contents"></a>Sommaire  
  
-   [Principes de base](#Basics)  
  
-   [Exemples : SQL Data Warehouse et Parallel Data Warehouse](#Examples)  
  
##  <a name="Basics"></a>Principes de base  
 Sous-requête  
 Une sous-requête est une requête qui est imbriquée dans une instruction SELECT, INSERT, UPDATE ou DELETE, ou dans une autre sous-requête. Cela est également appelé une sélection interne ou une requête interne.  
  
 Requête externe  
 L’instruction qui contient la sous-requête. Cela est également appelé une sélection externe.  
  
 Sous-requête corrélée  
 Une sous-requête qui fait référence à une table dans la requête externe.  
  
##  <a name="Examples"></a>Exemples : [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Cette section fournit des exemples de prise en charge dans des sous-requêtes [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
### <a name="a-top-and-order-by-in-a-subquery"></a>A. TOP et ORDER BY dans une sous-requête  
  
```  
SELECT * FROM tblA  
WHERE col1 IN  
    (SELECT TOP 100 col1 FROM tblB ORDER BY col1);  
  
```  
  
### <a name="b-having-clause-with-a-correlated-subquery"></a>B. HAVING (clause) avec une sous-requête corrélée  
  
```  
SELECT dm.EmployeeKey, dm.FirstName, dm.LastName   
FROM DimEmployee AS dm   
GROUP BY dm.EmployeeKey, dm.FirstName, dm.LastName  
HAVING 5000 <=   
(SELECT sum(OrderQuantity)  
FROM FactResellerSales AS frs  
WHERE dm.EmployeeKey = frs.EmployeeKey)  
ORDER BY EmployeeKey;  
  
```  
  
### <a name="c-correlated-subqueries-with-analytics"></a>C. Sous-requêtes en corrélation et analytique  
  
```  
SELECT * FROM ReplA AS A   
WHERE A.ID IN   
    (SELECT sum(B.ID2) OVER() FROM ReplB AS B WHERE A.ID2 = B.ID);  
```  
  
### <a name="d-correlated-union-statements-in-a-subquery"></a>D. Instructions corrélées unions dans une sous-requête  
  
```  
SELECT * FROM RA   
WHERE EXISTS   
    (SELECT 1 FROM RB WHERE RB.b1 = RA.a1   
     UNION ALL SELECT 1 FROM RC);  
```  
  
### <a name="e-join-predicates-in-a-subquery"></a>E. Joindre des prédicats dans une sous-requête  
  
```  
SELECT * FROM RA INNER JOIN RB   
    ON RA.a1 = (SELECT COUNT(*) FROM RC);  
```  
  
### <a name="f-correlated-join-predicates-in-a-subquery"></a>F. Prédicats de jointure en corrélation dans une sous-requête  
  
```  
SELECT * FROM RA   
    WHERE RA.a2 IN   
    (SELECT 1 FROM RB INNER JOIN RC ON RA.a1=RB.b1+RC.c1);  
```  
  
### <a name="g-correlated-subselects-as-data-sources"></a>G. Instructions de sous-sélection corrélées comme sources de données  
  
```  
SELECT * FROM RA   
    WHERE 3 = (SELECT COUNT(*)   
        FROM (SELECT b1 FROM RB WHERE RB.b1 = RA.a1) X);  
```  
  
### <a name="h-correlated-subqueries-in-the-data-values--used-with-aggregates"></a>H. Sous-requêtes en corrélation dans les valeurs de données utilisées avec les agrégats  
  
```  
SELECT Rb.b1, (SELECT RA.a1 FROM RA WHERE RB.b1 = RA.a1) FROM RB GROUP BY RB.b1;  
```  
  
### <a name="i-using-in-with-a-correlated-subquery"></a>I. À l’aide d’in avec une sous-requête corrélée  
 L'exemple suivant utilise `IN` dans une sous-requête en corrélation ou répétitive. Il s'agit d'une requête dont les valeurs dépendent de la requête externe. La requête interne est exécutée à plusieurs reprises, une fois pour chaque ligne qui peut être sélectionné par la requête externe. Cette requête extrait une instance de la `EmployeeKey` ainsi que le prénom et le nom de chaque employé pour lequel la `OrderQuantity` dans les `FactResellerSales` table est `5` et pour lequel les numéros d’identification d’employé correspondent dans le `DimEmployee` et `FactResellerSales` tables.  
  
```  
SELECT DISTINCT dm.EmployeeKey, dm.FirstName, dm.LastName   
FROM DimEmployee AS dm   
WHERE 5 IN   
    (SELECT OrderQuantity  
    FROM FactResellerSales AS frs  
    WHERE dm.EmployeeKey = frs.EmployeeKey)  
ORDER BY EmployeeKey;  
```  
  
### <a name="j-using-exists-versus-in-with-a-subquery"></a>J. À l’aide de EXISTS et in avec une sous-requête  
 L’exemple suivant montre des requêtes sémantiquement équivalentes pour illustrer la différence entre l’utilisation de la `EXISTS` (mot clé) et le `IN` (mot clé). Les deux sont des exemples d’une sous-requête qui Récupère une instance de chaque nom de produit pour lequel la sous-catégorie de produit est `Road Bikes`. `ProductSubcategoryKey`correspond entre le `DimProduct` et `DimProductSubcategory` tables.  
  
```  
SELECT DISTINCT EnglishProductName  
FROM DimProduct AS dp   
WHERE EXISTS  
    (SELECT *  
     FROM DimProductSubcategory AS dps   
     WHERE dp.ProductSubcategoryKey = dps.ProductSubcategoryKey  
           AND dps.EnglishProductSubcategoryName = 'Road Bikes')  
ORDER BY EnglishProductName;  
```  
  
 Ou  
  
```  
SELECT DISTINCT EnglishProductName  
FROM DimProduct AS dp   
WHERE dp.ProductSubcategoryKey IN  
    (SELECT ProductSubcategoryKey  
     FROM DimProductSubcategory   
     WHERE EnglishProductSubcategoryName = 'Road Bikes')  
ORDER BY EnglishProductName;  
```  
  
### <a name="k-using-multiple-correlated-subqueries"></a>K. Utilisation de plusieurs sous-requêtes corrélées  
 Cet exemple utilise deux sous-requêtes corrélées pour rechercher les noms des employés ayant vendu un produit spécifique.  
  
```  
SELECT DISTINCT LastName, FirstName, e.EmployeeKey  
FROM DimEmployee e JOIN FactResellerSales s ON e.EmployeeKey = s.EmployeeKey  
WHERE ProductKey IN  
(SELECT ProductKey FROM DimProduct WHERE ProductSubcategoryKey IN  
(SELECT ProductSubcategoryKey FROM DimProductSubcategory   
 WHERE EnglishProductSubcategoryName LIKE '%Bikes'))  
ORDER BY LastName  
;  
  
```  
  
  


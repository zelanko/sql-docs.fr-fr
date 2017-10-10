---
title: NOMBRE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COUNT_TSQL
- COUNT
dev_langs:
- TSQL
helpviewer_keywords:
- totals [SQL Server], COUNT function
- totals [SQL Server]
- counting items in group
- groups [SQL Server], number of items in
- number of group items
- COUNT function [Transact-SQL]
ms.assetid: 28d39da6-bc2e-46c7-858c-b1721c938830
caps.latest.revision: 45
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 80c1228faeaaa4012afc0fd27992a2f5cf389f6e
ms.openlocfilehash: e2d11d2cc57d275e952ff371ddf99c34dcae323d
ms.contentlocale: fr-fr
ms.lasthandoff: 10/05/2017

---
# <a name="count-transact-sql"></a>COUNT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Retourne le nombre d'éléments figurant dans un groupe. COUNT fonctionne comme le [COUNT_BIG](../../t-sql/functions/count-big-transact-sql.md) (fonction). Elles diffèrent uniquement au niveau des valeurs renvoyées : COUNT renvoie toujours une **int** valeur de type de données. COUNT_BIG retourne toujours un **bigint** valeur de type de données.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
-- Syntax for SQL Server and Azure SQL Database  
  
COUNT ( { [ [ ALL | DISTINCT ] expression ] | * } )   
    [ OVER (   
        [ partition_by_clause ]   
        [ order_by_clause ]   
        [ ROW_or_RANGE_clause ]  
    ) ]  
```  
  
```sql
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
-- Aggregation Function Syntax  
COUNT ( { [ [ ALL | DISTINCT ] expression ] | * } )  

-- Analytic Function Syntax  
COUNT ( { expression | * } ) OVER ( [ <partition_by_clause> ] )  
```  
  
## <a name="arguments"></a>Arguments  
**ALL**  
Applique la fonction d'agrégation à toutes les valeurs. ALL est l'argument par défaut.
  
DISTINCT  
Précise que la fonction COUNT doit renvoyer le nombre de valeurs non nulles uniques.
  
*expression*  
Est un [expression](../../t-sql/language-elements/expressions-transact-sql.md) de n’importe quel type sauf **texte**, **image**, ou **ntext**. Les fonctions d'agrégation et les sous-requêtes ne sont pas autorisées.
  
\*  
Spécifie que toutes les lignes doivent être comptées pour renvoyer le nombre total de lignes de la table. NOMBRE (\*) ne prend aucun paramètre et ne peut pas être utilisé avec DISTINCT. NOMBRE (\*) ne nécessite pas une *expression* paramètre car, par définition, elle n’utilise pas d’informations sur une colonne particulière. COUNT(*) calcule le nombre de lignes de la table spécifiée sans supprimer les doublons. Il compte chaque ligne séparément, y compris les lignes qui contiennent des valeurs NULL.
  
SUR **(** [ *partition_by_clause* ] [ *order_by_clause* ] [ *ROW_or_RANGE_clause* ] **)**  
*partition_by_clause* divise le jeu de résultats généré par la clause FROM en partitions auxquelles la fonction est appliquée. S'il n'est pas spécifié, la fonction gère toutes les lignes du jeu de résultats de la requête en un seul groupe. *order_by_clause* détermine l’ordre logique dans lequel l’opération est effectuée. Pour plus d’informations, consultez [la Clause OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).
  
## <a name="return-types"></a>Types de retour
 **int**  
  
## <a name="remarks"></a>Notes  
COUNT(*) renvoie le nombre d'éléments figurant dans un groupe. y compris les valeurs NULL et les doublons.
  
NOMBRE (tous les *expression*) prend la valeur *expression* pour chaque ligne d’un groupe et renvoie le nombre de valeurs non null.
  
COUNT (DISTINCT *expression*) prend la valeur *expression* pour chaque ligne d’un groupe et renvoie le nombre de valeurs uniques, non nulles.
  
Pour des valeurs renvoyées supérieures à 2^31-1, COUNT produit une erreur. Utilisez COUNT_BIG à la place.
  
COUNT est une fonction déterministe lorsqu'elle est utilisée sans les clauses OVER et ORDER BY. Elle n'est pas déterministe avec les clauses OVER et ORDER BY. Pour plus d’informations, consultez [Fonctions déterministes et non déterministes](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-count-and-distinct"></a>A. Utilisation de COUNT et DISTINCT  
L'exemple suivant liste le nombre de titres différents qu'un employé qui travaille à [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] peut porter.
  
```sql
SELECT COUNT(DISTINCT Title)  
FROM HumanResources.Employee;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
-----------
67  
  
(1 row(s) affected)
```
  
### <a name="b-using-count"></a>B. Utilisation de COUNT(*)  
L'exemple suivant recherche le nombre total d'employés travaillant à [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)].
  
```sql
SELECT COUNT(*)  
FROM HumanResources.Employee;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
-----------
290  
  
(1 row(s) affected)
```
  
### <a name="c-using-count-with-other-aggregates"></a>C. Utilisation de COUNT(*) avec d'autres fonctions d'agrégation  
L'exemple suivant illustre l'utilisation simultanée de `COUNT(*)` et d'autres fonctions d'agrégation dans la liste de sélection. L'exemple utilise la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].
  
```sql
SELECT COUNT(*), AVG(Bonus)  
FROM Sales.SalesPerson  
WHERE SalesQuota > 25000;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
----------- ---------------------
14            3472.1428
  
(1 row(s) affected)
```
  
### <a name="d-using-the-over-clause"></a>D. Utilisation de la clause OVER  
L'exemple suivant utilise les fonctions MIN, MAX, AVG et COUNT avec la clause OVER pour fournir des valeurs agrégées pour chaque service dans la table `HumanResources.Department` de la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].
  
```sql
SELECT DISTINCT Name  
       , MIN(Rate) OVER (PARTITION BY edh.DepartmentID) AS MinSalary  
       , MAX(Rate) OVER (PARTITION BY edh.DepartmentID) AS MaxSalary  
       , AVG(Rate) OVER (PARTITION BY edh.DepartmentID) AS AvgSalary  
       ,COUNT(edh.BusinessEntityID) OVER (PARTITION BY edh.DepartmentID) AS EmployeesPerDept  
FROM HumanResources.EmployeePayHistory AS eph  
JOIN HumanResources.EmployeeDepartmentHistory AS edh  
     ON eph.BusinessEntityID = edh.BusinessEntityID  
JOIN HumanResources.Department AS d  
ON d.DepartmentID = edh.DepartmentID
WHERE edh.EndDate IS NULL  
ORDER BY Name;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Name                          MinSalary             MaxSalary             AvgSalary             EmployeesPerDept  
----------------------------- --------------------- --------------------- --------------------- ----------------  
Document Control              10.25                 17.7885               14.3884               5  
Engineering                   32.6923               63.4615               40.1442               6  
Executive                     39.06                 125.50                68.3034               4  
Facilities and Maintenance    9.25                  24.0385               13.0316               7  
Finance                       13.4615               43.2692               23.935                10  
Human Resources               13.9423               27.1394               18.0248               6  
Information Services          27.4038               50.4808               34.1586               10  
Marketing                     13.4615               37.50                 18.4318               11  
Production                    6.50                  84.1346               13.5537               195  
Production Control            8.62                  24.5192               16.7746               8  
Purchasing                    9.86                  30.00                 18.0202               14  
Quality Assurance             10.5769               28.8462               15.4647               6  
Research and Development      40.8654               50.4808               43.6731               4  
Sales                         23.0769               72.1154               29.9719               18  
Shipping and Receiving        9.00                  19.2308               10.8718               6  
Tool Design                   8.62                  29.8462               23.5054               6  
  
(16 row(s) affected)
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-count-and-distinct"></a>E. Utilisation de COUNT et DISTINCT  
L’exemple suivant répertorie le nombre de titres différents qu’un employé qui travaille dans une société spécifique peut contenir.
  
```sql
USE ssawPDW;  
  
SELECT COUNT(DISTINCT Title)  
FROM dbo.DimEmployee;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
-----------
67
```  
  
### <a name="f-using-count"></a>F. Utilisation de COUNT(*)  
L’exemple suivant retourne le nombre total de lignes dans la `dbo.DimEmployee` table.
  
```sql
USE ssawPDW;  
  
SELECT COUNT(*)  
FROM dbo.DimEmployee;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
-------------
296
```  
  
### <a name="g-using-count-with-other-aggregates"></a>G. Utilisation de COUNT(*) avec d'autres fonctions d'agrégation  
L’exemple suivant combine `COUNT(*)` avec d’autres fonctions d’agrégation dans la liste de sélection. La requête retourne le nombre de représentants commerciaux avec un quota de ventes annuel est supérieur à 500 000 $ et le quota de ventes moyenne.
  
```sql
USE ssawPDW;  
  
SELECT COUNT(EmployeeKey) AS TotalCount, AVG(SalesAmountQuota) AS [Average Sales Quota]  
FROM dbo.FactSalesQuota  
WHERE SalesAmountQuota > 500000 AND CalendarYear = 2001;  
  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
TotalCount  Average Sales Quota
----------  -------------------
10          683800.0000
```
  
### <a name="h-using-count-with-having"></a>H. À l’aide de COUNT avec HAVING  
L’exemple suivant utilise le nombre avec la clause HAVING pour retourner les départements de l’entreprise qui ont plus de 15 employés.
  
```sql
USE ssawPDW;  
  
SELECT DepartmentName,   
       COUNT(EmployeeKey)AS EmployeesInDept  
FROM dbo.DimEmployee  
GROUP BY DepartmentName  
HAVING COUNT(EmployeeKey) > 15;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
DepartmentName  EmployeesInDept
--------------  ---------------
Sales           18
Production      179
```
  
### <a name="i-using-count-with-over"></a>I. À l’aide de COUNT avec basculement  
L’exemple suivant utilise le nombre avec la clause OVER pour retourner le nombre de produits qui sont contenus dans chacune des commandes client spécifiés.
  
```sql
USE ssawPDW;  
  
SELECT DISTINCT COUNT(ProductKey) OVER(PARTITION BY SalesOrderNumber) AS ProductCount  
    ,SalesOrderNumber  
FROM dbo.FactInternetSales  
WHERE SalesOrderNumber IN (N'SO53115',N'SO55981');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
ProductCount   SalesOrderID`
------------   -----------------
3              SO53115
1              SO55981
```
  
## <a name="see-also"></a>Voir aussi
[Fonctions d’agrégation &#40; Transact-SQL &#41;](../../t-sql/functions/aggregate-functions-transact-sql.md)  
[COUNT_BIG &#40; Transact-SQL &#41;](../../t-sql/functions/count-big-transact-sql.md)  
[SUR la clause for &#40; Transact-SQL &#41;](../../t-sql/queries/select-over-clause-transact-sql.md)
  
  




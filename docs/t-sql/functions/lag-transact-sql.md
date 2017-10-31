---
title: LAG (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 10/20/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- LAG_TSQL
- LAG
dev_langs:
- TSQL
helpviewer_keywords:
- LAG function
- analytic functions, LAG
ms.assetid: a9a90bdb-3f80-4c97-baca-b7407bcdc7f0
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 77598feb87f6766f6c24c454dace2c138315e69b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="lag-transact-sql"></a>LAG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Accède aux données d'une ligne précédente dans le même jeu de résultats sans recourir à une jointure réflexive dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. LAG permet d'accéder à une ligne à un décalage physique donné qui précède la ligne actuelle. Utilisez cette fonction analytique dans une instruction SELECT pour comparer des valeurs sur la ligne actuelle avec des valeurs sur une ligne précédente.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "icône lien de rubrique") [Conventions de syntaxe Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
LAG (scalar_expression [,offset] [,default])  
    OVER ( [ partition_by_clause ] order_by_clause )  
```  
  
## <a name="arguments"></a>Arguments  
 *scalar_expression*  
 Valeur à retourner en fonction du décalage spécifié. Il s'agit d'une expression de tout type qui retourne une valeur (scalaire) unique. *scalar_expression* ne peut pas être une fonction analytique.  
  
 *décalage*  
 Nombre de lignes en arrière de la ligne actuelle à partir de laquelle obtenir une valeur. Si cet argument n'est pas spécifié, la valeur par défaut est 1. *décalage* peut être une colonne, une sous-requête ou toute autre expression qui correspond à un entier positif ou peut être converti implicitement en **bigint**. *décalage* ne peut pas être une valeur négative ou une fonction analytique.  
  
 *par défaut*  
 La valeur à retourner lorsque *scalar_expression* à *offset* a la valeur NULL. Si aucune valeur par défaut n'est spécifiée, la valeur NULL est renvoyée. *par défaut* peut être une colonne, une sous-requête ou toute autre expression, mais il ne peut pas être une fonction analytique. *par défaut* doit être compatible avec *scalar_expression*.  
  
 SUR **(** [ *partition_by_clause* ] *order_by_clause***)**  
 *partition_by_clause* divise le jeu de résultats généré par la clause FROM en partitions auxquelles la fonction est appliquée. S'il n'est pas spécifié, la fonction gère toutes les lignes du jeu de résultats de la requête en un seul groupe. *order_by_clause* détermine l’ordre des données avant que la fonction est appliquée. Si *partition_by_clause* est spécifié, il détermine l’ordre des données dans la partition. Le *order_by_clause* est requis. Pour plus d’informations, consultez [la Clause OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
## <a name="return-types"></a>Types de retour  
 Le type de données spécifié *scalar_expression*. Valeur NULL est retournée si *scalar_expression* est nullable ou *par défaut* est définie sur NULL.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 LAG n'est pas déterministe. Pour plus d’informations, consultez [Fonctions déterministes et non déterministes](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-compare-values-between-years"></a>A. Comparer des valeurs entre des années  
 L'exemple suivant utilise la fonction LAG pour retourner la différence dans les quotas de ventes pour un employé spécifique sur les années précédentes. Notez que la valeur par défaut zéro (0) est retournée en raison de l'absence d'une valeur de décalage pour la première ligne.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT BusinessEntityID, YEAR(QuotaDate) AS SalesYear, SalesQuota AS CurrentQuota,   
       LAG(SalesQuota, 1,0) OVER (ORDER BY YEAR(QuotaDate)) AS PreviousQuota  
FROM Sales.SalesPersonQuotaHistory  
WHERE BusinessEntityID = 275 and YEAR(QuotaDate) IN ('2005','2006');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
BusinessEntityID SalesYear   CurrentQuota          PreviousQuota  
---------------- ----------- --------------------- ---------------------  
275              2005        367000.00             0.00  
275              2005        556000.00             367000.00  
275              2006        502000.00             556000.00  
275              2006        550000.00             502000.00  
275              2006        1429000.00            550000.00  
275              2006        1324000.00            1429000.00  
  
```  
  
### <a name="b-compare-values-within-partitions"></a>B. Comparer des valeurs dans des partitions  
 L'exemple suivant utilise la fonction LAG pour comparer les ventes annuelles cumulées entre les employés. La clause PARTITION BY est spécifiée pour diviser les lignes du jeu de résultats par secteur de vente. La fonction LAG est appliquée à chaque partition séparément et le calcul redémarre pour chaque partition. La clause ORDER BY de la clause OVER ordonnance les lignes dans chaque partition. La clause ORDER BY dans l'instruction SELECT trie les lignes dans le jeu de résultats entier. Notez que la valeur par défaut zéro (0) est retournée en raison de l'absence d'une valeur de décalage pour la première ligne de chaque partition.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT TerritoryName, BusinessEntityID, SalesYTD,   
       LAG (SalesYTD, 1, 0) OVER (PARTITION BY TerritoryName ORDER BY SalesYTD DESC) AS PrevRepSales  
FROM Sales.vSalesPerson  
WHERE TerritoryName IN (N'Northwest', N'Canada')   
ORDER BY TerritoryName;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
TerritoryName            BusinessEntityID SalesYTD              PrevRepSales  
-----------------------  ---------------- --------------------- ---------------------  
Canada                   282              2604540.7172          0.00  
Canada                   278              1453719.4653          2604540.7172  
Northwest                284              1576562.1966          0.00  
Northwest                283              1573012.9383          1576562.1966  
Northwest                280              1352577.1325          1573012.9383  
  
```  
  
### <a name="c-specifying-arbitrary-expressions"></a>C. Spécification d'expressions arbitraires  
 L'exemple suivant illustre la spécification de diverses expressions arbitraires dans la syntaxe de la fonction LAG.  
  
```  
CREATE TABLE T (a int, b int, c int);   
GO  
INSERT INTO T VALUES (1, 1, -3), (2, 2, 4), (3, 1, NULL), (4, 3, 1), (5, 2, NULL), (6, 1, 5);   
  
SELECT b, c,   
    LAG(2*c, b*(SELECT MIN(b) FROM T), -c/2.0) OVER (ORDER BY a) AS i  
FROM T;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
b           c           i  
----------- ----------- -----------  
1           -3          1  
2           4           -2  
1           NULL        8  
3           1           -6  
2           NULL        NULL  
1           5           NULL  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-compare-values-between-quarters"></a>D: comparer des valeurs entre les trimestres  
 L’exemple suivant illustre la fonction LAG. La requête utilise la fonction LAG pour retourner la différence dans les quotas de ventes pour un employé spécifique sur trimestres précédents de calendrier. Notez que la valeur par défaut zéro (0) est retournée en raison de l'absence d'une valeur de décalage pour la première ligne.  
  
```  
-- Uses AdventureWorks  
  
SELECT CalendarYear, CalendarQuarter, SalesAmountQuota AS SalesQuota,  
       LAG(SalesAmountQuota,1,0) OVER (ORDER BY CalendarYear, CalendarQuarter) AS PrevQuota,  
       SalesAmountQuota - LAG(SalesAmountQuota,1,0) OVER (ORDER BY CalendarYear, CalendarQuarter) AS Diff  
FROM dbo.FactSalesQuota  
WHERE EmployeeKey = 272 AND CalendarYear IN (2001, 2002)  
ORDER BY CalendarYear, CalendarQuarter;   
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Year Quarter  SalesQuota  PrevQuota  Diff  
---- -------  ----------  ---------  -------------  
2001 3        28000.0000      0.0000   28000.0000  
2001 4         7000.0000  28000.0000  -21000.0000  
2001 1        91000.0000   7000.0000   84000.0000  
2002 2       140000.0000  91000.0000   49000.0000  
2002 3         7000.0000 140000.0000  -70000.0000  
2002 4       154000.0000   7000.0000   84000.0000
```  
  
## <a name="see-also"></a>Voir aussi  
 [PROSPECT &#40; Transact-SQL &#41;](../../t-sql/functions/lead-transact-sql.md)  
  
  




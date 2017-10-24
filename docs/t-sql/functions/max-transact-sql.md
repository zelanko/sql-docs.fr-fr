---
title: MAX (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 08/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- MAX
- MAX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MAX function [Transact-SQL]
- values [SQL Server], maximum
- maximum values [SQL Server]
ms.assetid: 9b002b69-ab5e-472d-b12e-dc2fbe35ef42
caps.latest.revision: 38
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b6b784c3ac2140992ba7eaad65f9b3f57e0fb966
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="max-transact-sql"></a>MAX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne la valeur maximale de l'expression.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
MAX ( [ ALL | DISTINCT ] expression )  
   OVER ( [ partition_by_clause ] order_by_clause )     
```  
  
## <a name="arguments"></a>Arguments  
 **ALL**  
 Applique la fonction d'agrégation à toutes les valeurs. ALL est l'argument par défaut.  
  
 DISTINCT  
 Spécifie que chaque valeur unique est prise en considération. DISTINCT n'a pas d'effet avec MAX et n'est disponible que pour la compatibilité ISO.  
  
 *expression*  
 Constante, nom de colonne ou fonction, et toute combinaison d'opérateurs arithmétiques, de type chaîne ou binaire. MAX peut être utilisé avec **numérique**, **caractère**, **uniqueidentifier**, et **datetime** colonnes, mais pas avec **bits** colonnes. Les fonctions d'agrégation et les sous-requêtes ne sont pas autorisées.  
  
 Pour plus d’informations, consultez [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 SUR **(** [ *partition_by_clause* ] *order_by_clause***)**  
 *partition_by_clause* divise le jeu de résultats généré par la clause FROM en partitions auxquelles la fonction est appliquée. S'il n'est pas spécifié, la fonction gère toutes les lignes du jeu de résultats de la requête en un seul groupe. *order_by_clause* détermine l’ordre logique dans lequel l’opération est effectuée. *order_by_clause* est requis. Pour plus d’informations, consultez [la Clause OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
## <a name="return-types"></a>Types de retour  
 Retourne une valeur identique *expression*.  
  
## <a name="remarks"></a>Notes  
 MAX ignore toutes les valeurs NULL.  
  
 Pour les colonnes de type caractère, MAX recherche la valeur la plus élevée dans l'ordre de classement des caractères.  
  
 MAX est une fonction déterministe lorsqu'elle est utilisée sans les clauses OVER et ORDER BY. Elle n'est pas déterministe avec les clauses OVER et ORDER BY. Pour plus d’informations, consultez [Fonctions déterministes et non déterministes](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-simple-example"></a>A. Exemple simple  
 L'exemple suivant retourne le taux d'imposition (maximal) le plus élevé dans la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```sql  
SELECT MAX(TaxRate)  
FROM Sales.SalesTaxRate;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 -------------------  
 19.60  
 Warning, null value eliminated from aggregate.  
  
 (1 row(s) affected)  
 ```  
  
### <a name="b-using-the-over-clause"></a>B. Utilisation de la clause OVER  
 L’exemple suivant utilise les fonctions MIN, MAX, AVG et COUNT avec la clause OVER pour fournir des valeurs agrégées pour chaque service dans le `HumanResources.Department` de table dans le [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] base de données.  
  
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
  
```  
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
  
### <a name="c-using-max-with-character-data"></a>C. À l’aide de MAX avec des données caractères   
L’exemple suivant retourne le nom de la base de données qui trie par ordre alphabétique en tant que le nom de famille. L’exemple utilise `WHERE database_id < 5`, à prendre en compte uniquement les bases de données système.  
```sql   
SELECT MAX(name) FROM sys.databases WHERE database_id < 5;
```
La dernière base de données système est `tempdb`.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’agrégation &#40; Transact-SQL &#41;](../../t-sql/functions/aggregate-functions-transact-sql.md)   
 [SUR la clause for &#40; Transact-SQL &#41;](../../t-sql/queries/select-over-clause-transact-sql.md)  
  
  



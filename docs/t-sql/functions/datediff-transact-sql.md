---
title: DATEDIFF (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATEDIFF_TSQL
- DATEDIFF
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- DATEDIFF function [SQL Server]
- time [SQL Server], crossed boundaries
- differences in date and time [SQL Server]
- counting crossed date time boundaries [SQL Server]
- date and time [SQL Server], DATEDIFF
- dates [SQL Server], crossed boundaries
- boundary differences date and time [SQL Server]
- functions [SQL Server], time
- functions [SQL Server], date and time
- interval dates [SQL Server]
- time [SQL Server], functions
- crossing date time boundaries [SQL Server]
- calculating dates times [SQL Server]
ms.assetid: eba979f2-1a8d-4cce-9d75-b74f9b519b37
caps.latest.revision: 52
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 80c1228faeaaa4012afc0fd27992a2f5cf389f6e
ms.openlocfilehash: dba834b51bab48c2bd30d1bbbb4abe11694ab321
ms.contentlocale: fr-fr
ms.lasthandoff: 10/05/2017

---
# <a name="datediff-transact-sql"></a>DATEDIFF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Retourne le nombre (entier signé) spécifié *datepart* limites comprises entre spécifié *startdate* et *enddate*.
  
Pour les différences de plus grandes, consultez [DATEDIFF_BIG &#40; Transact-SQL &#41; ](../../t-sql/functions/datediff-big-transact-sql.md). Pour une vue d’ensemble de tous les [!INCLUDE[tsql](../../includes/tsql-md.md)] les types de données date et heure et les fonctions, consultez [Date et fonctions et Types de données &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
DATEDIFF ( datepart , startdate , enddate )  
```  
  
## <a name="arguments"></a>Arguments  
*partie de date*  
Est la partie de *startdate* et *enddate* qui spécifie le type de limite traversée. Le tableau suivant répertorie toutes valides *datepart* arguments. Les équivalents de variables définis par l'utilisateur ne sont pas valides.
  
|*partie de date*|Abréviations|  
|---|---|
|**année**|**yy, yyyy**|  
|**trimestre**|**qq, q**|  
|**mois**|**mm, m**|  
|**DAYOFYEAR**|**dy, y**|  
|**jour**|**DD, d**|  
|**semaine**|**wk, ww**|  
|**heure**|**hh**|  
|**minute**|**héritage multiple, n**|  
|**seconde**|**ss, s**|  
|**milliseconde**|**MS**|  
|**microsecondes**|**MCS**|  
|**nanosecondes**|**NS**|  
  
*startdate*  
Est une expression qui peut être résolue en un **temps**, **date**, **smalldatetime**, **datetime**, **datetime2**, ou **datetimeoffset** valeur. *date* peut être une expression, l’expression de colonne, variable définie par l’utilisateur ou de chaîne littérale. *StartDate* est soustraite de *enddate*.
  
Pour éviter toute ambiguïté, représentez les années à l'aide de quatre chiffres. Pour plus d’informations sur les années de deux chiffres, consultez [configurer l’année à deux chiffres cutoff Server Configuration Option](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).
  
*date de fin*  
Consultez *startdate*.
  
## <a name="return-type"></a>Type de retour  
 **int**  
  
## <a name="return-value"></a>Valeur retournée  
  
-   Chaque *datepart* et ses abréviations retournent la même valeur.  
  
Si la valeur de retour est hors limites pour **int** (allant de -2,147,483,648 à +2,147,483,647), une erreur est retournée. Pour **milliseconde**, la différence maximale entre *startdate* et *enddate* est de 24 jours, 20 heures, 31 minutes et 23,647 secondes. Pour **deuxième**, la différence maximale est de 68 ans.
  
Si *startdate* et *enddate* assignées à la fois une valeur d’heure et la *datepart* n’est pas une heure *datepart*, 0 est retourné.
  
Un fuseau horaire de composant de décalage *startdate* ou *endate* n’est pas utilisé dans le calcul de la valeur de retour.
  
Étant donné que [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md) est exacte uniquement à la minute, lorsqu’un **smalldatetime** valeur est utilisée pour *startdate* ou *enddate*, secondes et les millisecondes sont toujours définies sur 0 dans la valeur de retour.
  
Si une valeur d'heure uniquement est assignée à une variable d'un type de données date, la valeur de la partie date manquante est égale à la valeur par défaut : 1900-01-01. Si une valeur de date uniquement est assignée à une variable d'un type de données date ou heure, la valeur de la partie heure manquante est égale à la valeur par défaut : 00-00-00. Si le paramètre *startdate* ou *enddate* avoir uniquement une partie de l’heure et l’autre uniquement une partie de date, heure manquante et parties de date sont définis pour les valeurs par défaut.
  
Si *startdate* et *enddate* sont des types de données date différents et l’autre a plus de parties heure ou de précision en fractions de seconde à l’autre, les parties manquantes de l’autre sont définies sur 0.
  
## <a name="datepart-boundaries"></a>limites de DATEPART  
Les instructions suivantes ont la même *startdate* et le même *endate*. Ces dates sont adjacentes et ont une différence horaire de .0000001 seconde. La différence entre la *startdate* et *endate* dans chaque instruction traverse un calendrier ou limite d’heure de son *datepart*. Chaque instruction retourne 1. Si des années différentes sont utilisées pour cet exemple et si les deux *startdate* et *endate* se trouvent dans la même semaine de calendrier, la valeur de retour pour **semaine** serait 0.
  
```sql
SELECT DATEDIFF(year, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(quarter, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(month, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(dayofyear, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(day, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(week, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(hour, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(minute, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(second, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
SELECT DATEDIFF(millisecond, '2005-12-31 23:59:59.9999999', '2006-01-01 00:00:00.0000000');
```
  
## <a name="remarks"></a>Notes  
DATEDIFF peut être utilisé dans la liste de sélection et les clauses WHERE, HAVING, GROUP BY et ORDER BY.
  
DATEDIFF convertit implicitement les littéraux de chaîne comme un **datetime2** type. Cela signifie que DATEDIFF ne prend pas en charge le format YDM lorsque la date est transmise en tant que chaîne. Vous devez convertir explicitement la chaîne à un **datetime** ou **smalldatetime** type à utiliser le format YDM.
  
La spécification SET DATEFIRST n'a aucun effet sur DATEDIFF. DATEDIFF utilise toujours Dimanche comme le premier jour de la semaine pour que la fonction soit déterministe.
  
## <a name="examples"></a>Exemples  
Les exemples suivants utilisent différents types d’expressions comme arguments pour le *startdate* et *enddate* paramètres.
  
### <a name="a-specifying-columns-for-startdate-and-enddate"></a>A. Spécification de colonnes pour les dates de début et de fin  
L'exemple suivant calcule le nombre de limites de jour qui sont traversées entre des dates de deux colonnes dans une table.
  
```sql
CREATE TABLE dbo.Duration  
    (  
    startDate datetime2  
    ,endDate datetime2  
    );  
INSERT INTO dbo.Duration(startDate,endDate)  
    VALUES('2007-05-06 12:10:09','2007-05-07 12:10:09');  
SELECT DATEDIFF(day,startDate,endDate) AS 'Duration'  
FROM dbo.Duration;  
-- Returns: 1  
```  
  
### <a name="b-specifying-user-defined-variables-for-startdate-and-enddate"></a>B. Spécification de variables définies par l'utilisateur pour les dates de début et de fin  
L’exemple suivant utilise les variables définies par l’utilisateur en tant qu’arguments pour *startdate* et *enddate*.
  
```sql
DECLARE @startdate datetime2 = '2007-05-05 12:10:09.3312722';  
DECLARE @enddate datetime2 = '2007-05-04 12:10:09.3312722';   
SELECT DATEDIFF(day, @startdate, @enddate);  
```  
  
### <a name="c-specifying-scalar-system-functions-for-startdate-and-enddate"></a>C. Spécification de fonctions système scalaires pour les dates de début et de fin  
L’exemple suivant utilise des fonctions système scalaires comme arguments pour *startdate* et *enddate*.
  
```sql
SELECT DATEDIFF(millisecond, GETDATE(), SYSDATETIME());  
```  
  
### <a name="d-specifying-scalar-subqueries-and-scalar-functions-for-startdate-and-enddate"></a>D. Spécification de sous-requêtes scalaires et de fonctions scalaires pour les dates de début et de fin  
L’exemple suivant utilise des sous-requêtes scalaires et fonctions scalaires comme arguments pour *startdate* et *enddate*.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT DATEDIFF(day,(SELECT MIN(OrderDate) FROM Sales.SalesOrderHeader),  
    (SELECT MAX(OrderDate) FROM Sales.SalesOrderHeader));  
```  
  
### <a name="e-specifying-constants-for-startdate-and-enddate"></a>E. Spécification de constantes pour les dates de début et de fin  
L’exemple suivant utilise les constantes de caractère comme arguments pour *startdate* et *enddate*.
  
```sql
SELECT DATEDIFF(day, '2007-05-07 09:53:01.0376635'  
    , '2007-05-08 09:53:01.0376635');  
```  
  
### <a name="f-specifying-numeric-expressions-and-scalar-system-functions-for-enddate"></a>F. Spécification d'expressions numériques et de fonctions système scalaires pour la date de fin  
L’exemple suivant utilise une expression numérique, `(GETDATE ()+ 1)`et des fonctions système scalaires, `GETDATE` et `SYSDATETIME`, comme arguments pour *enddate*.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT DATEDIFF(day, '2007-05-07 09:53:01.0376635', GETDATE()+ 1)   
    AS NumberOfDays  
FROM Sales.SalesOrderHeader;  
GO  
USE AdventureWorks2012;  
GO  
SELECT DATEDIFF(day, '2007-05-07 09:53:01.0376635', DATEADD(day,1,SYSDATETIME())) AS NumberOfDays  
FROM Sales.SalesOrderHeader;  
GO  
```  
  
### <a name="g-specifying-ranking-functions-for-startdate"></a>G. Spécification de fonctions de classement pour la date de début  
L’exemple suivant utilise une fonction de classement en tant qu’argument pour *startdate*.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT p.FirstName, p.LastName  
    ,DATEDIFF(day,ROW_NUMBER() OVER (ORDER BY   
        a.PostalCode),SYSDATETIME()) AS 'Row Number'  
FROM Sales.SalesPerson s   
    INNER JOIN Person.Person p   
        ON s.BusinessEntityID = p.BusinessEntityID  
    INNER JOIN Person.Address a   
        ON a.AddressID = p.BusinessEntityID  
WHERE TerritoryID IS NOT NULL   
    AND SalesYTD <> 0;  
```  
  
### <a name="h-specifying-an-aggregate-window-function-for-startdate"></a>H. Spécification d'une fonction d'agrégation pour la date de début  
L’exemple suivant utilise une fonction d’agrégation en tant qu’argument pour *startdate*.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT soh.SalesOrderID, sod.ProductID, sod.OrderQty,soh.OrderDate  
    ,DATEDIFF(day,MIN(soh.OrderDate)   
        OVER(PARTITION BY soh.SalesOrderID),SYSDATETIME() ) AS 'Total'  
FROM Sales.SalesOrderDetail sod  
    INNER JOIN Sales.SalesOrderHeader soh  
        ON sod.SalesOrderID = soh.SalesOrderID  
WHERE soh.SalesOrderID IN(43659,58918);  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
Les exemples suivants utilisent différents types d’expressions comme arguments pour le *startdate* et *enddate* paramètres.
  
### <a name="i-specifying-columns-for-startdate-and-enddate"></a>I. Spécification de colonnes pour les dates de début et de fin  
L'exemple suivant calcule le nombre de limites de jour qui sont traversées entre des dates de deux colonnes dans une table.
  
```sql
CREATE TABLE dbo.Duration (  
    startDate datetime2  
    ,endDate datetime2  
    );  
INSERT INTO dbo.Duration(startDate,endDate)  
    VALUES('2007-05-06 12:10:09','2007-05-07 12:10:09');  
SELECT TOP(1) DATEDIFF(day,startDate,endDate) AS Duration  
FROM dbo.Duration;  
-- Returns: 1  
```  
  
### <a name="j-specifying-scalar-subqueries-and-scalar-functions-for-startdate-and-enddate"></a>J. Spécification de sous-requêtes scalaires et de fonctions scalaires pour les dates de début et de fin  
L’exemple suivant utilise des sous-requêtes scalaires et fonctions scalaires comme arguments pour *startdate* et *enddate*.
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP(1) DATEDIFF(day,(SELECT MIN(HireDate) FROM dbo.DimEmployee),  
    (SELECT MAX(HireDate) FROM dbo.DimEmployee))   
FROM dbo.DimEmployee;  
  
```  
  
### <a name="k-specifying-constants-for-startdate-and-enddate"></a>K. Spécification de constantes pour les dates de début et de fin  
L’exemple suivant utilise les constantes de caractère comme arguments pour *startdate* et *enddate*.
  
```sql
-- Uses AdventureWorks  
  
SELECT TOP(1) DATEDIFF(day, '2007-05-07 09:53:01.0376635'  
    , '2007-05-08 09:53:01.0376635') FROM DimCustomer;  
```  
  
### <a name="l-specifying-ranking-functions-for-startdate"></a>L. Spécification de fonctions de classement pour la date de début  
L’exemple suivant utilise une fonction de classement en tant qu’argument pour *startdate*.
  
```sql
-- Uses AdventureWorks  
  
SELECT FirstName, LastName  
,DATEDIFF(day,ROW_NUMBER() OVER (ORDER BY   
        DepartmentName),SYSDATETIME()) AS RowNumber  
FROM dbo.DimEmployee;  
```  
  
### <a name="m-specifying-an-aggregate-window-function-for-startdate"></a>M. Spécification d'une fonction d'agrégation pour la date de début  
L’exemple suivant utilise une fonction d’agrégation en tant qu’argument pour *startdate*.
  
```sql
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, DepartmentName  
    ,DATEDIFF(year,MAX(HireDate)  
             OVER (PARTITION BY DepartmentName),SYSDATETIME()) AS SomeValue  
FROM dbo.DimEmployee  
```  
  
## <a name="see-also"></a>Voir aussi
[DATEDIFF_BIG &#40; Transact-SQL &#41;](../../t-sql/functions/datediff-big-transact-sql.md)  
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  




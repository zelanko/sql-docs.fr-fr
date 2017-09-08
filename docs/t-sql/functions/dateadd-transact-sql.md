---
title: DATEADD (Transact-SQL) | Documents Microsoft
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
- DATEADD
- DATEADD_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- add interval to date or time [SQL Server]
- subtract interval from date or time [SQL Server]
- functions [SQL Server], time
- functions [SQL Server], date and time
- time [SQL Server], functions
- dates [SQL Server], intervals
- date and time [SQL Server], DATEADD
- DATEADD function [SQL Server]
ms.assetid: 89c5ae32-89c6-47e1-979e-15d97908b9f1
caps.latest.revision: 71
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6a90b51a1ef2156a2a05b8d3dd4e15111872edf6
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="dateadd-transact-sql"></a>DATEADD (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Retourne un *date* avec l’objet *nombre* intervalle (entier signé) ajouté à un *datepart* de qui *date*.
  
Pour une vue d’ensemble de tous les [!INCLUDE[tsql](../../includes/tsql-md.md)] les types de données date et heure et les fonctions, consultez [Date et fonctions et Types de données &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
DATEADD (datepart , number , date )  
```  
  
## <a name="arguments"></a>Arguments  
*partie de date*  
Est la partie de *date* auquel un **entier***nombre* est ajouté. Le tableau suivant répertorie toutes valides *datepart* arguments. Les équivalents de variables définis par l'utilisateur ne sont pas valides.
  
|*partie de date*|Abréviations|  
|---|---|
|**année**|**aa**, **aaaa**|  
|**trimestre**|**qq**, **q**|  
|**mois**|**mm**, **m**|  
|**DAYOFYEAR**|**dy**, **y**|  
|**jour**|**DD**, **d**|  
|**semaine**|**wk**, **ww**|  
|**jour de la semaine**|**entrepôt de données**, **w**|  
|**heure**|**hh**|  
|**minute**|**héritage multiple**,**n**|  
|**seconde**|**ss**, **s**|  
|**milliseconde**|**MS**|  
|**microsecondes**|**MCS**|  
|**nanosecondes**|**NS**|  
  
*nombre*  
Est une expression qui peut être résolue en un [int](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md) qui est ajouté à un *datepart* de *date*. Les variables définies par l'utilisateur sont valides.  
Si vous spécifiez une valeur avec une fraction décimale, la fraction est tronquée et n'est pas arrondie.
  
*date*  
Est une expression qui peut être résolue en un **temps**, **date**, **smalldatetime**, **datetime**, **datetime2**, ou **datetimeoffset** valeur. *date* peut être une expression, une expression de colonne, une variable définie par l’utilisateur ou une chaîne littérale. Si l’expression est un littéral de chaîne, il doit correspondre à un **datetime**. Pour éviter toute ambiguïté, représentez les années à l'aide de quatre chiffres. Pour plus d’informations sur les années à deux chiffres, consultez [configurer l’année à deux chiffres cutoff Server Configuration Option](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).
  
## <a name="return-types"></a>Types de retour
Le type de données de retour est le type de données de la *date* argument, à l’exception des littéraux de chaîne.
Les données de retournées de type pour un littéral de chaîne est **datetime**. Une erreur sera déclenchée si l'échelle des secondes du littéral de chaîne comprend plus de trois positions (.nnn) ou contient la partie du décalage de fuseau horaire.
  
## <a name="return-value"></a>Valeur retournée  
  
## <a name="datepart-argument"></a>Argument datepart  
**DAYOFYEAR**, **jour**, et **semaine** retournent la même valeur.
  
Chaque *datepart* et ses abréviations retournent la même valeur.
  
Si *datepart* est **mois** et *date* mois a plus de jours que le mois et le *date* jour n’existe pas dans le mois retourné, le dernier jour du mois est retourné. Par exemple, septembre compte 30 jours ; par conséquent, les deux instructions suivantes retournent 2006-09-30 00:00:00.000:
  
```sql
SELECT DATEADD(month, 1, '2006-08-30');
SELECT DATEADD(month, 1, '2006-08-31');
```
  
## <a name="number-argument"></a>Argument number  
Le *nombre* argument ne peut pas dépasser la plage de **int**. Dans les instructions suivantes, l’argument de *nombre* dépasse la plage de **int** par 1. Le message d'erreur suivant est retourné :`Msg 8115, Level 16, State 2, Line 1. Arithmetic overflow error converting expression to data type int."`
  
```sql
SELECT DATEADD(year,2147483648, '2006-07-31');  
SELECT DATEADD(year,-2147483649, '2006-07-31');  
```  
  
## <a name="date-argument"></a>Argument date  
Le *date* argument ne peut pas être incrémenté à une valeur en dehors de la plage de son type de données. Dans les instructions suivantes, le *nombre* valeur qui est ajoutée à la *date* valeur dépasse la plage de la *date* type de données. Le message d'erreur suivant est retourné :`Msg 517, Level 16, State 1, Line 1 Adding a value to a 'datetime' column caused overflow`.
  
```sql
SELECT DATEADD(year,2147483647, '2006-07-31');  
SELECT DATEADD(year,-2147483647, '2006-07-31');  
```  
  
## <a name="return-values-for-a-smalldatetime-date-and-a-second-or-fractional-seconds-datepart"></a>Valeurs retournées pour une date smalldatetime et une partie de date seconde ou fractions de seconde  
La partie secondes d’une [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md) valeur est toujours 00. Si *date* est **smalldatetime**, les remarques suivantes s’appliquent :
-   Si *datepart* est **deuxième** et *nombre* est comprise entre-30 et +29, aucun ajout n’est effectuée.  
-   Si *datepart* est **deuxième** et *nombre* est inférieure à 30 ou plus de +29, ajout est effectué en commençant à une minute.  
-   Si *datepart* est **milliseconde** et *nombre* est comprise entre-30001 et + 29998, aucun ajout n’est effectuée.  
-   Si *datepart* est **milliseconde** et *nombre* est inférieur à -30001 ou supérieur à + 29998, ajout est effectué en commençant à une minute.  
  
## <a name="remarks"></a>Notes  
DATEADD peut être utilisé dans l’instruction SELECT \<liste >, où, HAVING, les clauses GROUP BY et ORDER BY.
  
## <a name="fractional-seconds-precision"></a>Précision en fractions de seconde
Ajout d’un *datepart* de **microsecondes** ou **nanosecondes** pour *date* des types de données **smalldatetime**, **date**, et **datetime** n’est pas autorisée.
  
Les millisecondes ont une échelle de 3 (0,123). Les microsecondes ont une échelle de 6 (0,123456). Les nanosecondes ont une échelle de 9 (0,123456789). Le **temps**, **datetime2**, et **datetimeoffset** des types de données ont une échelle maximale de 7 (. 1234567). Si *datepart* est **nanosecondes**, *nombre* doit être 100 avant que les fractions de *date* augmenter. A *nombre* compris entre 1 et 49 est arrondi à 0 et de nombre compris entre 50 et 99 est arrondi à 100.
  
Les instructions suivantes ajoutent un *datepart* de **milliseconde**, **microsecondes**, ou **nanosecondes**.
  
```sql
DECLARE @datetime2 datetime2 = '2007-01-01 13:10:10.1111111';  
SELECT '1 millisecond', DATEADD(millisecond,1,@datetime2)  
UNION ALL  
SELECT '2 milliseconds', DATEADD(millisecond,2,@datetime2)  
UNION ALL  
SELECT '1 microsecond', DATEADD(microsecond,1,@datetime2)  
UNION ALL  
SELECT '2 microseconds', DATEADD(microsecond,2,@datetime2)  
UNION ALL  
SELECT '49 nanoseconds', DATEADD(nanosecond,49,@datetime2)  
UNION ALL  
SELECT '50 nanoseconds', DATEADD(nanosecond,50,@datetime2)  
UNION ALL  
SELECT '150 nanoseconds', DATEADD(nanosecond,150,@datetime2);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1 millisecond     2007-01-01 13:10:10.1121111  
2 milliseconds    2007-01-01 13:10:10.1131111  
1 microsecond     2007-01-01 13:10:10.1111121  
2 microseconds    2007-01-01 13:10:10.1111131  
49 nanoseconds    2007-01-01 13:10:10.1111111  
50 nanoseconds    2007-01-01 13:10:10.1111112  
150 nanoseconds   2007-01-01 13:10:10.1111113  
```  
  
## <a name="time-zone-offset"></a>Décalage de fuseau horaire
L'ajout n'est pas autorisé pour le décalage de fuseau horaire.
  
## <a name="examples"></a>Exemples  

### <a name="a-incrementing-datepart-by-an-interval-of-1"></a>A. Incrémentation d'une partie de date d'un intervalle de 1  
Chacune des instructions suivantes incrémente *datepart* par un intervalle de 1.
  
```sql
DECLARE @datetime2 datetime2 = '2007-01-01 13:10:10.1111111';  
SELECT 'year', DATEADD(year,1,@datetime2)  
UNION ALL  
SELECT 'quarter',DATEADD(quarter,1,@datetime2)  
UNION ALL  
SELECT 'month',DATEADD(month,1,@datetime2)  
UNION ALL  
SELECT 'dayofyear',DATEADD(dayofyear,1,@datetime2)  
UNION ALL  
SELECT 'day',DATEADD(day,1,@datetime2)  
UNION ALL  
SELECT 'week',DATEADD(week,1,@datetime2)  
UNION ALL  
SELECT 'weekday',DATEADD(weekday,1,@datetime2)  
UNION ALL  
SELECT 'hour',DATEADD(hour,1,@datetime2)  
UNION ALL  
SELECT 'minute',DATEADD(minute,1,@datetime2)  
UNION ALL  
SELECT 'second',DATEADD(second,1,@datetime2)  
UNION ALL  
SELECT 'millisecond',DATEADD(millisecond,1,@datetime2)  
UNION ALL  
SELECT 'microsecond',DATEADD(microsecond,1,@datetime2)  
UNION ALL  
SELECT 'nanosecond',DATEADD(nanosecond,1,@datetime2);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Year         2008-01-01 13:10:10.1111111  
quarter      2007-04-01 13:10:10.1111111  
month        2007-02-01 13:10:10.1111111  
dayofyear    2007-01-02 13:10:10.1111111  
day          2007-01-02 13:10:10.1111111  
week         2007-01-08 13:10:10.1111111  
weekday      2007-01-02 13:10:10.1111111  
hour         2007-01-01 14:10:10.1111111  
minute       2007-01-01 13:11:10.1111111  
second       2007-01-01 13:10:11.1111111  
millisecond  2007-01-01 13:10:10.1121111  
microsecond  2007-01-01 13:10:10.1111121  
nanosecond   2007-01-01 13:10:10.1111111  
```  
  
### <a name="b-incrementing-more-than-one-level-of-datepart-in-one-statement"></a>B. Incrémentation de plusieurs niveaux d'une partie de date dans une instruction  
Chacune des instructions suivantes incrémente *datepart* par un *nombre* suffisamment grand pour incrémenter également la prochaine supérieur *datepart* de *date*.
  
```sql
DECLARE @datetime2 datetime2;  
SET @datetime2 = '2007-01-01 01:01:01.1111111';  
--Statement                                 Result     
-------------------------------------------------------------------   
SELECT DATEADD(quarter,4,@datetime2);     --2008-01-01 01:01:01.110  
SELECT DATEADD(month,13,@datetime2);      --2008-02-01 01:01:01.110  
SELECT DATEADD(dayofyear,365,@datetime2); --2008-01-01 01:01:01.110  
SELECT DATEADD(day,365,@datetime2);       --2008-01-01 01:01:01.110  
SELECT DATEADD(week,5,@datetime2);        --2007-02-05 01:01:01.110  
SELECT DATEADD(weekday,31,@datetime2);    --2007-02-01 01:01:01.110  
SELECT DATEADD(hour,23,@datetime2);       --2007-01-02 00:01:01.110  
SELECT DATEADD(minute,59,@datetime2);     --2007-01-01 02:00:01.110  
SELECT DATEADD(second,59,@datetime2);     --2007-01-01 01:02:00.110  
SELECT DATEADD(millisecond,1,@datetime2); --2007-01-01 01:01:01.110  
```  
  
### <a name="c-using-expressions-as-arguments-for-the-number-and-date-parameters"></a>C. Utilisation d'expressions comme arguments pour les paramètres de date et numériques  
Les exemples suivants utilisent différents types d’expressions comme arguments pour le *nombre* et *date* paramètres. Les exemples utilisent la base de données AdventureWorks.
  
#### <a name="specifying-a-column-as-date"></a>Spécification d'une colonne comme date  
L'exemple suivant ajoute `2` jours à chaque valeur figurant dans la colonne `OrderDate` pour dériver une nouvelle colonne nommée `PromisedShipDate`.
  
```sql
SELECT SalesOrderID  
    ,OrderDate   
    ,DATEADD(day,2,OrderDate) AS PromisedShipDate  
FROM Sales.SalesOrderHeader;  
```  
  
Voici un jeu de résultats partiel.
  
```sql
SalesOrderID OrderDate               PromisedShipDate  
------------ ----------------------- -----------------------  
43659        2005-07-01 00:00:00.000 2005-07-03 00:00:00.000  
43660        2005-07-01 00:00:00.000 2005-07-03 00:00:00.000  
43661        2005-07-01 00:00:00.000 2005-07-03 00:00:00.000  
...  
43702        2005-07-02 00:00:00.000 2005-07-04 00:00:00.000  
43703        2005-07-02 00:00:00.000 2005-07-04 00:00:00.000  
43704        2005-07-02 00:00:00.000 2005-07-04 00:00:00.000  
43705        2005-07-02 00:00:00.000 2005-07-04 00:00:00.000  
43706        2005-07-03 00:00:00.000 2005-07-05 00:00:00.000  
...  
43711        2005-07-04 00:00:00.000 2005-07-06 00:00:00.000  
43712        2005-07-04 00:00:00.000 2005-07-06 00:00:00.000  
...  
43740        2005-07-11 00:00:00.000 2005-07-13 00:00:00.000  
43741        2005-07-12 00:00:00.000 2005-07-14 00:00:00.000  
  
```  
  
#### <a name="specifying-user-defined-variables-as-number-and-date"></a>Spécification de variables définies par l'utilisateur comme nombre et date  
L’exemple suivant spécifie les variables définies par l’utilisateur en tant qu’arguments pour *nombre* et *date*.
  
```sql
DECLARE @days int = 365,   
        @datetime datetime = '2000-01-01 01:01:01.111'; /* 2000 was a leap year */;  
SELECT DATEADD(day, @days, @datetime);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
-----------------------  
2000-12-31 01:01:01.110  
  
(1 row(s) affected)  
```  
  
#### <a name="specifying-scalar-system-function-as-date"></a>Spécification de la fonction système scalaire comme date  
L’exemple suivant spécifie `SYSDATETIME` pour *date*.
  
```sql
SELECT DATEADD(month, 1, SYSDATETIME());  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
---------------------------  
2013-02-06 14:29:59.6727944  
  
(1 row(s) affected)  
```  
  
#### <a name="specifying-scalar-subqueries-and-scalar-functions-as-number-and-date"></a>Spécification de sous-requêtes scalaires et de fonctions scalaires comme nombre et date  
L’exemple suivant utilise des sous-requêtes scalaires, `MAX(ModifiedDate)`, comme arguments pour *nombre* et *date*. `(SELECT TOP 1 BusinessEntityID FROM Person.Person)`est un argument artificiel pour le paramètre numérique montrer comment sélectionner un *nombre* argument à partir d’une liste de valeurs.
  
```sql
SELECT DATEADD(month,(SELECT TOP 1 BusinessEntityID FROM Person.Person),  
    (SELECT MAX(ModifiedDate) FROM Person.Person));  
```  
  
#### <a name="specifying-numeric-expressions-and-scalar-system-functions-as-number-and-date"></a>Spécification d'expressions numériques et de fonctions système scalaires comme nombre et date  
L’exemple suivant utilise une expression numérique (-`(10/2))`, [opérateurs unaires](../../mdx/unary-operators.md) (`-`), un [opérateur arithmétique](../../mdx/arithmetic-operators.md) (`/`) et des fonctions système scalaires (`SYSDATETIME`) en tant qu’arguments pour *nombre* et *date*.
  
```sql
SELECT DATEADD(month,-(10/2), SYSDATETIME());  
```  
  
#### <a name="specifying-ranking-functions-as-number"></a>Spécification de fonctions de classement comme nombre  
L’exemple suivant utilise une fonction de classement comme arguments pour *nombre*.
  
```sql
SELECT p.FirstName, p.LastName  
    ,DATEADD(day,ROW_NUMBER() OVER (ORDER BY  
        a.PostalCode),SYSDATETIME()) AS 'Row Number'  
FROM Sales.SalesPerson AS s   
    INNER JOIN Person.Person AS p   
        ON s.BusinessEntityID = p.BusinessEntityID  
    INNER JOIN Person.Address AS a   
        ON a.AddressID = p.BusinessEntityID  
WHERE TerritoryID IS NOT NULL   
    AND SalesYTD <> 0;  
```  
  
#### <a name="specifying-an-aggregate-window-function-as-number"></a>Spécification d'une fonction d'agrégation comme nombre  
L’exemple suivant utilise une fonction d’agrégation en tant qu’argument pour *nombre*.
  
```sql
SELECT SalesOrderID, ProductID, OrderQty  
    ,DATEADD(day,SUM(OrderQty)   
        OVER(PARTITION BY SalesOrderID),SYSDATETIME()) AS 'Total'  
FROM Sales.SalesOrderDetail   
WHERE SalesOrderID IN(43659,43664);  
GO  
```  
  
  
## <a name="see-also"></a>Voir aussi
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  



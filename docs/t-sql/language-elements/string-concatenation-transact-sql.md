---
title: "+ (Concaténation de chaînes) (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 12/06/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- concatenation
- +
- string
dev_langs:
- TSQL
helpviewer_keywords:
- concatenation [SQL Server]
- string concatenation operators
- + (string concatenation)
ms.assetid: 35cb3d7a-48f5-4b13-926c-a9d369e20ed7
caps.latest.revision: 51
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 66f482d424c6be56d89e8ec5b99cff30b2ddab0b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="-string-concatenation-transact-sql"></a>+ (Concaténation de chaîne) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Opérateur dans une expression de chaîne qui concatène des chaînes binaires ou des chaînes de deux caractères ou plus, des colonnes ou une combinaison de chaînes et de noms de colonnes, pour former une seule expression (un opérateur chaîne).  Par exemple `SELECT 'book'+'case';` retourne `bookcase`.
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
expression + expression  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Valide [expression](../../t-sql/language-elements/expressions-transact-sql.md) de tout des données de type de caractère ou de la catégorie de type de données binaires, sauf le **image**, **ntext**, ou **texte** des types de données. Les deux expressions doivent être de même type de données, ou l'une des expressions doit pouvoir être implicitement convertie dans le type de données de l'autre expression.  
  
 Pour concaténer des chaînes binaires et tout caractère compris entre ces chaînes, il faut utiliser une conversion explicite en données de type caractère. L’exemple suivant montre quand `CONVERT`, ou `CAST`, doit être utilisé avec une concaténation binaire et à quel moment `CONVERT`, ou `CAST`, ne doit pas être utilisé.  
  
```  
DECLARE @mybin1 varbinary(5), @mybin2 varbinary(5)  
SET @mybin1 = 0xFF  
SET @mybin2 = 0xA5  
-- No CONVERT or CAST function is required because this example   
-- concatenates two binary strings.  
SELECT @mybin1 + @mybin2  
-- A CONVERT or CAST function is required because this example  
-- concatenates two binary strings plus a space.  
SELECT CONVERT(varchar(5), @mybin1) + ' '   
   + CONVERT(varchar(5), @mybin2)  
-- Here is the same conversion using CAST.  
SELECT CAST(@mybin1 AS varchar(5)) + ' '   
   + CAST(@mybin2 AS varchar(5))  
  
```  
  
## <a name="result-types"></a>Types des résultats  
 Retourne le type de données de l'argument dont la priorité est la plus élevée. Pour plus d’informations, consultez [Priorités des types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Notes  
 L'opérateur + (Concaténation de chaîne) se comporte différemment selon qu'il est utilisé avec une chaîne vide et de longueur nulle ou avec des valeurs NULL. Une chaîne de caractères de longueur nulle peut être spécifiée par deux guillemets simples sans caractères à l'intérieur. Une chaîne binaire de longueur nulle peut être spécifiée par 0x sans aucune valeur d'octet dans la constante hexadécimale. La concaténation d'une chaîne de longueur nulle concatène toujours deux chaînes spécifiées. Lorsque vous opérez avec des chaînes dont la valeur est NULL, le résultat de la concaténation est fonction des paramètres de la session. De même que pour les opérations arithmétiques réalisées sur des valeurs NULL, l'ajout d'une valeur NULL à une valeur connue se solde généralement par une valeur inconnue. Une concaténation de chaînes effectuée avec une valeur NULL doit produire un résultat du même type. Toutefois, vous pouvez modifier ce comportement en modifiant le paramètre de `CONCAT_NULL_YIELDS_NULL` pour la session active. Pour plus d’informations, consultez [SET CONCAT_NULL_YIELDS_NULL &#40;Transact-SQL&#41;](../../t-sql/statements/set-concat-null-yields-null-transact-sql.md).  
  
 Si le résultat de la concaténation de chaînes dépasse la limite des 8 000 octets, il sera tronqué. Néanmoins, si au moins une des chaînes concaténées est de type valeur élevée, le résultat n'est pas tronqué.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-string-concatenation"></a>A. Utilisation de la concaténation de chaîne  
 L'exemple suivant crée une seule colonne sous l'en-tête `Name` à partir de plusieurs colonnes de caractères, avec le nom de famille de la personne suivi d'une virgule, d'un espace puis de son prénom. Le jeu de résultats est classé par ordre alphabétique croissant sur le nom de famille puis sur le prénom.  
  
```  
-- Uses AdventureWorks  
  
SELECT (LastName + ', ' + FirstName) AS Name  
FROM Person.Person  
ORDER BY LastName ASC, FirstName ASC;  
```  
  
### <a name="b-combining-numeric-and-date-data-types"></a>B. Combinaison des types de données numérique et date  
 L’exemple suivant utilise le `CONVERT` (fonction) pour concaténer **numérique** et **date** des types de données.  
  
```  
-- Uses AdventureWorks  
  
SELECT 'The order is due on ' + CONVERT(varchar(12), DueDate, 101)  
FROM Sales.SalesOrderHeader  
WHERE SalesOrderID = 50001;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `------------------------------------------------`  
  
 `The order is due on 04/23/2007`  
  
 `(1 row(s) affected)`  
  
### <a name="c-using-multiple-string-concatenation"></a>C. Utilisation de la concaténation de plusieurs chaînes  
 L'exemple suivant concatène plusieurs chaînes pour constituer une chaîne longue et afficher le nom de famille et l'initiale des vice-présidents [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)]. Le nom de famille est suivi d'une virgule ; l'initiale est suivie d'un point.  
  
```  
-- Uses AdventureWorks  
  
SELECT (LastName + ',' + SPACE(1) + SUBSTRING(FirstName, 1, 1) + '.') AS Name, e.JobTitle  
FROM Person.Person AS p  
    JOIN HumanResources.Employee AS e  
    ON p.BusinessEntityID = e.BusinessEntityID  
WHERE e.JobTitle LIKE 'Vice%'  
ORDER BY LastName ASC;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Name               Title`  
  
 `-------------      ---------------`  
  
 `Duffy, T.          Vice President of Engineering`  
  
 `Hamilton, J.       Vice President of Production`  
  
 `Welcker, B.        Vice President of Sales`  
  
 `(3 row(s) affected)`  
 
### <a name="d-using-large-strings-in-concatenation"></a>D. À l’aide de chaînes de grande taille dans la concaténation
L’exemple suivant concatène plusieurs chaînes pour former une chaîne longue et tente ensuite de calculer la longueur de la chaîne finale. La longueur finale du jeu de résultats est 16000, car l’expression d’évaluation commence gauche qui plus est, @x + @z + @y = > (@x + @z) + @y. Dans ce cas, le résultat de (@x + @z) est tronquée à 8 000 octets, puis @y est ajouté au jeu de résultats, ce qui rend la longueur de la chaîne finale 16000. Étant donné que @y est une chaîne de type de valeur élevée, la troncation n’a pas lieu.

```
DECLARE @x varchar(8000) = replicate('x', 8000)
DECLARE @y varchar(max) = replicate('y', 8000)
DECLARE @z varchar(8000) = replicate('z',8000)
SET @y = @x + @z + @y
-- The result of following select is 16000
SELECT len(@y) AS y
GO
```
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `y      `  
  
 `-------`  
  
 `16000`  
  
  `(1 row(s) affected)`  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-string-concatenation"></a>E. Utilisation de la concaténation de chaîne  
 L’exemple suivant crée une seule colonne sous l’en-tête de colonne `Name` à partir de colonnes de plusieurs caractères, avec le nom de famille du contact suivi par une virgule, un espace, puis le prénom du contact. Le jeu de résultats est classé par ordre alphabétique croissant sur le nom de famille puis sur le prénom.  
  
```  
-- Uses AdventureWorks  
  
SELECT (LastName + ', ' + FirstName) AS Name  
FROM DimEmployee  
ORDER BY LastName ASC, FirstName ASC;  
```  
  
### <a name="f-using-multiple-string-concatenation"></a>F. Utilisation de la concaténation de plusieurs chaînes  
 L’exemple suivant concatène plusieurs chaînes pour former une chaîne longue pour afficher le nom et l’initiale des vice-présidents au sein d’une base de données exemple. Le nom de famille est suivi d'une virgule ; l'initiale est suivie d'un point.  
  
```  
-- Uses AdventureWorks  
  
SELECT (LastName + ', ' + SUBSTRING(FirstName, 1, 1) + '.') AS Name, Title  
FROM DimEmployee  
WHERE Title LIKE '%Vice Pres%'  
ORDER BY LastName ASC;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Name               Title                                           
-------------      ---------------  
Duffy, T.          Vice President of Engineering  
Hamilton, J.       Vice President of Production  
Welcker, B.        Vice President of Sales  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CAST et CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Conversion de Type de données &#40; moteur de base de données &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)   
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Expressions &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Fonctions intégrées &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [Opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [+= &#40; Concaténation de chaînes &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/string-concatenation-equal-transact-sql.md)  
  
  





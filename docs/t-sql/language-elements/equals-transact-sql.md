---
title: = (Est égal à) (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/06/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- =
- = (Equals)
- Equals
- =_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- equals operator (=)
- = (equals operator)
ms.assetid: 18885245-5f55-4831-8f0b-7f2a3e82e246
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a08dbc63f765b436d9f6bb56be6456f197217db8
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68075268"
---
# <a name="-equals-transact-sql"></a>= (Equals) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Compare l'égalité de deux expressions (opérateur de comparaison) dans [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression = expression  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Toute [expression](../../t-sql/language-elements/expressions-transact-sql.md) valide. Si les expressions n'ont pas le même type de données, le type de données d'une expression doit être implicitement convertible dans le type de données de l'autre. La conversion se base sur les règles de [priorité des types de données](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="result-types"></a>Types des résultats  
 Boolean  
  
## <a name="remarks"></a>Notes  
 Quand vous effectuez une comparaison à l’aide d’une expression NULL, le résultat dépend du paramètre `ANSI_NULLS` :  
  
-   Si `ANSI_NULLS` a la valeur ON, le résultat de toute comparaison avec la valeur NULL est UNKNOWN, conformément à la convention ANSI selon laquelle NULL est une valeur inconnue qui ne peut être comparée à aucune autre valeur, notamment d’autres valeurs NULL.  
  
-   Si `ANSI_NULLS` a la valeur OFF, le résultat de la comparaison de NULL à NULL est TRUE, et le résultat de la comparaison de NULL à toute autre valeur est FALSE.  

Pour plus d’informations, consultez [SET ANSI_NULLS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-nulls-transact-sql.md).
  
 Une expression booléenne ayant pour résultat UNKNOWN se comporte de manière similaire à FALSE dans la plupart des cas, mais pas tous. Pour plus d’informations, consultez [NULL et UNKNOWN &#40;Transact-SQL&#41;](../../t-sql/language-elements/null-and-unknown-transact-sql.md) et [NOT &#40;Transact-SQL&#41;](../../t-sql/language-elements/not-transact-sql.md).  
  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using--in-a-simple-query"></a>R. Utilisation de = dans une requête simple  
 L'exemple suivant utilise l'opérateur d'égalité pour retourner toutes les lignes de la table `HumanResources.Department` dans lesquelles la valeur de la colonne `GroupName` est égale au mot « Manufacturing ».  
  
```  
-- Uses AdventureWorks  
  
SELECT DepartmentID, Name  
FROM HumanResources.Department  
WHERE GroupName = 'Manufacturing';  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
DepartmentID Name  
------------ --------------------------------------------------  
7            Production  
8            Production Control  
  
(2 row(s) affected)  
  
```  
  
### <a name="b-comparing-null-and-non-null-values"></a>B. Comparaison des valeurs NULL et non NULL  
 L'exemple ci-dessous utilise les opérateurs de comparaison Égal à (`=`) et Différent de (`<>`) pour effectuer une comparaison avec des valeurs `NULL` et non NULL dans une table. Il montre également que l’option `IS NULL` n’est pas influencée par le paramètre `SET ANSI_NULLS`.  
  
```  
-- Create table t1 and insert 3 rows.  
CREATE TABLE dbo.t1 (a INT NULL);  
INSERT INTO dbo.t1 VALUES (NULL),(0),(1);  
GO  
  
-- Print message and perform SELECT statements.  
PRINT 'Testing default setting';  
DECLARE @varname int;   
SET @varname = NULL;  
  
SELECT a  
FROM t1   
WHERE a = @varname;  
  
SELECT a   
FROM t1   
WHERE a <> @varname;  
  
SELECT a   
FROM t1   
WHERE a IS NULL;  
GO  
  
-- SET ANSI_NULLS to ON and test.  
PRINT 'Testing ANSI_NULLS ON';  
SET ANSI_NULLS ON;  
GO  
DECLARE @varname int;  
SET @varname = NULL  
  
SELECT a   
FROM t1   
WHERE a = @varname;  
  
SELECT a   
FROM t1   
WHERE a <> @varname;  
  
SELECT a   
FROM t1   
WHERE a IS NULL;  
GO  
  
-- SET ANSI_NULLS to OFF and test.  
PRINT 'Testing SET ANSI_NULLS OFF';  
SET ANSI_NULLS OFF;  
GO  
DECLARE @varname int;  
SET @varname = NULL;  
SELECT a   
FROM t1   
WHERE a = @varname;  
  
SELECT a   
FROM t1   
WHERE a <> @varname;  
  
SELECT a   
FROM t1   
WHERE a IS NULL;  
GO  
  
-- Drop table t1.  
DROP TABLE dbo.t1;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Testing default setting  
a  
-----------  
NULL  
  
(1 row(s) affected)  
  
a  
-----------  
0  
1  
  
(2 row(s) affected)  
  
a  
-----------  
NULL  
  
(1 row(s) affected)  
  
Testing ANSI_NULLS ON  
a  
-----------  
  
(0 row(s) affected)  
  
a  
-----------  
  
(0 row(s) affected)  
  
a  
-----------  
NULL  
  
(1 row(s) affected)  
  
Testing SET ANSI_NULLS OFF  
a  
-----------  
NULL  
  
(1 row(s) affected)  
  
a  
-----------  
0  
1  
  
(2 row(s) affected)  
  
a  
-----------  
NULL  
  
(1 row(s) affected)  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Opérateurs &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  

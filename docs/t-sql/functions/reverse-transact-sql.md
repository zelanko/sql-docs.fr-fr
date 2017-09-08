---
title: REVERSE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- REVERSE_TSQL
- REVERSE
dev_langs:
- TSQL
helpviewer_keywords:
- expressions [SQL Server], reverse
- REVERSE function
- reverse character expressions
ms.assetid: 555d8877-7cc7-4955-ae2c-6215aca313b7
caps.latest.revision: 46
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8696a2cff3589b9b756e2ddd9cc1160b465b70d8
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="reverse-transact-sql"></a>REVERSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne l'ordre inverse d'une valeur de chaîne.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
REVERSE ( string_expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *string_expression*  
 *string_expression* est un [expression](../../t-sql/language-elements/expressions-transact-sql.md) d’un type de données binaire ou chaîne. *string_expression* peut être une constante, une variable ou une colonne de données binaire ou caractère.  
  
## <a name="return-types"></a>Types de retour  
 **varchar** ou **nvarchar**  
  
## <a name="remarks"></a>Notes  
 *string_expression* doit être de type de données qui est implicitement convertible en **varchar**. Sinon, utilisez [CAST](../../t-sql/functions/cast-and-convert-transact-sql.md) pour convertir explicitement *string_expression*.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Caractères supplémentaires (paires de substitution)  
 Lors de l'utilisation de classements SC, la fonction REVERSE n'inversera pas l'ordre de deux moitiés d'une paire de substitution.  
  
## <a name="examples"></a>Exemples  
 Cet exemple renvoie le prénom de tous les contacts avec inversion des caractères. Cet exemple utilise la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
SELECT FirstName, REVERSE(FirstName) AS Reverse  
FROM Person.Person  
WHERE BusinessEntityID < 5  
ORDER BY FirstName;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `FirstName      Reverse`  
  
 `-------------- --------------`  
  
 `Ken            neK`  
  
 `Rob            boR`  
  
 `Roberto        otreboR`  
  
 `Terri          irreT`  
  
 `(4 row(s) affected)`  
  
 L'exemple suivant inverse les caractères dans une variable.  
  
```  
DECLARE @myvar varchar(10);  
SET @myvar = 'sdrawkcaB';  
SELECT REVERSE(@myvar) AS Reversed ;  
GO  
```  
  
 L’exemple suivant effectue une conversion implicite d’un **int** de type de données dans **varchar** type de données et inverse le résultat.  
  
```  
SELECT REVERSE(1234) AS Reversed ;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L’exemple suivant retourne les noms de toutes les bases de données et les noms avec les caractères inversé.  
  
```  
SELECT name, REVERSE(name) FROM sys.databases;  
GO  
```  
  
 L'exemple suivant inverse les caractères dans une variable.  
  
```  
DECLARE @myvar varchar(10);  
SET @myvar = 'sdrawkcaB';  
SELECT REVERSE(@myvar) AS Reversed ;  
GO  
```  
  
 L’exemple suivant effectue une conversion implicite d’un **int** de type de données dans **varchar** type de données et inverse le résultat.  
  
```  
SELECT REVERSE(1234) AS Reversed ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CAST et CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Fonctions de chaîne &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  



---
title: GAUCHE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- LEFT
- LEFT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- character strings [SQL Server], LEFT
- characters [SQL Server], leftmost
- LEFT function
- leftmost character of expression
ms.assetid: 44a8c71b-63d8-458b-8b5d-99d570067c3c
caps.latest.revision: 48
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0b0ec58ed9e8bbaae6f4f4ae90834f415476b039
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="left-transact-sql"></a>LEFT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne la partie de gauche d'une chaîne de caractères avec le nombre spécifié de caractères.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
LEFT ( character_expression , integer_expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *character_expression*  
 Est un [expression](../../t-sql/language-elements/expressions-transact-sql.md) de type binaire ou caractère. *character_expression* peut être une constante, une variable ou une colonne. *character_expression* peut être de n’importe quel type de données, à l’exception de **texte** ou **ntext**, qui peut être converti implicitement en **varchar** ou **nvarchar**. Sinon, utilisez le [CAST](../../t-sql/functions/cast-and-convert-transact-sql.md) fonction pour convertir explicitement *character_expression*.  
  
 *integer_expression*  
 Est un entier positif qui spécifie le nombre de caractères de la *character_expression* sera retourné. Si *expression_entier* est négatif, une erreur est retournée. Si *expression_entier* est de type **bigint** et contient une valeur élevée, *character_expression* doit être d’un type de données de grande taille, tel que **varchar (max)**.  
  
 Le *expression_entier* paramètre compte un caractère de substitution UTF-16 comme un caractère.  
  
## <a name="return-types"></a>Types de retour  
 Retourne **varchar** lorsque *character_expression* est un type de données de caractères non-Unicode.  
  
 Retourne **nvarchar** lorsque *character_expression* est un type de données de caractères Unicode.  
  
## <a name="remarks"></a>Notes  
 Lors de l’utilisation de classements SC, la *expression_entier* paramètre compte une paire de substitution UTF-16 comme un caractère. Pour plus d’informations, consultez [Prise en charge d’Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-left-with-a-column"></a>A. Utilisation de LEFT avec une colonne  
 L'exemple suivant retourne les cinq caractères les plus à gauche de chaque nom de produit dans la table `Product` de la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
SELECT LEFT(Name, 5)   
FROM Production.Product  
ORDER BY ProductID;  
GO  
```  
  
### <a name="b-using-left-with-a-character-string"></a>B. Utilisation de LEFT avec une chaîne de caractères  
 L'exemple suivant utilise `LEFT` pour retourner les deux caractères les plus à gauche de la chaîne de caractères `abcdefg`.  
  
```  
SELECT LEFT('abcdefg',2);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--   
ab   
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-left-with-a-column"></a>C. Utilisation de LEFT avec une colonne  
 L'exemple suivant retourne les cinq caractères les plus à gauche du nom de chaque produit.  
  
```  
-- Uses AdventureWorks  
  
SELECT LEFT(EnglishProductName, 5)   
FROM dbo.DimProduct  
ORDER BY ProductKey;  
```  
  
### <a name="d-using-left-with-a-character-string"></a>D. Utilisation de LEFT avec une chaîne de caractères  
 L'exemple suivant utilise `LEFT` pour retourner les deux caractères les plus à gauche de la chaîne de caractères `abcdefg`.  
  
```  
-- Uses AdventureWorks  
  
SELECT LEFT('abcdefg',2) FROM dbo.DimProduct;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--   
ab  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CAST et CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Fonctions de chaîne &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  



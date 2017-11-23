---
title: "&gt;(Supérieur à) (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Greater
- Than
- '> (Greater Than)'
- '>_TSQL'
- Greater Than
- '>'
dev_langs: TSQL
helpviewer_keywords:
- greater than operator (>)
- '> (greater than operator)'
ms.assetid: 50a7b098-a3fb-4df6-ae42-1272d6346338
caps.latest.revision: "37"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 5ca1c189b4548175fd1038b2c83bed87d768a776
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="gt-greater-than-transact-sql"></a>&gt;(Supérieur à) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Compare deux expressions (opérateur de comparaison) dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Lorsque vous comparez des expressions non nulles, le résultat est TRUE si l'opérande de gauche a une valeur plus élevée que celui de droite. Si tel n'est pas le cas, le résultat est FALSE. Si un ou les deux opérandes ont la valeur NULL, consultez la rubrique [SET ANSI_NULLS &#40; Transact-SQL &#41; ](../../t-sql/statements/set-ansi-nulls-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression > expression  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Valide [expression](../../t-sql/language-elements/expressions-transact-sql.md). Les deux expressions doivent avoir des types de données implicitement convertibles. La conversion dépend des règles de [priorité des types de données](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="result-types"></a>Types des résultats  
 **Booléen**  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using--in-a-simple-query"></a>A. À l’aide de > dans une requête simple  
 L'exemple suivant retourne toutes les lignes de la table `HumanResources.Department` qui ont une valeur dans `DepartmentID` supérieure à la valeur 13.  
  
```  
--Uses AdventureWorks  
  
SELECT DepartmentID, Name  
FROM HumanResources.Department  
WHERE DepartmentID > 13  
ORDER BY DepartmentID;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
DepartmentID Name  
------------ --------------------------------------------------  
14           Facilities and Maintenance  
15           Shipping and Receiving  
16           Executive  
  
(3 row(s) affected)  
  
```  
  
### <a name="b-using--to-compare-two-variables"></a>B. À l’aide de > pour comparer deux variables  
  
```  
DECLARE @a int = 45, @b int = 40;  
SELECT IIF ( @a > @b, 'TRUE', 'FALSE' ) AS Result;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
------  
TRUE  
  
(1 row(s) affected)  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IIF &#40; Transact-SQL &#41;](../../t-sql/functions/logical-functions-iif-transact-sql.md)   
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  

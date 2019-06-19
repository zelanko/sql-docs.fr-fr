---
title: '&gt;= (Supérieur ou égal à) (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Greater
- '>='
- '>= (Greater Than or Equal To)'
- Equal To
- '>=_TSQL'
- Greater Than
- Equal
dev_langs:
- TSQL
helpviewer_keywords:
- greater than or equal to operator (>=)
- '>= (greater than or equal to operator)'
ms.assetid: 641ee28d-7536-46dd-a48a-6c63c2d59278
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 721a7795f027e3641e3a8f5ab2c740e17c9cff57
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65982282"
---
# <a name="gt-greater-than-or-equal-to-transact-sql"></a>&gt;= (Supérieur ou égal à) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Compare deux expressions avec l'opérateur de comparaison supérieur ou égal à.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression >= expression  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Toute [expression](../../t-sql/language-elements/expressions-transact-sql.md) valide. Les deux expressions doivent avoir des types de données implicitement convertibles. La conversion dépend des règles de [priorité des types de données](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="result-types"></a>Types des résultats  
 Booléen  
  
## <a name="remarks"></a>Notes  
 Lorsque vous comparez des expressions de valeur non NULL, le résultat est TRUE si l'opérande de gauche a une valeur supérieure ou égale à celui de droite ; si tel n'est pas le cas, le résultat est FALSE.  
  
 Contrairement à l’opérateur de comparaison = (égalité), le résultat de la comparaison >= de deux valeurs NULL ne dépend pas du paramètre ANSI_NULLS.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using--in-a-simple-query"></a>A. Utilisation de >= dans une requête simple  
 L'exemple suivant retourne toutes les lignes de la table `HumanResources.Department` qui ont une valeur dans `DepartmentID` supérieure ou égale à la valeur 13.  
  
```  
-- Uses AdventureWorks  
  
SELECT DepartmentID, Name  
FROM HumanResources.Department  
WHERE DepartmentID >= 13  
ORDER BY DepartmentID;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
DepartmentID Name  
------------ --------------------------------------------------  
13           Quality Assurance  
14           Facilities and Maintenance  
15           Shipping and Receiving  
16           Executive  
  
(4 row(s) affected)  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [= &#40;Equals&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/equals-transact-sql.md)   
 [&#62; &#40;Supérieur à&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/greater-than-transact-sql.md)   
 [Opérateurs &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  

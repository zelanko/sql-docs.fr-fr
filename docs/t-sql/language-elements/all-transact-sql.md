---
title: Toutes les (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server (starting with 2008)
f1_keywords:
- ALL_TSQL
- ALL
dev_langs:
- TSQL
helpviewer_keywords:
- single-column set of values [SQL Server]
- ALL (Transact-SQL)
ms.assetid: 4b0c002e-1ffd-4425-a980-11fdc1f24af7
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1fd1b250a30b83a3b014384aafee6c40ff4f1a5a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="all-transact-sql"></a>ALL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Compare une valeur scalaire avec un ensemble de valeurs appartenant à une seule colonne.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
scalar_expression { = | <> | != | > | >= | !> | < | <= | !< } ALL ( subquery )  
```  
  
## <a name="arguments"></a>Arguments  
 *scalar_expression*  
 Valide [expression](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 { = | <> | != | > | >= | !> | < | <= | !< }  
 Est un opérateur de comparaison.  
  
 *sous-requête*  
 Sous-requête dont le jeu de résultats est une colonne. Le type de données de la colonne renvoyée doit être le même type de données en tant que type de données de *scalar_expression*.  
  
 Instruction SELECT limitée, dans laquelle les clauses ORDER BY et le mot clé INTO ne sont pas autorisés.  
  
## <a name="result-types"></a>Types des résultats  
 **Booléen**  
  
## <a name="result-value"></a>Valeur des résultats  
 Retourne la valeur TRUE lorsque la comparaison spécifiée est vraie pour toutes les paires (*scalar_expression***,***x)*, lorsque *x* est une valeur dans le jeu de colonnes uniques ; sinon, retourne FALSE.  
  
## <a name="remarks"></a>Notes  
 ALL requiert le *scalar_expression* corresponde à toutes les valeurs retournées par la sous-requête. Par exemple, si la sous-requête retourne les valeurs 2 et 3, *scalar_expression* < = ALL (sous-requête) serait équivalente à TRUE pour une *scalar_expression* 2. Si la sous-requête retourne les valeurs 2 et 3, *scalar_expression* = ALL (sous-requête) donne FALSE comme résultat, car certaines valeurs de la sous-requête (la valeur 3) ne répondent pas aux critères de l’expression.  
  
 Pour les instructions qui nécessitent le *scalar_expression* corresponde à une seule valeur est retournée par la sous-requête, consultez [certaines &#124; &#40; Transact-SQL &#41; ](../../t-sql/language-elements/some-any-transact-sql.md).  
  
 Cette rubrique fait référence à l'instruction ALL lorsqu'elle est utilisée avec une sous-requête. ALL peut également être utilisé avec [UNION](../../t-sql/language-elements/set-operators-union-transact-sql.md) et [sélectionnez](../../t-sql/queries/select-transact-sql.md).  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant crée une procédure stockée qui détermine si tous les composants d’un `SalesOrderID` dans les [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] base de données peut être fabriqué dans le nombre de jours spécifié. L'exemple utilise une sous-requête pour créer une liste du nombre de `DaysToManufacture` pour tous les composants du `SalesOrderID` spécifié, puis vérifie que toutes les valeurs `DaysToManufacture` sont inférieures ou égales au nombre de jours spécifié.  
  
```  
-- Uses AdventureWorks  
  
CREATE PROCEDURE DaysToBuild @OrderID int, @NumberOfDays int  
AS  
IF   
@NumberOfDays >= ALL  
   (  
    SELECT DaysToManufacture  
    FROM Sales.SalesOrderDetail  
    JOIN Production.Product   
    ON Sales.SalesOrderDetail.ProductID = Production.Product.ProductID   
    WHERE SalesOrderID = @OrderID  
   )  
PRINT 'All items for this order can be manufactured in specified number of days or less.'  
ELSE   
PRINT 'Some items for this order cannot be manufactured in specified number of days or less.' ;  
  
```  
  
 Pour tester la procédure, exécutez-la en utilisant le `SalesOrderID 49080` dont l'un des composants demande `2` jours de fabrication, tandis que les 2 autres en demandent 0. La première instruction ci-dessous remplit les critères, mais pas la deuxième.  
  
```  
EXECUTE DaysToBuild 49080, 2 ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `All items for this order can be manufactured in specified number of days or less.`  
  
```  
EXECUTE DaysToBuild 49080, 1 ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Some items for this order cannot be manufactured in specified number of days or less.`  
  
## <a name="see-also"></a>Voir aussi  
 [CAS &#40; Transact-SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [Expressions &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Fonctions intégrées &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [COMME &#40; Transact-SQL &#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [Opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [OÙ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)   
 [IN &#40; Transact-SQL &#41;](../../t-sql/language-elements/in-transact-sql.md)  
  
  


---
title: "CERTAINS | N’importe quel (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server (starting with 2008)
f1_keywords:
- SOME
- SOME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- scalar values
- comparing scalar with single-column set
- ANY operator
- SOME | ANY keyword
- single-column set of values [SQL Server]
ms.assetid: 1f717ad6-f67b-4980-9397-577ecb0e5789
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a67801d62cb05cdb0b589548e8bd3f9676d5840a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="some--any-transact-sql"></a>SOME | ANY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Compare une valeur scalaire avec un ensemble de valeurs appartenant à une seule colonne. SOME et ANY sont équivalents.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
scalar_expression { = | < > | ! = | > | > = | ! > | < | < = | ! < }   
     { SOME | ANY } ( subquery )   
```  
  
## <a name="arguments"></a>Arguments  
 *scalar_expression*  
 Valide [expression](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 { = | <> | != | > | >= | !> | < | <= | !< }  
 Tout opérateur de comparaison valide.  
  
 SOME | ANY  
 Spécifie qu'il convient d'effectuer une comparaison.  
  
 *sous-requête*  
 Sous-requête avec un jeu de résultats d'une colonne. Le type de données de la colonne retournée doit être le même type de données en tant que *scalar_expression*.  
  
## <a name="result-types"></a>Types des résultats  
 **Booléen**  
  
## <a name="result-value"></a>Valeur des résultats  
 CERTAINS ou tous les retours **TRUE** lorsque la comparaison spécifiée a la valeur TRUE pour n’importe quelle paire (*scalar_expression***,***x*) où *x* est une valeur dans le jeu de colonnes uniques ; sinon, retourne **FALSE**.  
  
## <a name="remarks"></a>Notes  
 SOME requiert le *scalar_expression* corresponde au moins une valeur retournée par la sous-requête. Pour les instructions qui nécessitent le *scalar_expression* corresponde à toutes les valeurs retournées par la sous-requête, consultez [tous les &#40; Transact-SQL &#41; ](../../t-sql/language-elements/all-transact-sql.md). Par exemple, si la sous-requête retourne les valeurs 2 et 3, *scalar_expression* = SOME (sous-requête) serait équivalente à TRUE pour une *scalar_express* de 2. Si la sous-requête retourne les valeurs 2 et 3, *scalar_expression* = ALL (sous-requête) donne FALSE comme résultat, car certaines valeurs de la sous-requête (la valeur 3) ne répondent pas aux critères de l’expression.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-running-a-simple-example"></a>A. Exécution d'un exemple simple  
 Les instructions suivantes créent une table simple et ajoutent les valeurs `1`, `2`, `3` et `4` à la colonne `ID`.  
  
```  
CREATE TABLE T1  
(ID int) ;  
GO  
INSERT T1 VALUES (1) ;  
INSERT T1 VALUES (2) ;  
INSERT T1 VALUES (3) ;  
INSERT T1 VALUES (4) ;  
```  
  
 La requête suivante renvoie `TRUE` car `3` est inférieur à certaines des valeurs de la table.  
  
```  
IF 3 < SOME (SELECT ID FROM T1)  
PRINT 'TRUE'   
ELSE  
PRINT 'FALSE' ;  
```  
  
 La requête suivante renvoie `FALSE` car `3` n'est pas inférieur à toutes les valeurs de la table.  
  
```  
IF 3 < ALL (SELECT ID FROM T1)  
PRINT 'TRUE'   
ELSE  
PRINT 'FALSE' ;  
```  
  
### <a name="b-running-a-practical-example"></a>B. Exécution d'un exemple pratique  
 L’exemple suivant crée une procédure stockée qui détermine si tous les composants d’un `SalesOrderID` dans les `AdventureWorks2012` base de données peut être fabriqué dans le nombre de jours spécifié. L'exemple utilise une sous-requête pour créer une liste du nombre de `DaysToManufacture` pour tous les composants du `SalesOrderID` spécifié, puis vérifie si parmi les valeurs retournées par la sous-requête certaines sont supérieures au nombre de jours spécifié. Si chaque valeur retournée pour `DaysToManufacture` est inférieure au nombre fourni, la condition a la valeur TRUE et le premier message est imprimé.  
  
```  
-- Uses AdventureWorks  
  
CREATE PROCEDURE ManyDaysToComplete @OrderID int, @NumberOfDays int  
AS  
IF   
@NumberOfDays < SOME  
   (  
    SELECT DaysToManufacture  
    FROM Sales.SalesOrderDetail  
    JOIN Production.Product   
    ON Sales.SalesOrderDetail.ProductID = Production.Product.ProductID   
    WHERE SalesOrderID = @OrderID  
   )  
PRINT 'At least one item for this order cannot be manufactured in specified number of days.'  
ELSE   
PRINT 'All items for this order can be manufactured in the specified number of days or less.' ;  
  
```  
  
 Pour tester la procédure, exécutez la procédure à l’aide de la `SalesOrderID``49080`, qui a un composant qui nécessite `2` jours et les deux composants qui demandent 0. La première instruction remplit les critères, mais pas la deuxième.  
  
```  
EXECUTE ManyDaysToComplete 49080, 2 ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `All items for this order can be manufactured in the specified number of days or less.`  
  
```  
EXECUTE ManyDaysToComplete 49080, 1 ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `At least one item for this order cannot be manufactured in specified number of days.`  
  
## <a name="see-also"></a>Voir aussi  
 [Tous les &#40; Transact-SQL &#41;](../../t-sql/language-elements/all-transact-sql.md)   
 [CAS &#40; Transact-SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [Fonctions intégrées &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [Opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [OÙ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)   
 [IN &#40; Transact-SQL &#41;](../../t-sql/language-elements/in-transact-sql.md)  
  
  


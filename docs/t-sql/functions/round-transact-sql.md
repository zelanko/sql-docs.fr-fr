---
title: ROUND (Transact-SQL) | Documents Microsoft
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
- ROUND_TSQL
- ROUND
dev_langs:
- TSQL
helpviewer_keywords:
- rounding expressions
- ROUND function [Transact-SQL]
ms.assetid: 23921ed6-dd6a-4c9e-8c32-91c0d44fe4b7
caps.latest.revision: 40
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: cba8b5a9b62a21fc810ff9bb5fcd3d0c6429f9f5
ms.contentlocale: fr-fr
ms.lasthandoff: 10/17/2017

---
# <a name="round-transact-sql"></a>ROUND (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne une valeur numérique, arrondie à la longueur ou à la précision indiquée.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
ROUND ( numeric_expression , length [ ,function ] )  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ROUND (numeric_expression , length )  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression*  
 Est un [expression](../../t-sql/language-elements/expressions-transact-sql.md) de la catégorie, de type de données numérique approximatives ou à l’exception de la **bits** type de données.  
  
 *length*  
 Indique la précision avec laquelle *numeric_expression* doit être arrondie. *longueur* doit être une expression de type **tinyint**, **smallint**, ou **int**. Lorsque *longueur* est un nombre positif, *numeric_expression* est arrondi au nombre de décimales indiqué par *longueur*. Lorsque *longueur* est un nombre négatif, *numeric_expression* est arrondi à gauche de la virgule décimale, comme spécifié par *longueur*.  
  
 *function*  
 Type d'opération à effectuer. *fonction* doit être **tinyint**, **smallint**, ou **int**. Lorsque *fonction* est omis ou a la valeur 0 (valeur par défaut), *numeric_expression* est arrondi. Lorsqu’une valeur autre que 0 est spécifiée, *numeric_expression* est tronqué.  
  
## <a name="return-types"></a>Types de retour  
 Retourne les types de données suivants.  
  
|Résultat de l'expression|Type de retour|  
|-----------------------|-----------------|  
|**tinyint**|**int**|  
|**smallint**|**int**|  
|**int**|**int**|  
|**bigint**|**bigint**|  
|**décimal** et **numérique** catégorie (p, s)|**Decimal (p, s)**|  
|**Money** et **smallmoney** catégorie|**money**|  
|**float** et **réel** catégorie|**float**|  
  
## <a name="remarks"></a>Notes  
 ROUND retourne toujours une valeur. Si *longueur* est négative et supérieur au nombre de chiffres avant la virgule décimale, ROUND retourne 0.  
  
|Exemple|Résultat|  
|-------------|------------|  
|ROUND (748.58, -4)|0|  
  
 La fonction ROUND renvoie un arrondi *numeric_expression*, quel que soit le type de données, lors de la *longueur* est un nombre négatif.  
  
|Exemples|Résultat|  
|--------------|------------|  
|ROUND (748.58, -1)|750.00|  
|ROUND (748.58, -2)|700.00|  
|ROUND(748.58, -3)|Le résultat est un dépassement arithmétique car la valeur par défaut de 748.58 est une décimale (5,2) qui ne peut pas retourner 1000.00.|  
|Pour arrondir jusqu'à 4 chiffres, modifiez le type de données de l'entrée. Exemple :<br /><br /> `SELECT ROUND(CAST (748.58 AS decimal (6,2)),-3);`|1000.00|  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-round-and-estimates"></a>A. Utilisation de ROUND et des estimations  
 Cet exemple contient deux expressions qui montrent qu'avec `ROUND`, le dernier chiffre est toujours une estimation.  
  
```  
SELECT ROUND(123.9994, 3), ROUND(123.9995, 3);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------- -----------  
123.9990    124.0000      
```  
  
### <a name="b-using-round-and-rounding-approximations"></a>B. Utilisation de ROUND et des approximations d'arrondi  
 Cet exemple montre des arrondis et des approximations.  
  
```  
SELECT ROUND(123.4545, 2), ROUND(123.45, -2);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

 ```
--------  ----------
123.45    100.00
```
  
### <a name="c-using-round-to-truncate"></a>C. Utilisation de ROUND pour une troncature  
 Cet exemple utilise deux instructions `SELECT` pour démontrer la différence entre l'arrondi et la troncature. La première instruction arrondit le résultat. La seconde instruction tronque le résultat.  
  
```  
SELECT ROUND(150.75, 0);  
GO  
SELECT ROUND(150.75, 0, 1);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--------  
151.00  
  
(1 row(s) affected)  
  
--------  
150.00  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-round-and-estimates"></a>D. Utilisation de ROUND et des estimations  
 Cet exemple contient deux expressions qui montrent qu'avec `ROUND`, le dernier chiffre est toujours une estimation.  
  
```  
SELECT ROUND(123.994999, 3), ROUND(123.995444, 3);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

 ```
--------  ---------
123.995000    123.995444
```
  
## <a name="see-also"></a>Voir aussi  
 [PLAFOND &#40; Transact-SQL &#41;](../../t-sql/functions/ceiling-transact-sql.md)   
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Expressions &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [FLOOR &#40; Transact-SQL &#41;](../../t-sql/functions/floor-transact-sql.md)   
 [Fonctions mathématiques &#40; Transact-SQL &#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
  



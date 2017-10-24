---
title: RADIANS (Transact-SQL) | Documents Microsoft
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
- RADIANS
- RADIANS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- RADIANS function
ms.assetid: e9f69951-ecda-45d9-8909-dcb716b1b1c0
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 64c662ed806f5173c506756433318d589a42d4ea
ms.contentlocale: fr-fr
ms.lasthandoff: 10/17/2017

---
# <a name="radians-transact-sql"></a>RADIANS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne les radians lorsqu'une expression numérique, en degrés, est entrée.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
RADIANS ( numeric_expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression*  
 Est un [expression](../../t-sql/language-elements/expressions-transact-sql.md) de la catégorie, de type de données numérique approximatives ou à l’exception de la **bits** type de données.  
  
## <a name="return-types"></a>Types de retour  
 Retourne le même type que *numeric_expression*.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-radians-to-show-00"></a>A. Utilisation de RADIANS pour afficher 0.0  
 L'exemple suivant renvoie `0.0` comme résultat car l'expression numérique à convertir en radians est trop petite pour la fonction `RADIANS`.  
  
```  
SELECT RADIANS(1e-307)  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-------------------   
0.0                        
(1 row(s) affected)  
```  
  
### <a name="b-using-radians-to-return-the-equivalent-angle-of-a-float-expression"></a>B. Utilisation de la fonction RADIANS pour renvoyer l'angle équivalent à une expression de type float.  
 L'exemple suivant prend une expression `float` et renvoie la valeur en `RADIANS` de l'angle spécifié.  
  
```  
-- First value is -45.01.  
DECLARE @angle float  
SET @angle = -45.01  
SELECT 'The RADIANS of the angle is: ' +  
   CONVERT(varchar, RADIANS(@angle))  
GO  
-- Next value is -181.01.  
DECLARE @angle float  
SET @angle = -181.01  
SELECT 'The RADIANS of the angle is: ' +  
   CONVERT(varchar, RADIANS(@angle))  
GO  
-- Next value is 0.00.  
DECLARE @angle float  
SET @angle = 0.00  
SELECT 'The RADIANS of the angle is: ' +  
   CONVERT(varchar, RADIANS(@angle))  
GO  
-- Next value is 0.1472738.  
DECLARE @angle float  
SET @angle = 0.1472738  
SELECT 'The RADIANS of the angle is: ' +  
    CONVERT(varchar, RADIANS(@angle))  
GO  
-- Last value is 197.1099392.  
DECLARE @angle float  
SET @angle = 197.1099392  
SELECT 'The RADIANS of the angle is: ' +  
   CONVERT(varchar, RADIANS(@angle))  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
---------------------------------------   
The RADIANS of the angle is: -0.785573                        
(1 row(s) affected)  
---------------------------------------   
The RADIANS of the angle is: -3.15922                         
(1 row(s) affected)  
---------------------------------------   
The RADIANS of the angle is: 0                                
(1 row(s) affected)  
---------------------------------------   
The RADIANS of the angle is: 0.00257041                       
 (1 row(s) affected)  
---------------------------------------   
The RADIANS of the angle is: 3.44022                          
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CAST et CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Decimal et numeric &#40; Transact-SQL &#41;](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)   
 [float et real &#40; Transact-SQL &#41;](../../t-sql/data-types/float-and-real-transact-sql.md)   
 [int, bigint, smallint, tinyint et #40 ; Transact-SQL &#41;](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)   
 [Fonctions mathématiques &#40; Transact-SQL &#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)   
 [Money et smallmoney &#40; Transact-SQL &#41;](../../t-sql/data-types/money-and-smallmoney-transact-sql.md)  
  
  



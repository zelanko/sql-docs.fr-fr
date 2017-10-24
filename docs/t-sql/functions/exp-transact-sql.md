---
title: EXP (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- EXP_TSQL
- EXP
dev_langs:
- TSQL
helpviewer_keywords:
- exponential functions
- EXP function
ms.assetid: 5a9b8c52-6fb6-4e33-8b02-a878785b2f51
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c50757291a8f1fc3d58d8a9a131c4a24aa79a008
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="exp-transact-sql"></a>EXP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Renvoie la valeur exponentielle de l’objet **float** expression.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
EXP ( float_expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Est un [expression](../../t-sql/language-elements/expressions-transact-sql.md) de type **float** ou d’un type qui peut être implicitement converti en **float**.  
  
## <a name="return-types"></a>Types de retour  
 **float**  
  
## <a name="remarks"></a>Notes  
 La constante **e** (2,718281...), est la base du logarithme népérien.  
  
 L’exposant d’un nombre correspond à la constante **e** élevé à la puissance du nombre. Par exemple, EXP(1,0) = e^1,0 = 2,71828182845905 et EXP(10) = e^10 = 22026,4657948067.  
  
 La valeur exponentielle du logarithme naturel d’un nombre est le nombre lui-même : EXP (journal (*n*)) =  *n* . Le logarithme naturel de la valeur exponentielle d’un nombre est le nombre lui-même : journal (EXP (*n*)) =  *n* .  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-finding-the-exponent-of-a-number"></a>A. Calcul de l'exposant d'un nombre  
 L'exemple suivant déclare une variable et renvoie la valeur exponentielle de cette dernière (`10`), accompagnées d'un texte descriptif.  
  
```  
DECLARE @var float  
SET @var = 10  
SELECT 'The EXP of the variable is: ' + CONVERT(varchar,EXP(@var))  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------------------------------------------------------  
The EXP of the variable is: 22026.5  
(1 row(s) affected)  
```  
  
### <a name="b-finding-exponentials-and-natural-logarithms"></a>B. Calcul des valeurs exponentielles et logarithmes naturels  
 L'exemple suivant renvoie la valeur exponentielle du logarithme naturel de `20` et le logarithme naturel de la valeur exponentielle de `20`. Comme ces fonctions sont l'inverse l'une de l'autre, la valeur `20` est renvoyée dans les deux cas.  
  
```  
SELECT EXP( LOG(20)), LOG( EXP(20))  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
---------------------- ----------------------  
20                     20  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-finding-the-exponent-of-a-number"></a>C. Calcul de l'exposant d'un nombre  
 L’exemple suivant renvoie la valeur exponentielle de la valeur spécifiée (`10`).  
  
```  
SELECT EXP(10);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------  
22026.4657948067  
```  
  
### <a name="d-finding-exponential-values-and-natural-logarithms"></a>D. Valeurs exponentielles et logarithmes naturels  
 L'exemple suivant renvoie la valeur exponentielle du logarithme naturel de `20` et le logarithme naturel de la valeur exponentielle de `20`. Comme ces fonctions sont l'inverse l'une de l'autre, la valeur `20` est renvoyée dans les deux cas.  
  
```  
SELECT EXP( LOG(20)), LOG( EXP(20));  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-------------- -----------------  
20                  20  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions mathématiques &#40; Transact-SQL &#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)   
 [JOURNAL &#40; Transact-SQL &#41;](../../t-sql/functions/log-transact-sql.md)   
 [LOG10 &#40; Transact-SQL &#41;](../../t-sql/functions/log10-transact-sql.md)  
  
  



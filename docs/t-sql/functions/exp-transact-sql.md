---
title: EXP (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
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
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 638e9960af007710b7c9a891109597db14227092
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68071593"
---
# <a name="exp-transact-sql"></a>EXP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Renvoie la valeur exponentielle de l’expression **float** spécifiée.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
EXP ( float_expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *float_expression*  
 [Expression](../../t-sql/language-elements/expressions-transact-sql.md) de type **float** ou dont le type peut être implicitement converti en type **float**.  
  
## <a name="return-types"></a>Types de retour  
 **float**  
  
## <a name="remarks"></a>Notes  
 La constante **e** (2,718281…), est la base des logarithmes naturels.  
  
 L’exposant d’un nombre correspond à la constante **e** élevée à la puissance de ce nombre. Par exemple, EXP(1,0) = e^1,0 = 2,71828182845905 et EXP(10) = e^10 = 22026,4657948067.  
  
 La valeur exponentielle du logarithme népérien d’un nombre est le nombre lui-même : EXP (LOG (*n*)) = *n*. De même, le logarithme népérien de la valeur exponentielle d’un nombre est le nombre lui-même : LOG (EXP (*n*)) = *n*.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-finding-the-exponent-of-a-number"></a>R. Calcul de l'exposant d'un nombre  
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
  
## <a name="examples-sssdwfull-and-sspdw"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
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
  
### <a name="d-finding-exponential-values-and-natural-logarithms"></a>D. Calcul des valeurs exponentielles et des logarithmes népériens  
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
 [Fonctions mathématiques &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)   
 [LOG &#40;Transact-SQL&#41;](../../t-sql/functions/log-transact-sql.md)   
 [LOG10 &#40;Transact-SQL&#41;](../../t-sql/functions/log10-transact-sql.md)  
  
  


---
title: LOG10 (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- LOG10
- LOG10_TSQL
dev_langs: TSQL
helpviewer_keywords:
- float expressions
- LOG10 function
- base-10 logarithms
- logarithm of expression
ms.assetid: 1eb7fb34-1937-4a39-a936-f5c0c7c7e06f
caps.latest.revision: "23"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cc919a2a047213b78dbf381d1c486897a7a740da
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="log10-transact-sql"></a>LOG10 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne le logarithme de base 10 de spécifié **float** expression.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
LOG10 ( float_expression )  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Est un [expression](../../t-sql/language-elements/expressions-transact-sql.md) de type **float** ou d’un type qui peut être implicitement converti en **float**.  
  
## <a name="return-types"></a>Types de retour  
 **float**  
  
## <a name="remarks"></a>Notes  
 Les fonctions LOG10 et POWER sont inversement proportionnelles. Par exemple, 10 ^ LOG10 (*n*) =  *n* .  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-calculating-the-base-10-logarithm-for-a-variable"></a>A. Calcul du logarithme de base 10 pour une variable.  
 L'exemple suivant calcule le `LOG10` de la variable spécifiée.  
  
```  
DECLARE @var float;  
SET @var = 145.175643;  
SELECT 'The LOG10 of the variable is: ' + CONVERT(varchar,LOG10(@var));  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
The LOG10 of the variable is: 2.16189      
  
(1 row(s) affected)  
```  
  
### <a name="b-calculating-the-result-of-raising-a-base-10-logarithm-to-a-specified-power"></a>B. Calcul du résultat de l'élévation d'un logarithme de base 10 à une puissance donnée.  
 L'exemple suivant renvoie le résultat de l'élévation d'un logarithme de base 10 à une puissance donnée.  
  
```  
SELECT POWER (10, LOG10(5));   
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-----------  
5  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-calculating-the-base-10-logarithm-for-a-value"></a>C: calcule le logarithme de base 10 d’une valeur.  
 L’exemple suivant calcule le `LOG10` de la valeur spécifiée.  
  
```  
SELECT LOG10(145.175642);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
-------------------  
2.16
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions mathématiques &#40; Transact-SQL &#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)   
 [ALIMENTATION &#40; Transact-SQL &#41;](../../t-sql/functions/power-transact-sql.md)   
 [JOURNAL &#40; Transact-SQL &#41;](../../t-sql/functions/log-transact-sql.md)  
  
  


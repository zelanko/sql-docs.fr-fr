---
title: "Fonctions mathématiques (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 07/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- calculations [SQL Server]
- mathematical functions [SQL Server]
- functions [SQL Server], mathematical
ms.assetid: 46495a2e-81d0-4677-9d72-9db083cd1023
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5ec4a6767acab606d6459b439683a88a0cae1caf
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="mathematical-functions-transact-sql"></a>Fonctions mathématiques (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Les fonctions scalaires suivantes effectuent un calcul, généralement basé sur les valeurs d'entrée fournies en tant qu'arguments, et retournent une valeur numérique :  
  
||||  
|-|-|-|  
|[ABS](../../t-sql/functions/abs-transact-sql.md)|[DEGRÉS](../../t-sql/functions/degrees-transact-sql.md)|[FONCTION RAND](../../t-sql/functions/rand-transact-sql.md)|  
|[FONCTION ACOS](../../t-sql/functions/acos-transact-sql.md)|[EXP](../../t-sql/functions/exp-transact-sql.md)|[ARRONDIR](../../t-sql/functions/round-transact-sql.md)|  
|[ASIN](../../t-sql/functions/asin-transact-sql.md)|[FLOOR](../../t-sql/functions/floor-transact-sql.md)|[CONNEXION](../../t-sql/functions/sign-transact-sql.md)|  
|[ATAN](../../t-sql/functions/atan-transact-sql.md)|[JOURNAL](../../t-sql/functions/log-transact-sql.md)|[SIN](../../t-sql/functions/sin-transact-sql.md)|  
|[ATN2](../../t-sql/functions/atn2-transact-sql.md)|[LOG10](../../t-sql/functions/log10-transact-sql.md)|[SQRT](../../t-sql/functions/sqrt-transact-sql.md)|  
|[PLAFOND](../../t-sql/functions/ceiling-transact-sql.md)|[PI](../../t-sql/functions/pi-transact-sql.md)|[CARRÉ](../../t-sql/functions/square-transact-sql.md)|  
|[COS](../../t-sql/functions/cos-transact-sql.md)|[ALIMENTATION](../../t-sql/functions/power-transact-sql.md)|[TAN](../../t-sql/functions/tan-transact-sql.md)|  
|[COT](../../t-sql/functions/cot-transact-sql.md)|[RADIANS](../../t-sql/functions/radians-transact-sql.md)||  
  
> [!NOTE]  
>  Les fonctions arithmétiques telles que ABS, CEILING, DEGREES, FLOOR, POWER, RADIANS et SIGN retournent une valeur du même type que la valeur d'entrée. Fonctions trigonométriques et autres fonctions, y compris EXP, LOG, LOG10, SQUARE et SQRT, effectuer un cast de leurs valeurs d’entrée à **float** et renvoyer un **float** valeur.  
  
 Toutes les fonctions mathématiques, à l'exception de RAND, sont déterministes. En d'autres termes, elles retournent le même résultat chaque fois qu'elles sont appelées avec un ensemble spécifique de valeurs d'entrée. RAND est déterministe uniquement lorsqu'une valeur de départ est spécifiée. Pour plus d’informations sur le déterminisme des fonctions, consultez [fonctions déterministes et non déterministes](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
## <a name="see-also"></a>Voir aussi  
  [Opérateurs arithmétiques &#40; Transact-SQL &#41;](../../t-sql/language-elements/arithmetic-operators-transact-sql.md)  
  [Fonctions intégrées &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)  
  
  


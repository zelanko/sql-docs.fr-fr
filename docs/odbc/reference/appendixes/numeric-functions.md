---
title: Fonctions numériques (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], numeric functions
- numeric functions [ODBC]
ms.assetid: 4fa548dc-e8b0-4179-92ff-81d6a79d10c3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 03da5b6644e0f7df3dc4e5e16a211cb503023bad
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299869"
---
# <a name="numeric-functions"></a>Fonctions numériques
Le tableau suivant décrit les fonctions numériques qui sont incluses dans l’ensemble de fonctions scalaires ODBC. En appelant **SQLGetInfo** avec un *type d’information* de SQL_NUMERIC_FUNCTIONS, une application peut déterminer quelles fonctions numériques sont prises en charge par un conducteur.  
  
 Toutes les fonctions numériques renvoient les valeurs de type de données SQL_FLOAT à l’exception d’ABS, ROUND, TRUNCATE, SIGN, FLOOR et CEILING, qui retournent des valeurs du même type de données que les paramètres d’entrée.  
  
 Les arguments indiqués comme *numeric_exp* peuvent être le nom d’une colonne, le résultat d’une autre fonction scalaire, ou un *numérique-litera*l, où le type de données sous-jacente pourrait être représenté comme SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL, ou SQL_DOUBLE.  
  
 Arguments désignés comme *float_exp* peuvent être le nom d’une colonne, le résultat d’une autre fonction scalaire, ou un numérique-littérale , où le type de données *sous-jacente*peut être représenté comme SQL_FLOAT.  
  
 Les arguments indiqués comme *integer_exp* peuvent être le nom d’une colonne, le résultat d’une autre fonction scalaire, ou un numérique-littérale , où le type de données *sous-jacente*peut être représenté comme SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, ou SQL_BIGINT.  
  
 Les fonctions CURRENT_DATE, CURRENT_TIME et CURRENT_TIMESTAMP scalar ont été ajoutées dans ODBC 3.0 pour s’aligner sur SQL-92.  
  
|Fonction|Description|  
|--------------|-----------------|  
|**ABS(** _numeric_exp_ **)** (ODBC 1.0)|Retourne la valeur absolue de *numeric_exp*.|  
|**ACOS (** _float_exp_ **)** (ODBC 1.0)|Retourne l’arccosine de *float_exp* comme un angle, exprimé en radians.|  
|**ASIN (** _float_exp_ **)** (ODBC 1.0)|Retourne l’arc de *float_exp* comme un angle, exprimé en radians.|  
|**ATAN (** _float_exp_ **)** (ODBC 1.0)|Retourne l’arctangent de *float_exp* comme un angle, exprimé en radians.|  
|**ATAN2 (** _float_exp1_, _float_exp2_**)** (ODBC 2.0)|Retourne l’arctangent des coordonnées *x* et *y,* spécifiée par *float_exp1* et *float_exp2,* respectivement, comme un angle, exprimé en radianes.|  
|**CEILING (** _numeric_exp_ **)** (ODBC 1.0)|Retourne le plus petit integer plus grand ou égal à *numeric_exp*. La valeur de retour est du même type de données que le paramètre d’entrée.|  
|**COS (** _float_exp_ **)** (ODBC 1.0)|Retourne la cosine de *float_exp*, où *float_exp* est un angle exprimé en radians.|  
|**COT (** _float_exp_ **)** (ODBC 1.0)|Retourne le cotangent de *float_exp*, où *float_exp* est un angle exprimé en radians.|  
|**DEGREES (** _numeric_exp_ **)** (ODBC 2.0)|Retourne le nombre de degrés convertis à partir de *numeric_exp* radians.|  
|**EXP (** _float_exp_ **)** (ODBC 1.0)|Retourne la valeur exponentielle de *float_exp*.|  
|**FLOOR (** _numeric_exp_ **)** (ODBC 1.0)|Retourne le plus grand integer moins ou égal à *numeric_exp*. La valeur de retour est du même type de données que le paramètre d’entrée.|  
|**LOG (** _float_exp_ **)** (ODBC 1.0)|Retourne le logarithme naturel de *float_exp*.|  
|**LOG10 (** _float_exp_ **)** (ODBC 2.0)|Retourne la base 10 logarithm de *float_exp*.|  
|**MOD (** _integer_exp1_, _integer_exp2_**)** (ODBC 1.0)|Retourne le reste (modulus) de *integer_exp1* divisé par *integer_exp2*.|  
|**PI( )** (ODBC 1.0)|Retourne la valeur constante de pi comme une valeur de point flottant.|  
|**POWER (** _numeric_exp_, _integer_exp_**)** (ODBC 2.0)|Retourne la valeur de *numeric_exp* à la puissance de *integer_exp*.|  
|**RADIANS (** _numeric_exp_ **)** (ODBC 2.0)|Retourne le nombre de radianes convertis à partir de *numeric_exp* degrés.|  
|**RAND (**[*integer_exp*]**)** (ODBC 1.0)|Retourne une valeur aléatoire de point flottant utilisant *integer_exp* comme valeur de graine optionnelle.|  
|**ROUND (** _numeric_exp_, _integer_exp_**)** (ODBC 2.0)|Retours *numeric_exp* arrondis à *integer_exp* places à droite du point décimal. Si *integer_exp* est négative, *numeric_exp* est arrondie à &#124;*integer_exp*&#124; endroits à gauche du point décimal.|  
|**SIGN(** _numeric_exp_ **)** (ODBC 1.0)|Retourne un indicateur du signe de *numeric_exp*. Si *numeric_exp* est inférieure à zéro, -1 est retourné. Si *numeric_exp* équivaut à zéro, 0 est retourné. Si *numeric_exp* est supérieure à zéro, 1 est retourné.|  
|**SIN (** _float_exp_ **)** (ODBC 1.0)|Retourne le sinus de *float_exp*, où *float_exp* est un angle exprimé en radians.|  
|**SQRT(** _float_exp_ **)** (ODBC 1.0)|Retourne la racine carrée de *float_exp*.|  
|**TAN (** _float_exp_ **)** (ODBC 1.0)|Retourne la tangente de *float_exp*, où *float_exp* est un angle exprimé en radians.|  
|**TRUNCATE (** _numeric_exp_, _integer_exp_**)** (ODBC 2.0)|Retours *numeric_exp* tronqués à *integer_exp* places à droite du point décimal. Si *integer_exp* est négative, *numeric_exp* est tronquée pour &#124;*integer_exp*&#124; endroits à gauche du point décimal.|

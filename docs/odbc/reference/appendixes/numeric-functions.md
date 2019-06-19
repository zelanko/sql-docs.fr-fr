---
title: Fonctions numériques | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 47711a7e974373e9da4ac8068295029d88accaf6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63181305"
---
# <a name="numeric-functions"></a>Fonctions numériques
Le tableau suivant décrit les fonctions numériques qui sont incluses dans le jeu de fonction scalaire ODBC. En appelant **SQLGetInfo** avec un *d’informations, tapez* de SQL_NUMERIC_FUNCTIONS, une application peut déterminer les fonctions numériques sont pris en charge par un pilote.  
  
 Fonctions numériques toutes les valeurs de retour du type de données SQL_FLOAT à l’exception de ABS, ROUND, TRUNCATE, signe, FLOOR et CEILING, qui retournent des valeurs des données mêmes type que les paramètres d’entrée.  
  
 Arguments indiqués par *positions numeric_exp* peut être le nom d’une colonne, le résultat d’une autre fonction scalaire, ou un *numérique-litera*l, où le type de données sous-jacent peut être représenté en tant que SQL_NUMERIC, SQL_ DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL ou SQL_DOUBLE.  
  
 Arguments indiqués par *exp_float* peut être le nom d’une colonne, le résultat d’une autre fonction scalaire, ou un *littéral numérique*, où le type de données sous-jacent peut être représenté comme SQL_FLOAT.  
  
 Arguments indiqués par *integer_exp* peut être le nom d’une colonne, le résultat d’une autre fonction scalaire, ou un *littéral numérique*, où le type de données sous-jacent peut être représenté en tant que SQL_TINYINT, SQL_ SMALLINT, SQL_INTEGER ou SQL_BIGINT.  
  
 Les fonctions scalaires CURRENT_DATE, CURRENT_TIME et CURRENT_TIMESTAMP ont été ajoutées dans ODBC 3.0 pour les aligner avec SQL-92.  
  
|Fonction|Description|  
|--------------|-----------------|  
|**ABS(** _numeric_exp_ **)**  (ODBC 1.0)|Retourne la valeur absolue de *positions numeric_exp*.|  
|**ACOS(** _float_exp_ **)**  (ODBC 1.0)|Retourne l’arc cosinus de *exp_float* à un angle exprimé en radians.|  
|**ASIN(** _float_exp_ **)**  (ODBC 1.0)|Retourne l’arc sinus de *exp_float* à un angle exprimé en radians.|  
|**ATAN(** _float_exp_ **)**  (ODBC 1.0)|Retourne l’arc tangente de *exp_float* à un angle exprimé en radians.|  
|**ATAN2(** _float_exp1_, _float_exp2_ **)**  (ODBC 2.0)|Retourne l’arc tangente de le *x* et *y* coordonnées, spécifiées par *exp_float1* et *exp_float2*, respectivement, sous la forme d’un angle. exprimé en radians.|  
|**CEILING(** _numeric_exp_ **)**  (ODBC 1.0)|Retourne le plus petit entier supérieur ou égal à *positions numeric_exp*. La valeur de retour est du même type de données en tant que le paramètre d’entrée.|  
|**COS(** _float_exp_ **)**  (ODBC 1.0)|Retourne le cosinus de *exp_float*, où *exp_float* est un angle exprimé en radians.|  
|**COT(** _float_exp_ **)**  (ODBC 1.0)|Renvoie la cotangente de *exp_float*, où *exp_float* est un angle exprimé en radians.|  
|**DEGRÉS (** _positions numeric_exp_ **)** (ODBC 2.0)|Retourne le nombre de degrés convertis à partir de *positions numeric_exp* radians.|  
|**EXP (** _exp_float_ **)** (ODBC version 1.0)|Retourne la valeur exponentielle de *exp_float*.|  
|**FLOOR(** _numeric_exp_ **)**  (ODBC 1.0)|Retourne le plus grand entier inférieur ou égal à *positions numeric_exp*. La valeur de retour est du même type de données en tant que le paramètre d’entrée.|  
|**JOURNAL (** _exp_float_ **)** (ODBC version 1.0)|Retourne le logarithme népérien de *exp_float*.|  
|**LOG10 (** _exp_float_ **)** (ODBC 2.0)|Logarithme de base 10 de retourne de *exp_float*.|  
|**MOD(** _integer_exp1_, _integer_exp2_ **)**  (ODBC 1.0)|Retourne le reste (modulo) de *exp_entier1* divisé par *exp_entier2*.|  
|**PI( )**  (ODBC 1.0)|Retourne la valeur constante de pi sous la forme d’une valeur à virgule flottante.|  
|**POWER (** _positions numeric_exp_, _integer_exp_ **)** (ODBC 2.0)|Retourne la valeur de *positions numeric_exp* à la puissance de *integer_exp*.|  
|**RADIANS(** _numeric_exp_ **)**  (ODBC 2.0)|Retourne le nombre de radians convertis à partir de *positions numeric_exp* degrés.|  
|**RAND(** [*integer_exp*] **)**  (ODBC 1.0)|Retourne une valeur à virgule flottante aléatoire à l’aide *integer_exp* en tant que la valeur de départ facultative.|  
|**ROUND (** _positions numeric_exp_, _integer_exp_ **)** (ODBC 2.0)|Retourne *positions numeric_exp* arrondi à *integer_exp* place droite de la virgule décimale. Si *integer_exp* est négatif, *positions numeric_exp* est arrondi à &#124; *integer_exp* &#124; place à gauche de la virgule décimale.|  
|**SIGN(** _numeric_exp_ **)**  (ODBC 1.0)|Retourne un indicateur du signe de *positions numeric_exp*. Si *positions numeric_exp* est inférieur à zéro, -1 est retournée. Si *positions numeric_exp* est égal à zéro, 0 est retournée. Si *positions numeric_exp* est supérieure à zéro, 1 est retourné.|  
|**SIN(** _float_exp_ **)**  (ODBC 1.0)|Retourne le sinus de *exp_float*, où *exp_float* est un angle exprimé en radians.|  
|**SQRT(** _float_exp_ **)**  (ODBC 1.0)|Retourne la racine carrée de *exp_float*.|  
|**TAN(** _float_exp_ **)**  (ODBC 1.0)|Retourne la tangente de *exp_float*, où *exp_float* est un angle exprimé en radians.|  
|**TRUNCATE (** _positions numeric_exp_, _integer_exp_ **)** (ODBC 2.0)|Retourne *positions numeric_exp* tronqué à *integer_exp* place droite de la virgule décimale. Si *integer_exp* est négatif, *positions numeric_exp* est tronqué à &#124; *integer_exp* &#124; place à gauche de la virgule décimale.|

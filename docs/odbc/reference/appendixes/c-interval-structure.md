---
title: Structure d’intervalle C | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], interval data types
- interval data type [ODBC], structure
- C data types [ODBC], interval
ms.assetid: 52b42b56-50aa-4ce6-8d79-0963c7a71437
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3387b4fa48eb1a04102daadcc08f971765d7ca2b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68037781"
---
# <a name="c-interval-structure"></a>Structure d’intervalle C
Chacun des types de données d’intervalle C répertoriées dans le [les Types de données C](../../../odbc/reference/appendixes/c-data-types.md) section utilise la même structure pour contenir les données d’intervalle. Lorsque **SQLFetch**, **SQLFetchScroll**, ou **SQLGetData** est appelée, le pilote retourne les données dans la structure SQL_INTERVAL_STRUCT, utilise la valeur qui a été spécifiée par le application pour les types de données C (dans l’appel à **SQLBindCol**, **SQLGetData**, ou **SQLBindParameter**) pour interpréter le contenu de SQL_INTERVAL_STRUCT et remplit la *interval_type* champ de la structure avec le *enum* valeur correspondant au type C. Notez que les pilotes ne lisent pas les *interval_type* champ pour déterminer le type de l’intervalle ; ils récupèrent la valeur du champ de descripteur SQL_DESC_CONCISE_TYPE. Lors de la structure est utilisée pour les données de paramètre, le pilote utilise la valeur spécifiée par l’application dans le champ SQL_DESC_CONCISE_TYPE du descripteur APD interpréter le contenu de SQL_INTERVAL_STRUCT, même si l’application définit la valeur de la  *interval_type* champ à une valeur différente.  
  
 Cette structure est définie comme suit :  
  
```  
typedef struct tagSQL_INTERVAL_STRUCT  
{  
   SQLINTERVAL interval_type;   
   SQLSMALLINT interval_sign;  
   union {  
         SQL_YEAR_MONTH_STRUCT   year_month;  
         SQL_DAY_SECOND_STRUCT   day_second;  
         } intval;  
} SQL_INTERVAL_STRUCT;  
typedef enum   
{  
   SQL_IS_YEAR = 1,  
   SQL_IS_MONTH = 2,  
   SQL_IS_DAY = 3,  
   SQL_IS_HOUR = 4,  
   SQL_IS_MINUTE = 5,  
   SQL_IS_SECOND = 6,  
   SQL_IS_YEAR_TO_MONTH = 7,  
   SQL_IS_DAY_TO_HOUR = 8,  
   SQL_IS_DAY_TO_MINUTE = 9,  
   SQL_IS_DAY_TO_SECOND = 10,  
   SQL_IS_HOUR_TO_MINUTE = 11,  
   SQL_IS_HOUR_TO_SECOND = 12,  
   SQL_IS_MINUTE_TO_SECOND = 13  
} SQLINTERVAL;  
  
typedef struct tagSQL_YEAR_MONTH  
{  
   SQLUINTEGER year;  
   SQLUINTEGER month;   
} SQL_YEAR_MONTH_STRUCT;  
  
typedef struct tagSQL_DAY_SECOND  
{  
   SQLUINTEGER day;  
   SQLUINTEGER hour;  
   SQLUINTEGER minute;  
   SQLUINTEGER second;  
   SQLUINTEGER fraction;  
} SQL_DAY_SECOND_STRUCT;  
```  
  
 Le *interval_type* champ de la SQL_INTERVAL_STRUCT indique à l’application quelle structure est maintenu dans l’union et également quels membres de la structure sont pertinentes. Le *interval_sign* champ a la valeur SQL_FALSE si l’intervalle de début de champ n’est pas signé ; si elle est SQL_TRUE, le champ Début est négatif. La valeur dans le champ Début lui-même est toujours non signée, quelle que soit la valeur de *interval_sign*. Le *interval_sign* champ agit comme un bit de signe.

---
title: Structure d’intervalle C Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 02c86ebe24a0e12531e355f95185b01f3089a31b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292151"
---
# <a name="c-interval-structure"></a>Structure d’intervalle C
Chacun des types de données d’intervalle C répertoriés dans la section [C Data Types](../../../odbc/reference/appendixes/c-data-types.md) utilise la même structure pour contenir les données d’intervalle. Lorsque **SQLFetch**, **SQLFetchScroll**, ou **SQLGetData** est appelé, le conducteur retourne des données dans la structure SQL_INTERVAL_STRUCT, utilise la valeur qui a été spécifiée par l’application pour les types de données C (dans l’appel à **SQLBindCol**, **SQLGetData**, ou **SQLBindParameter**) pour interpréter le contenu de SQL_INTERVAL_STRUCT, et remplit le champ *interval_type* de la structure avec la valeur enum correspondant à la *Cum.* Notez que les conducteurs ne lisent pas le champ *interval_type* pour déterminer le type d’intervalle; ils récupèrent la valeur du champ descripteur SQL_DESC_CONCISE_TYPE. Lorsque la structure est utilisée pour les données de paramètres, le conducteur utilise la valeur spécifiée par l’application dans le champ SQL_DESC_CONCISE_TYPE de l’APD pour interpréter le contenu de SQL_INTERVAL_STRUCT, même si l’application définit la valeur du *champ interval_type* à une valeur différente.  
  
 Cette structure est définie comme suit :  
  
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
  
 Le *interval_type* domaine de la SQL_INTERVAL_STRUCT indique à la demande quelle structure est tenue dans le syndicat et aussi quels membres de la structure sont pertinents. Le champ *interval_sign* a la valeur SQL_FALSE si le champ de tête d’intervalle n’est pas signé; s’il est SQL_TRUE, le champ de tête est négatif. La valeur dans le domaine de tête lui-même n’est toujours pas signée, quelle que soit la valeur de *interval_sign*. Le champ *interval_sign* agit comme un morceau de signe.

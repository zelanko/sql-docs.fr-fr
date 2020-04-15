---
title: Date, Heure et Literals Timestamp Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], literals
ms.assetid: 2b42a52a-6353-494c-a179-3a7533cd729f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d899938be4689daab50a773f189219a797794006
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288295"
---
# <a name="date-time-and-timestamp-literals"></a>Littéraux de date, d’heure et d’horodatage
La séquence d’évasion pour les littérals de date, d’heure et d’humidité temporelle est  
  
 **-**  _type_ **'** _valeur_ **''**  
  
 où *le type littéral* est l’une des valeurs énumérées dans le tableau suivant.  
  
|*type littéral*|Signification|Format de *valeur*|  
|---------------------|-------------|-----------------------|  
|**D**|Date|*yyyy*-*mm*-*dd*|  
|**T**|Temps|*hh*:*mm*:*ss*[1]|  
|**Ts**|Timestamp|*yyyy*-*mm*-*dd* *hh*:*mm*:*ss*[.* f...*] [1]|  
  
 [1] Le nombre de chiffres à droite du point décimal dans un intervalle de temps ou d’intervalle de temps littéral contenant un composant de secondes dépend de la précision secondes, comme contenu dans le champ descripteur SQL_DESC_PRECISION. (Pour plus d’informations, voir [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
 Pour plus d’informations sur les séquences d’évasion date, heure et timetamp, voir [Date, Time et Timestamp Escape Sequences](../../../odbc/reference/appendixes/date-time-and-timestamp-escape-sequences.md) dans l’annexe C: SQL Grammar.  
  
 Par exemple, les deux énoncés SQL suivants mettent à jour la date d’ouverture de l’ordre de vente 1023 dans le tableau des commandes. La première déclaration utilise la syntaxe de séquence d’évacuation. La deuxième déclaration utilise la syntaxe native Oracle Rdb pour la colonne DATE et n’est pas interopérable.  
  
```  
UPDATE Orders SET OpenDate={d '1995-01-15'} WHERE OrderID=1023  
UPDATE Orders SET OpenDate='15-Jan-1995' WHERE OrderID=1023  
```  
  
 La séquence d’évacuation d’une date, d’une heure ou d’un littératie temporelle peut également être placée dans une variable de caractère liée à un paramètre de date, d’heure ou d’heure. Par exemple, le code suivant utilise un paramètre de date lié à une variable de caractère pour mettre à jour la date d’ouverture de l’ordre de vente 1023 dans le tableau des commandes :  
  
```  
SQLCHAR      OpenDate[56]; // The size of a date literal is 55.  
SQLINTEGER   OpenDateLenOrInd = SQL_NTS;  
  
// Bind the parameter.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_TYPE_DATE, 0, 0,  
                  OpenDate, sizeof(OpenDate), &OpenDateLenOrInd);  
  
// Place the date in the OpenDate variable. In addition to the escape  
// sequence shown, it would also be possible to use either of the  
// strings "{d '1995-01-15'}" and "15-Jan-1995", although the latter  
// is data source-specific.  
strcpy_s( (char*) OpenDate, _countof(OpenDate), "{d '1995-01-15'}");  
  
// Execute the statement.  
SQLExecDirect(hstmt, "UPDATE Orders SET OpenDate=? WHERE OrderID = 1023", SQL_NTS);  
```  
  
 Cependant, il est généralement plus efficace de lier le paramètre directement à une structure de date :  
  
```  
SQL_DATE_STRUCT   OpenDate;  
SQLINTEGER        OpenDateInd = 0;  
  
// Bind the parameter.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 0, 0,  
                  &OpenDate, 0, &OpenDateLen);  
  
// Place the date in the dsOpenDate structure.  
OpenDate.year = 1995;  
OpenDate.month = 1;  
OpenDate.day = 15;  
  
// Execute the statement.  
SQLExecDirect(hstmt, "UPDATE Employee SET OpenDate=? WHERE OrderID = 1023", SQL_NTS);  
```  
  
 Pour déterminer si un conducteur prend en charge les séquences d’évacuation de l’ODBC pour les littérals de date, d’heure ou d’humidité temporelle, une application appelle **SQLGetTypeInfo**. Si la source de données prend en charge un type de données de date, d’heure ou de timetamp, elle doit également prendre en charge la séquence d’évacuation correspondante.  
  
 Les sources de données peuvent également prendre en charge les littérations de date définies dans les spécifications ANSI SQL-92, qui sont différentes des séquences d’évasion de l’ODBC pour les littérations de date, d’heure ou d’humidité temporelle. Pour déterminer si une source de données prend en charge les littérals de l’ANSI, une application appelle **SQLGetInfo** avec l’option SQL_ANSI_SQL_DATETIME_LITERALS.  
  
 Pour déterminer si un conducteur prend en charge les séquences d’évacuation ODBC pour les littérals d’intervalle, une application appelle **SQLGetTypeInfo**. Si la source de données prend en charge un type de données d’intervalle de date, elle doit également prendre en charge la séquence d’évacuation correspondante.  
  
 Les sources de données peuvent également prendre en charge les littérations de date définies dans les spécifications ANSI SQL-92, qui sont différentes des séquences d’évacuation ODBC pour les littérations d’intervalle de date. Pour déterminer si une source de données prend en charge les littérals de l’ANSI, une application appelle **SQLGetInfo** avec l’option SQL_ANSI_SQL_DATETIME_LITERALS.

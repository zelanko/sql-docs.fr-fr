---
title: Littéraux de date, d’heure et d’horodatage | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e6191995c9d1c488fc5af056248ba39dd3eb4607
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68076983"
---
# <a name="date-time-and-timestamp-literals"></a>Littéraux de date, d’heure et d’horodatage
La séquence d’échappement pour les littéraux de date, d’heure et d’horodatage est  
  
 **{**  _-type_ **'** _valeur_ **'}**  
  
 où *Literal-type* est l’une des valeurs énumérées dans le tableau suivant.  
  
|*type littéral*|Signification|Format de *valeur*|  
|---------------------|-------------|-----------------------|  
|**e**|Date|*aaaa*-** mm-*JJ*|  
|**t**|Simultanément|*hh*:*mm*:*SS*[1]|  
|**TS**|Timestamp|*aaaa*-** mm-*JJ* *hh*:*mm*:*SS*[.* f...*] 1,0|  
  
 [1] le nombre de chiffres à droite de la virgule décimale dans un littéral d’intervalle de temps ou d’horodatage contenant un composant de secondes dépend de la précision en secondes, telle qu’elle est contenue dans le champ du descripteur de SQL_DESC_PRECISION. (Pour plus d’informations, consultez [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
 Pour plus d’informations sur les séquences d’échappement de date, d’heure et d’horodatage, consultez [séquences d’échappement de date, d’heure et d’horodatage](../../../odbc/reference/appendixes/date-time-and-timestamp-escape-sequences.md) dans annexe C : grammaire SQL.  
  
 Par exemple, les deux instructions SQL suivantes mettent à jour la date d’ouverture de la commande client 1023 dans la table Orders. La première instruction utilise la syntaxe de la séquence d’échappement. La deuxième instruction utilise la syntaxe Native RDB Oracle pour la colonne de DATE et n’est pas interopérable.  
  
```  
UPDATE Orders SET OpenDate={d '1995-01-15'} WHERE OrderID=1023  
UPDATE Orders SET OpenDate='15-Jan-1995' WHERE OrderID=1023  
```  
  
 La séquence d’échappement pour un littéral de date, d’heure ou d’horodatage peut également être placée dans une variable de caractère liée à un paramètre de date, d’heure ou d’horodatage. Par exemple, le code suivant utilise un paramètre de date lié à une variable de caractères pour mettre à jour la date d’ouverture de la commande client 1023 dans la table Orders :  
  
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
  
 Toutefois, il est généralement plus efficace de lier le paramètre directement à une structure de date :  
  
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
  
 Pour déterminer si un pilote prend en charge les séquences d’échappement ODBC pour les littéraux de date, d’heure ou d’horodatage, une application appelle **SQLGetTypeInfo**. Si la source de données prend en charge un type de données date, Time ou TIMESTAMP, elle doit également prendre en charge la séquence d’échappement correspondante.  
  
 Les sources de données peuvent également prendre en charge les littéraux datetime définis dans la spécification SQL-92 ANSI, qui sont différents des séquences d’échappement ODBC pour les littéraux de date, d’heure ou d’horodatage. Pour déterminer si une source de données prend en charge les littéraux ANSI, une application appelle **SQLGetInfo** avec l’option SQL_ANSI_SQL_DATETIME_LITERALS.  
  
 Pour déterminer si un pilote prend en charge les séquences d’échappement ODBC pour les littéraux d’intervalle, une application appelle **SQLGetTypeInfo**. Si la source de données prend en charge un type de données DateTime Interval, elle doit également prendre en charge la séquence d’échappement correspondante.  
  
 Les sources de données peuvent également prendre en charge les littéraux datetime définis dans la spécification SQL-92 ANSI, qui sont différents des séquences d’échappement ODBC pour les littéraux d’intervalle DateTime. Pour déterminer si une source de données prend en charge les littéraux ANSI, une application appelle **SQLGetInfo** avec l’option SQL_ANSI_SQL_DATETIME_LITERALS.

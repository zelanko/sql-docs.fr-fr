---
title: 'SQL à C : Intervalles de jours-heures | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], day-time intervals
- day-time intervals [ODBC]
- data conversions from SQL to C types [ODBC], day-time intervals
- intervals [ODBC], converting
ms.assetid: 8ea84d69-2292-4128-89a0-f184f68abb98
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ee08f42a4ccd7eb51f45e1654f20e264f80c49d2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63270429"
---
# <a name="sql-to-c-day-time-intervals"></a>SQL à C : Intervalles de jours-heures

Les identificateurs pour les types de données SQL ODBC intervalle de jours-heures sont les suivantes :

- SQL_INTERVAL_DAY
- SQL_INTERVAL_DAY_TO_MINUTE
- SQL_INTERVAL_HOUR
- SQL_INTERVAL_DAY_TO_SECOND
- SQL_INTERVAL_MINUTE
- SQL_INTERVAL_HOUR_TO_MINUTE
- SQL_INTERVAL_SECOND
- SQL_INTERVAL_HOUR_TO_SECOND
- SQL_INTERVAL_DAY_TO_HOUR
- SQL_INTERVAL_MINUTE_TO_SECOND

Le tableau suivant présente le ODBC C types de données à laquelle l’intervalle de jours-heures de données SQL peut-être être convertie. Pour obtenir une explication des colonnes et des termes dans la table, consultez [conversion des données à partir de SQL pour les Types de données C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).

|Identificateur de type C|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|Tous les types d’intervalle C jours-heures|Portion de champs ne pas tronquée à droite<br /><br /> Portion de champs tronquée à droite<br /><br /> La précision de la cible de début n’est pas assez grande pour contenir les données à partir de la source|Données<br /><br /> Données tronquées<br /><br /> Indéfini|Longueur des données<br /><br /> Longueur des données<br /><br /> Indéfini|n/a<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_STINYINT[b] SQL_C_UTINYINT[b] SQL_C_USHORT[b] SQL_C_SHORT[b] SQL_C_SLONG[b] SQL_C_ULONG[b] SQL_C_NUMERIC[b] SQL_C_BIGINT[b]|Précision de l’intervalle a été un champ unique et les données ont été converties sans troncation<br /><br /> Précision de l’intervalle a été un champ unique et tronquée en fractions de seconde<br /><br /> Précision de l’intervalle a été un seul champ et tronqué en entier<br /><br /> Précision de l’intervalle n’était pas un champ unique|Données<br /><br /> Données tronquées<br /><br /> Données tronquées<br /><br /> Indéfini|Taille du type de données C<br /><br /> Longueur des données<br /><br /> Longueur des données<br /><br /> Taille du type de données C|n/a<br /><br /> 01S07<br /><br /> 22003<br /><br /> 07006|  
|SQL_C_BINARY|Longueur d’octet de données < = *BufferLength*<br /><br /> Longueur d’octet de données > *BufferLength*|Données<br /><br /> Indéfini|Longueur des données<br /><br /> Indéfini|n/a<br /><br /> 22003|  
|SQL_C_CHAR|Longueur d’octet de caractère < *BufferLength*<br /><br /> Nombre de chiffres de l’ensemble (par opposition aux fractions de seconde) < *BufferLength*<br /><br /> Nombre de chiffres de l’ensemble (par opposition aux fractions de seconde) > = *BufferLength*|Données<br /><br /> Données tronquées<br /><br /> Indéfini|Taille du type de données C<br /><br /> Taille du type de données C<br /><br /> Indéfini|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Longueur des caractères < *BufferLength*<br /><br /> Nombre de chiffres de l’ensemble (par opposition aux fractions de seconde) < *BufferLength*<br /><br /> Nombre de chiffres de l’ensemble (par opposition aux fractions de seconde) > = *BufferLength*|Données<br /><br /> Données tronquées<br /><br /> Indéfini|Taille du type de données C<br /><br /> Taille du type de données C<br /><br /> Indéfini|n/a<br /><br /> 01004<br /><br /> 22003|  
  
 [a] intervalle de jours-heures d’un type SQL peut être converti en n’importe quel type d’intervalle de temps du jour C.  
  
 [b] si la précision de l’intervalle est un champ unique (un des jours, heure, MINUTE ou seconde), l’intervalle de type SQL peut être converti en n’importe quel numérique exact (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_USHORT, SQL_C_SHORT, SQL_C_SLONG, SQL_C_ULONG ou SQL_C_NUMERIC).  
  
La conversion par défaut d’un intervalle de type SQL consiste au type de données d’intervalle C correspondant. L’application puis lie la colonne ou du paramètre (ou définit le champ SQL_DESC_DATA_PTR dans l’enregistrement approprié de la ARD) pour pointer vers la structure SQL_INTERVAL_STRUCT initialisée (ou passe un pointeur vers la structure SQL_ INTERVAL_STRUCT comme le *TargetValuePtr* argument dans un appel à **SQLGetData**).  
  
L’exemple suivant montre comment transférer des données à partir d’une colonne de type SQL_INTERVAL_DAY_TO_MINUTE dans la structure SQL_INTERVAL_STRUCT où elle est renvoyée comme un intervalle DAY_TO_HOUR.  

```cpp
SQL_INTERVAL_STRUCT is;  
SQLINTEGER    cbValue;  
SQLUINTEGER   days, hours;  
  
// Execute a select statement; "interval_column" is a column  
// whose data type is SQL_INTERVAL_DAY_TO_MINUTE.  
SQLExecDirect(hstmt, "SELECT interval_column FROM table", SQL_NTS);  
  
// Bind  
SQLBindCol(hstmt, 1, SQL_C_INTERVAL_DAY_TO_MINUTE, &is, sizeof(SQL_INTERVAL_STRUCT), &cbValue);  
  
// Fetch  
SQLFetch(hstmt);  
  
// Process data  
days = is.intval.day_second.day;  
hours = is.intval.day_second.hour;  
```

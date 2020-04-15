---
title: 'SQL à C : Intervalles de jour-temps Microsoft Docs'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1318da5285ba2384dd23e4c235e698aa72c7658e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296469"
---
# <a name="sql-to-c-day-time-intervals"></a>SQL à C : Intervalles de jours-heures

Les identificateurs pour l’intervalle de jour ODBC SQL types de données sont les suivants:

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

Le tableau suivant montre les types de données ODBC C auxquels les données SQL d’intervalle de jour peuvent être converties. Pour une explication des colonnes et des termes dans le tableau, voir [convertir les données de SQL à C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).

|Identifiant de type C|Test|**TargetValuePtr (en)*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|Tous les types d’intervalle C de jour|Partie des champs de trail non tronquée<br /><br /> Partie des champs de trail tronquée<br /><br /> La précision de pointe de la cible n’est pas assez grande pour contenir les données de la source|Données<br /><br /> Données tronquées<br /><br /> Indéfini|Longueur des données<br /><br /> Longueur des données<br /><br /> Indéfini|n/a<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_STINYINT[b] SQL_C_UTINYINT[b] SQL_C_USHORT[b] SQL_C_SHORT[b] SQL_C_SLONG[b] SQL_C_ULONG[b] SQL_C_NUMERIC[b] SQL_C_BIGINT[b]|La précision d’intervalle était un champ unique et les données ont été converties sans troncation<br /><br /> La précision d’intervalle était un champ simple et tronqué fractionnaire<br /><br /> La précision d’intervalle était un champ simple et tronquée entière<br /><br /> La précision d’intervalle n’était pas un seul champ|Données<br /><br /> Données tronquées<br /><br /> Données tronquées<br /><br /> Indéfini|Taille du type de données C<br /><br /> Longueur des données<br /><br /> Longueur des données<br /><br /> Taille du type de données C|n/a<br /><br /> 01S07<br /><br /> 22003<br /><br /> 07006|  
|SQL_C_BINARY|Longueur d’enseille des données <*'BufferLength'*<br /><br /> Longueur d’enseille des données > *BufferLength*|Données<br /><br /> Indéfini|Longueur des données<br /><br /> Indéfini|n/a<br /><br /> 22003|  
|SQL_C_CHAR|Longueur d’en-linge de caractère < *BufferLength*<br /><br /> Nombre de chiffres entiers (par opposition à fractionnels) < *BufferLength*<br /><br /> Nombre de chiffres entiers (par opposition à fractionnels) >' *BufferLength*|Données<br /><br /> Données tronquées<br /><br /> Indéfini|Taille du type de données C<br /><br /> Taille du type de données C<br /><br /> Indéfini|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Longueur de caractère < *BufferLength*<br /><br /> Nombre de chiffres entiers (par opposition à fractionnels) < *BufferLength*<br /><br /> Nombre de chiffres entiers (par opposition à fractionnels) >' *BufferLength*|Données<br /><br /> Données tronquées<br /><br /> Indéfini|Taille du type de données C<br /><br /> Taille du type de données C<br /><br /> Indéfini|n/a<br /><br /> 01004<br /><br /> 22003|  
  
 [a] Un type SQL d’intervalle de jour peut être converti en n’importe quel type d’intervalle C de jour.  
  
 [b] Si la précision d’intervalle est un seul champ (un de JOUR, HOUR, MINUTE, ou SECOND), le type SQL d’intervalle peut être converti en n’importe quel numérique exact (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_USHORT, SQL_C_SHORT, SQL_C_SLONG, SQL_C_ULONG, ou SQL_C_NUMERIC).  
  
La conversion par défaut d’un type SQL d’intervalle est au type de données d’intervalle C correspondant. L’application lie ensuite la colonne ou le paramètre (ou définit le champ SQL_DESC_DATA_PTR dans le dossier approprié de l’ARD) pour indiquer la structure SQL_INTERVAL_STRUCT initialisée (ou passe un pointeur à la structure INTERVAL_STRUCT SQL_ comme l’argument *TargetValuePtr* dans un appel à **SQLGetData**).  
  
L’exemple suivant montre comment transférer des données à partir d’une colonne de type SQL_INTERVAL_DAY_TO_MINUTE dans la structure SQL_INTERVAL_STRUCT de telle sorte qu’il revient comme un intervalle DAY_TO_HOUR.  

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

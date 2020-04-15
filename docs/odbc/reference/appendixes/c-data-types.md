---
title: Types de données C (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 07/12/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], C data types
- C data types [ODBC], about C data types
- C data types [ODBC]
- C buffers [ODBC]
ms.assetid: b681d260-3dbb-47df-a616-4910d727add7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 979bfe85e1e78b55718e1f12fdcfcc7583097bb4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292299"
---
# <a name="c-data-types"></a>Type de données C
Les types de données ODBC C indiquent le type de données des tampons C utilisés pour stocker les données de l’application.  
  
 Tous les conducteurs doivent prendre en charge tous les types de données C. Cela est nécessaire parce que tous les conducteurs doivent prendre en charge tous les types C à quels types SQL qu’ils prennent en charge peuvent être convertis, et tous les conducteurs prennent en charge au moins un type SQL caractère. Parce que le type SQL caractère peut être converti à et à partir de tous les types C, tous les conducteurs doivent prendre en charge tous les types C.  
  
 Le type de données C est spécifié dans les fonctions **SQLBindCol** et **SQLGetData** avec l’argument *TargetType* et dans la fonction **SQLBindParameter** avec l’argument *ValueType.* Il peut également être spécifié en appelant **SQLSetDescField** pour définir le champ SQL_DESC_CONCISE_TYPE d’un ARD ou APD, ou en appelant **SQLSetDescRec** avec l’argument *type* (et l’argument *SubType* si nécessaire) et *l’argument DescriptorHandle* réglé à la poignée d’un ARD ou APD.  
  
 Les tableaux suivants répertorie les identifiants de type valides pour les types de données C. Le tableau répertorie également le type de données ODBC C qui correspond à chaque identifiant et à la définition de ce type de données.  
  
|Identifiant de type C|ODBC C typedef|Type C|  
|-----------------------|--------------------|------------|  
|SQL_C_CHAR|SQLCHAR - France|unsigned char *|  
|SQL_C_WCHAR|SQLWCHAR - France|wchar_t *|  
|SQL_C_SSHORT[j]|SQLSMALLINT|short int|  
|SQL_C_USHORT[j]|SQLUSMALLINT|unsigned short int|  
|SQL_C_SLONG[j]|SQLINTEGER|long int|  
|SQL_C_ULONG[j]|SQLUINTEGER|unsigned long int|  
|SQL_C_FLOAT|SQLREAL (SQLREAL)|float|  
|SQL_C_DOUBLE|SQLDOUBLE, SQLFLOAT|double|  
|SQL_C_BIT|SQLCHAR|unsigned char|  
|SQL_C_STINYINT[j]|SQLSCHAR (SQLSCHAR)|signed char|  
|SQL_C_UTINYINT[j]|SQLCHAR|unsigned char|  
|SQL_C_SBIGINT|SQLBIGINT|_int64[h]|  
|SQL_C_UBIGINT|SQLUBIGINT|non signé _int64[h]|  
|SQL_C_BINARY|SQLCHAR - France|unsigned char *|  
|SQL_C_BOOKMARK[i]|Signet|non signé longtemps int[d]|  
|SQL_C_VARBOOKMARK|SQLCHAR - France|unsigned char *|  
|Tous les types de données d’intervalle C|SQL_INTERVAL_STRUCT|Voir la section [Structure d’intervalle C,](../../../odbc/reference/appendixes/c-interval-structure.md) plus tard dans cette annexe.|  
  
 **Identifiant de type C** SQL_C_TYPE_DATE[c]  
  
 **ODBC C typedef** SQL_DATE_STRUCT  
  
 **Type C**  
  
```  
struct tagDATE_STRUCT {  
   SQLSMALLINT year;  
   SQLUSMALLINT month;  
   SQLUSMALLINT day;    
} DATE_STRUCT;[a]  
```  
  
 **Identifiant de type C** SQL_C_TYPE_TIME[c]  
  
 **ODBC C typedef** SQL_TIME_STRUCT  
  
 **Type C**  
  
```  
struct tagTIME_STRUCT {  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
} TIME_STRUCT;[a]  
```  
  
 **Identifiant de type C** SQL_C_TYPE_TIMESTAMP[c]  
  
 **ODBC C typedef** SQL_TIMESTAMP_STRUCT  
  
 **Type C**  
  
```  
struct tagTIMESTAMP_STRUCT {  
   SQLSMALLINT year;  
   SQLUSMALLINT month;  
   SQLUSMALLINT day;  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
   SQLUINTEGER fraction;[b]   
} TIMESTAMP_STRUCT;[a]  
```  
  
 **Identifiant de type C** SQL_C_NUMERIC  
  
 **ODBC C typedef** SQL_NUMERIC_STRUCT  
  
 **Type C**  
  
```  
struct tagSQL_NUMERIC_STRUCT {  
   SQLCHAR precision;  
   SQLSCHAR scale;  
   SQLCHAR sign[g];  
   SQLCHAR val[SQL_MAX_NUMERIC_LEN];[e], [f]   
} SQL_NUMERIC_STRUCT;  
```  
  
 **Identifiant de type C** SQL_C_GUID  
  
 **ODBC C typedef** SQLGUID  
  
 **Type C**  
  
```  
struct tagSQLGUID {  
   DWORD Data1;  
   WORD Data2;  
   WORD Data3;  
   BYTE Data4[8];  
} SQLGUID;[k]  
```  
  
 [a] Les valeurs de l’année, du mois, du jour, de l’heure, de la minute et du deuxième champ dans les types de données date time C doivent se conformer aux contraintes du calendrier grégorien. (Voir [Contraintes du Calendrier grégorien](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md) plus tard dans cette annexe.)  
  
 [b] La valeur du champ fraction est le nombre de milliardièmes de seconde et varie de 0 à 999 999 999 (1 moins d’un milliard). Par exemple, la valeur du champ fractionnel pendant une demi-seconde est de 500 000 000, pour un millième de seconde (une milliseconde) est de 1 000 000, pour un millionième de seconde (une microseconde) est de 1 000, et pour un milliardième de seconde (une nanoseconde) est de 1.  
  
 [c] Dans ODBC 2. *x*, les types de données C date, heure et timetamp sont SQL_C_DATE, SQL_C_TIME et SQL_C_TIMESTAMP.  
  
 [d] Les applications ODBC 3 *.x* doivent utiliser SQL_C_VARBOOKMARK, et non SQL_C_BOOKMARK. Lorsqu’une application ODBC 3 *.x* fonctionne avec un ODBC 2. *x* pilote, l’ODBC 3 *.x* Driver Manager cartographiera SQL_C_VARBOOKMARK pour SQL_C_BOOKMARK.  
  
 [e] Un nombre est stocké dans le champ *val* de la structure SQL_NUMERIC_STRUCT comme un intégriste à l’échelle, en mode endian peu (le byte le plus à gauche étant le byte le moins significatif). Par exemple, le nombre de 10.001 base 10, avec une échelle de 4, est réduit à un intégrant de 100010. Parce que c’est 186AA dans le format hexadecimal, la valeur dans SQL_NUMERIC_STRUCT serait "AA 86 01 00 00 ... 00", avec le nombre d’octets définis par le SQL_MAX_NUMERIC_LEN **#define**.  
  
 Pour plus d’informations sur **SQL_NUMERIC_STRUCT**, voir [HOWTO: Retrieving Numeric Data avec SQL_NUMERIC_STRUCT](retrieve-numeric-data-sql-numeric-struct-kb222831.md).  
  
 [f] Les champs de précision et d’échelle du type de données SQL_C_NUMERIC sont utilisés pour l’entrée d’une application et pour la sortie du conducteur à l’application. Lorsque le conducteur écrit une valeur numérique dans le SQL_NUMERIC_STRUCT, il utilisera son propre défaut spécifique au conducteur comme valeur pour le champ *de précision,* et il utilisera la valeur dans le champ SQL_DESC_SCALE du descripteur d’application (qui par défaut à 0) pour le champ *d’échelle.* Une application peut fournir ses propres valeurs de précision et d’échelle en définissant les champs SQL_DESC_PRECISION et SQL_DESC_SCALE du descripteur d’application.  
  
 [g] Le champ de signalisation est 1 si positif, 0 si négatif.  
  
 [h] _int64 pourrait ne pas être fourni par certains compilateurs.  
  
 [i] _SQL_C_BOOKMARK a été déprécié dans ODBC 3 *.x*.  
  
 [j] _SQL_C_SHORT, SQL_C_LONG et SQL_C_TINYINT ont été remplacés en ODBC par des types signés et non signés : SQL_C_SSHORT et SQL_C_USHORT, SQL_C_SLONG et SQL_C_ULONG, et SQL_C_STINYINT et SQL_C_UTINYINT. Un pilote ODBC 3 *.x* qui devrait travailler avec ODBC 2. *x* les applications doivent prendre en charge SQL_C_SHORT, SQL_C_LONG et SQL_C_TINYINT, parce que lorsqu’ils sont appelés, le gestionnaire de conducteur les transmet au conducteur.  
  
 [k] SQL_C_GUID ne peut être converti qu’en SQL_CHAR ou en SQL_WCHAR.  
  
 Cette section contient le sujet suivant.  
  
-   [Structures d’entiers 64 bits](../../../odbc/reference/appendixes/64-bit-integer-structures.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données C dans ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)

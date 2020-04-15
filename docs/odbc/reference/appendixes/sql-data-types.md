---
title: Types de données SQL Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL data types [ODBC]
- SQL data types [ODBC], about SQL data types
- data types [ODBC], SQL data types
ms.assetid: 1b22f985-f5e4-4779-87eb-e43329a442b1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3cc91213533aa39f30be1bc838cc014c20e70884
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305003"
---
# <a name="sql-data-types"></a>Types de données SQL
Chaque DBMS définit ses propres types SQL. Chaque conducteur ODBC n’expose que les types de données SQL que le DBMS associé définit. L’information sur la façon dont un conducteur cartographie les types DBMS SQL aux identificateurs de type SQL définis par LBC et comment un conducteur cartographie les types DBMS SQL à ses propres identificateurs de type SQL spécifiques au conducteur est retournée par un appel à **SQLGetTypeInfo**. Un conducteur retourne également les types de données SQL lorsqu’il décrit les types de données de colonnes et de paramètres par le biais d’appels à **SQLColAttribute**, **SQLColumns**, **SQLDescribeCol**, **SQLDescribeParam**, **SQLProcedureColumns**, et **SQLSpecialColumns**.  
  
> [!NOTE]  
>  Les types de données SQL sont contenus dans les domaines SQL_DESC_ CONCISE_TYPE, SQL_DESC_TYPE et SQL_DESC_DATETIME_INTERVAL_CODE des descripteurs de mise en œuvre. Les caractéristiques des types de données SQL sont contenues dans les domaines SQL_DESC_PRECISION, SQL_DESC_SCALE, SQL_DESC_LENGTH et SQL_DESC_OCTET_LENGTH des descripteurs de mise en œuvre. Pour plus d’informations, consultez [les identifiants de type de données et les descripteurs](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md) plus tard dans cette annexe.  
  
 Un conducteur et une source de données donnés ne prennent pas nécessairement en charge tous les types de données SQL qui sont définis dans cette annexe. Le soutien d’un conducteur pour les types de données SQL dépend du niveau de SQL-92 auquel le conducteur se conforme. Pour déterminer le niveau de grammaire SQL-92 supporté par le conducteur, une application appelle **SQLGetInfo** avec le type d’information SQL_SQL_CONFORMANCE. De plus, un conducteur et une source de données donnés peuvent prendre en charge d’autres types de données SQL spécifiques au conducteur. Pour déterminer quels types de données un conducteur prend en charge, une application appelle **SQLGetTypeInfo**. Pour obtenir de l’information sur les types de données SQL spécifiques au conducteur, consultez la documentation du conducteur. Pour plus d’informations sur les types de données dans une source de données spécifique, consultez la documentation de cette source de données.  
  
> [!IMPORTANT]  
>  Les tableaux tout au long de cette annexe ne sont que des lignes directrices et montrent généralement les noms, les plages et les limites des types de données SQL. Une source de données donnée ne peut prendre en charge que certains des types de données énumérés, et les caractéristiques des types de données pris en charge peuvent différer de celles énumérées.  
  
 Le tableau suivant répertorie les identifiants valides de type SQL pour tous les types de données SQL. Le tableau énumère également le nom et la description du type de données correspondant de SQL-92 (s’il y en a).  
  
|Identifiant de type SQL[1]|Données SQL typiques<br /><br /> type[2]|Description de type typique|  
|------------------------------|------------------------------------|------------------------------|  
|SQL_CHAR|CHAR(*n*)|Chaîne de caractère de longueur de corde fixe *n*.|  
|SQL_VARCHAR|VARCHAR(*n*)|Chaîne de caractère à longueur variable avec une longueur maximale de chaîne *n*.|  
|SQL_LONGVARCHAR|LONG VARCHAR|Données de caractères de longueur variable. La longueur maximale dépend de la source de données. [9]|  
|SQL_WCHAR|WCHAR(*n*)|Chaîne de caractère Unicode de longueur de chaîne fixe *n*|  
|SQL_WVARCHAR|VARWCHAR(*n*)|Chaîne de caractères à longueur variable Unicode avec une longueur de chaîne maximale *n*|  
|SQL_WLONGVARCHAR|LONGWVARCHAR (LONGWVARCHAR)|Données de caractères de longueur variable Unicode. La longueur maximale dépend de la source de données|  
|SQL_DECIMAL|DECIMAL(*p*,*s*)|Valeur numérique signée, exacte, avec une précision *d’au* moins *p* et échelle s. (La précision maximale est définie par le conducteur.) (1 <*p* <15; *p* <= *).* [4]|  
|SQL_NUMERIC|NUMERIC (*p*,*s*)|Valeur numérique signée, exacte avec un *p* de précision et une balance *s* (1 <' *p* <'15; *p* <= *).* [4]|  
|SQL_SMALLINT|SMALLINT|Valeur numérique exacte avec précision 5 et échelle 0 (signé : -32 768 <*n* <32 767, non signé : 0 <et *n* <65 535)[3].|  
|SQL_INTEGER|INTEGER|Valeur numérique exacte avec précision 10 et échelle 0 (signée : -2[31] <*n* <2[31] - 1, non signé : 0 <*'n* <'2[32] - 1)[3].|  
|SQL_REAL|real|Valeur numérique signée, approximative, avec une précision binaire 24 (valeur zéro ou absolue 10[-38] à 10[38]).|  
|SQL_FLOAT|FLOAT(*p*)|Valeur numérique signée, approximative, avec une précision binaire d’au moins *p*. (La précision maximale est définie par le conducteur.) [5]|  
|SQL_DOUBLE|DOUBLE PRECISION|Valeur numérique signée, approximative, avec une précision binaire 53 (valeur zéro ou absolue 10[-308] à 10[308]).|  
|SQL_BIT|BIT|Données binaires à bit unique. [8]|  
|SQL_TINYINT|TINYINT|Valeur numérique exacte avec précision 3 et échelle 0 (signée : -128 <*n* <127, non signée : 0 <*n* <255)[3].|  
|SQL_BIGINT|bigint|Valeur numérique exacte avec précision 19 (si elle est signée) ou 20 (si non signée) et échelle 0 (signée : -2[63] <*n* <2[63] - 1, non signé : 0 <*n* <2[64] - 1)[3],[9].|  
|SQL_BINARY|BINARY(*n*)|Données binaires de longueur fixe *n*. [9]|  
|SQL_VARBINARY|VARBINARY(*n*)|Données binaires de longueur variable de longueur maximale *n*. Le maximum est défini par l’utilisateur. [9]|  
|SQL_LONGVARBINARY|LONG VARBINAIRE|Données binaires de longueur variable. La longueur maximale dépend de la source de données. [9]|  
|SQL_TYPE_DATE[6]|DATE|Champs d’année, de mois et de jour, conformes aux règles du calendrier grégorien. (Voir [Contraintes du Calendrier grégorien](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md), plus tard dans cette annexe.)|  
|SQL_TYPE_TIME[6]|TEMPS(*p*)|Heures, minutes et deuxièmes champs, avec des valeurs valides pour des heures de 00 à 23, des valeurs valides pour des minutes de 00 à 59, et des valeurs valides pour les secondes de 00 à 61. Precision *p* indique la précision des secondes.|  
|SQL_TYPE_TIMESTAMP[6]|TIMESTAMP(*p*)|Année, mois, jour, heure, minute et deuxième champs, avec des valeurs valides telles que définies pour les types de données DATE et TIME.|  
|SQL_TYPE_UTCDATETIME|UTCDATETIME (EN ANGLAIS)|Année, mois, jour, heure, minute, deuxième, utchour, et les champs utcminute. Les champs d’utchour et d’utcminute ont une précision de 1/10 microseconde.|  
|SQL_TYPE_UTCTIME|UTCTIME (EN anglais)|Des champs d’heure, de minute, de seconde, d’utchour et d’utcminute. Les champs d’utchour et d’utcminute ont une précision de 1/10 microseconde.|  
|SQL_INTERVAL_MONTH[7]|INTERVAL MONTH(*p*)|Nombre de mois entre deux dates; *p* est la précision de pointe d’intervalle.|  
|SQL_INTERVAL_YEAR[7]|ANNÉE D’INTERVALLE (*p*)|Nombre d’années entre deux dates; *p* est la précision de pointe d’intervalle.|  
|SQL_INTERVAL_YEAR_TO_MONTH[7]|ANNÉE D’INTERVALLE *(P)* AU MOIS|Nombre d’années et de mois entre deux dates; *p* est la précision de pointe d’intervalle.|  
|SQL_INTERVAL_DAY[7]|INTERVAL DAY(*p*)|Nombre de jours entre deux dates; *p* est la précision de pointe d’intervalle.|  
|SQL_INTERVAL_HOUR[7]|INTERVAL HOUR(*p*)|Nombre d’heures entre deux dates/heures; *p* est la précision de pointe d’intervalle.|  
|SQL_INTERVAL_MINUTE[7]|MINUTE INTERVAL(*p*)|Nombre de minutes entre deux dates/heures; *p* est la précision de pointe d’intervalle.|  
|SQL_INTERVAL_SECOND[7]|INTERVAL SECOND(*p*,*q*)|Nombre de secondes entre deux dates/heures; *p* est la précision de tête d’intervalle et *q* est la précision des secondes d’intervalle.|  
|SQL_INTERVAL_DAY_TO_HOUR[7]|JOUR D’INTERVALLE (*P*) À L’HEURE|Nombre de jours/heures entre deux dates/heures; *p* est la précision de pointe d’intervalle.|  
|SQL_INTERVAL_DAY_TO_MINUTE[7]|JOUR D’INTERVALLE (*P*) À LA MINUTE|Nombre de jours/heures/minutes entre deux dates/heures; *p* est la précision de pointe d’intervalle.|  
|SQL_INTERVAL_DAY_TO_SECOND[7]|INTERVAL DAY(*p*) TO SECOND(*q*)|Nombre de jours/heures/minutes/secondes entre deux dates/heures; *p* est la précision de tête d’intervalle et *q* est la précision des secondes d’intervalle.|  
|SQL_INTERVAL_HOUR_TO_MINUTE[7]|HEURE D’INTERVALLE *(P)* À LA MINUTE|Nombre d’heures/minutes entre deux dates/heures; *p* est la précision de pointe d’intervalle.|  
|SQL_INTERVAL_HOUR_TO_SECOND[7]|INTERVAL HOUR(*p*) TO SECOND(*q*)|Nombre d’heures/minutes/secondes entre deux dates/heures; *p* est la précision de tête d’intervalle et *q* est la précision des secondes d’intervalle.|  
|SQL_INTERVAL_MINUTE_TO_SECOND[7]|INTERVAL MINUTE(*p*) TO SECOND(*q*)|Nombre de minutes/secondes entre deux dates/heures; *p* est la précision de tête d’intervalle et *q* est la précision des secondes d’intervalle.|  
|SQL_GUID|GUID|GuiD de longueur fixe.|  
  
 [1] C’est la valeur retournée dans la colonne DATA_TYPE par un appel à **SQLGetTypeInfo**.  
  
 [2] C’est la valeur retournée dans la colonne NOM et CREATE PARAMS par un appel à **SQLGetTypeInfo**. La colonne NAME renvoie la désignation - par exemple, CHAR - alors que la colonne CREATE PARAMS renvoie une liste de paramètres de création séparées par virgule tels que la précision, l’échelle et la longueur.  
  
 [3] Une application utilise **SQLGetTypeInfo** ou **SQLColAttribute** pour déterminer si un type de données particulier ou une colonne particulière dans un ensemble de résultats n’est pas signé.  
  
 [4] les types de données SQL_DECIMAL et SQL_NUMERIC ne diffèrent que par leur précision. La précision d’un DECIMAL (*p*,*s*) est une précision décimale définie par implémentation qui n’est pas moins de *p*, alors que la précision d’un NUMERIC (*p*,*s*) est exactement égale à *p*.  
  
 [5] Selon la mise en œuvre, la précision de SQL_FLOAT peut être soit 24 ou 53 : s’il est de 24, le type de données SQL_FLOAT est le même que SQL_REAL ; s’il est 53, le type de données SQL_FLOAT est le même que SQL_DOUBLE.  
  
 [6] Dans ODBC *3.x*, la date, l’heure et les types de données de décalage horaires sont SQL_TYPE_DATE, SQL_TYPE_TIME et SQL_TYPE_TIMESTAMP, respectivement ; dans ODBC *2.x*, les types de données sont SQL_DATE, SQL_TIME et SQL_TIMESTAMP.  
  
 [7] Pour plus d’informations sur les types de données SQL d’intervalle, consultez la section [Types de données d’intervalle,](../../../odbc/reference/appendixes/interval-data-types.md) plus tard dans cette annexe.  
  
 [8] Le type de données SQL_BIT a des caractéristiques différentes du type BIT dans SQL-92.  
  
 [9] Ce type de données n’a pas de type de données correspondante dans SQL-92.  
  
 Cette section donne l’exemple suivant.  
  
-   [Exemple de jeu de résultats de SQLGetTypeInfo](../../../odbc/reference/appendixes/example-sqlgettypeinfo-result-set.md)

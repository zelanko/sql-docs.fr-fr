---
title: DateTimeOffset (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- datetimeoffset_TSQL
- datetimeoffset
dev_langs:
- TSQL
helpviewer_keywords:
- time [SQL Server], data types
- date and time [SQL Server], datetimeoffset
- datetimeoffset data type [SQL Server]
- dates [SQL Server], data types
- data types [SQL Server], date and time
- time zones [SQL Server]
ms.assetid: a0455b71-ca25-476e-a7a8-0770f1860bb7
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9a6c143380711d1af39a6c11f311e9ce3caf87c7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="datetimeoffset-transact-sql"></a>datetimeoffset (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Définit une date qui est associée à une heure de la journée qui prend en charge les fuseaux horaires et se présente au format 24 heures.
  
## <a name="datetimeoffset-description"></a>description de DateTimeOffset
  
|Propriété|Valeur|  
|---|---|
|Syntaxe|**DateTimeOffset** [(*précision de fractions de seconde*)]|  
|Utilisation|DÉCLARER @MyDatetimeoffset **datetimeoffset(7)**<br /><br /> CRÉER la TABLE Table1 (Column1 **datetimeoffset(7)** )|  
|Formats de littéraux de chaîne par défaut (utilisés pour le client de bas niveau)|AAAA-MM-JJ HH : mm : [.nnnnnnn] [{+ &#124;-} hh : mm]<br /><br /> Pour plus d’informations, consultez la section « Compatibilité descendante pour les Clients de bas niveau » qui suit.|  
|Plage de dates|0001-01-01 à 9999-12-31<br /><br /> Le 1er janvier 1 CE et le 31 décembre 9999 CE|  
|Plage temporelle|00:00:00 à 23:59:59.9999999 (les fractions de secondes ne sont pas pris en charge dans Informatica)|  
|Plage de décalages de fuseau horaire|-14:00 et + 14:00 (décalage de fuseau horaire est ignoré dans Informatica)|  
|Plages d'éléments|AAAA comprend quatre chiffres, entre 0001 et 9999, qui représentent une année.<br /><br /> MM est deux chiffres, entre 01 et 12, qui représentent un mois dans l’année spécifiée.<br /><br /> DD est à deux chiffres, entre 01 et 31 selon le mois, qui représentent un jour du mois spécifié.<br /><br /> hh comprend deux chiffres, entre 00 et 23, qui représentent l'heure.<br /><br /> mm comprend deux chiffres, entre 00 et 59, qui représentent la minute.<br /><br /> ss comprend deux chiffres, entre 00 et 59, qui représentent la seconde.<br /><br /> n* comprend entre zéro et sept chiffres, entre 0 et 9999999, qui représentent les fractions de seconde. Les fractions de secondes ne sont pas pris en charge dans Informatica.<br /><br /> hh comprend deux chiffres, entre -14 et +14. Le décalage de fuseau horaire est ignoré dans Informatica.<br /><br /> mm comprend deux chiffres, entre 00 et 59. Le décalage de fuseau horaire est ignoré dans Informatica.|  
|Longueur de caractère|26 positions au minimum (AAAA-MM-JJ HH : mm : {+ &#124;-} hh : mm) et 34 au maximum (AAAA-MM-JJ.nnnnnnn {+ &#124;-} hh : mm)|  
|Précision, échelle|Consultez le tableau ci-dessous.|  
|Taille de stockage|10 octets, fixes, sont la valeur par défaut avec une précision à la fraction de seconde de 100 ns par défaut.|  
|Analyse de précision|100 nanosecondes|  
|Valeur par défaut|1900-01-01 00:00:00 00:00|  
|Calendrier|Grégorien|  
|Précision à la fraction de seconde définie par l'utilisateur|Oui|  
|Prise en charge et conservation du décalage de fuseau horaire|Oui|  
|Prise en charge de l'heure d'été|Non|  
  
|Échelle spécifiée|Résultat (précision, échelle)|Longueur de colonne (octets)|Précision en fractions de seconde|  
|---|---|---|---|
|**datetimeoffset**|(34,7)|10|7|  
|**DateTimeOffset(0)**|(26,0)|8|0-2|  
|**DateTimeOffset(1)**|(28,1)|8|0-2|  
|**DateTimeOffset(2)**|(29,2)|8|0-2|  
|**DateTimeOffset(3)**|(30,3)|9|3-4|  
|**DateTimeOffset(4)**|(31,4)|9|3-4|  
|**DateTimeOffset(5)**|(32,5)|10|5-7|  
|**DateTimeOffset(6)**|(33,6)|10|5-7|  
|**DateTimeOffset(7)**|(34,7)|10|5-7|  
  
## <a name="supported-string-literal-formats-for-datetimeoffset"></a>Prise en charge des formats de littéraux de chaîne pour datetimeoffset
Le tableau suivant répertorie les prise en charge ISO 8601 formats littéraux de chaîne pour **datetimeoffset**. Pour plus d’informations sur les formats alphabétique, numériques, non séparées et le temps pour les parties de date et heure de **datetimeoffset**, consultez [date &#40; Transact-SQL &#41; ](../../t-sql/data-types/date-transact-sql.md) et [temps &#40; Transact-SQL &#41; ](../../t-sql/data-types/time-transact-sql.md).
  
|ISO 8601| Description|  
|---|---|
|AAAA-MM-JJThh [.nnnnnnn] [{+ &#124;-} hh : mm]|Ces deux formats ne sont pas affectés par les paramètres régionaux de session SET LANGUAGE et SET DATEFORMAT. Les espaces ne sont pas autorisés entre les **datetimeoffset** et **datetime** parties.|  
|AAAA-MM-JJThh:mm:ss[.nnnnnnn]Z (UTC)|Ce format par définition ISO indique le **datetime** partie doit être exprimée en temps universel coordonné (UTC). Par exemple, 1999-12-12 12:30:30.12345 -07:00 doit être représenté sous la forme 1999-12-12 19:30:30.12345Z.|  
  
## <a name="time-zone-offset"></a>Décalage de fuseau horaire
Un décalage de fuseau horaire Spécifie le décalage de fuseau UTC pour un **temps** ou **datetime** valeur. Le décalage de fuseau horaire peut être représenté sous la forme [+|-] hh:mm:
-   hh comprend deux chiffres, entre 00 et 14, qui représentent le nombre d'heures dans le décalage de fuseau horaire.  
-   mm comprend deux chiffres, entre 00 et 59, qui représentent le nombre de minutes supplémentaires dans le décalage de fuseau horaire.  
-   \+(plus) ou – (moins) est le signe obligatoire d’un décalage de fuseau horaire. Indique si le décalage de fuseau horaire est ajouté ou soustrait de l’heure UTC pour obtenir l’heure locale. La plage valide du décalage de fuseau horaire se situe entre -14:00 et +14:00.  
  
La plage des décalages de fuseau horaire respecte la norme XML W3C pour la définition de schéma XSD et est légèrement différente de la définition de la norme SQL 2003, 12:59 à +14:00.
  
Le paramètre de type facultatif *précision de fractions de seconde* Spécifie le nombre de chiffres pour la partie fractionnaire des secondes. Cette valeur peut être un entier avec 0 à 7 chiffres (100 nanosecondes). La valeur par défaut *précision de fractions de seconde* est 100 NS (sept chiffres pour la partie fractionnaire des secondes).
  
Les données sont stockées dans la base de données, puis traitées, comparées, triées et indexées sur le serveur comme au format UTC. Le décalage de fuseau horaire sera conservé dans la base de données pour récupération.
  
Le décalage de fuseau horaire donné sera considéré comme étant l’heure d’été (DST) prenant en charge et réglé pour tout donné **datetime** qui se trouve dans la période d’heure d’été.
  
Pour **datetimeoffset** type, l’heure UTC et locale (pour le décalage de fuseau horaire persistant ou préservé) **datetime** valeur sera validée pendant l’insertion, mise à jour, arithmétique, convert ou affecter les opérations. La détection de UTC ou locale (pour le décalage de fuseau horaire persistant ou préservé) non valide **datetime** valeur génère une erreur de valeur non valide. Par exemple, 9999-12-31 10:10:00 est valide au format UTC, mais déborde en heure locale sur le décalage de fuseau horaire +13:50.
  
Pour convertir une date correspondant **datetimeoffset** valeur dans une cible de fuseau horaire, consultez [AT TIME ZONE &#40; Transact-SQL &#41; ](../../t-sql/queries/at-time-zone-transact-sql.md).
  
## <a name="ansi-and-iso-8601-compliance"></a>Conformité ANSI et ISO 8601  
Les sections ANSI et ISO 8601 conformité de la [date](../../t-sql/data-types/date-transact-sql.md) et [temps](../../t-sql/data-types/time-transact-sql.md) rubriques s’appliquent à **datetimeoffset**.
  
## <a name="backward-compatibility-for-down-level-clients"></a>Compatibilité descendante pour les clients de bas niveau
Certains clients de bas niveau ne gèrent pas la **temps**, **date**, **datetime2** et **datetimeoffset** des types de données. Le tableau suivant présente le type de mappage entre une instance de haut niveau de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et des clients de bas niveau.
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de données|Format de littéral de chaîne par défaut passé au client de bas niveau|ODBC de bas niveau|OLEDB de bas niveau|JDBC de bas niveau|SQLCLIENT de bas niveau|  
|---|---|---|---|---|---|
|**time**|hh:mm:ss [.nnnnnnn]|SQL_WVARCHAR ou SQL_VARCHAR|DBTYPE_WSTR ou DBTYPE_STR|Java.sql.String|String ou SqString|  
|**date**|AAAA-MM-JJ|SQL_WVARCHAR ou SQL_VARCHAR|DBTYPE_WSTR ou DBTYPE_STR|Java.sql.String|String ou SqString|  
|**datetime2**|AAAA-MM-JJ hh:mm:ss[.nnnnnnn]|SQL_WVARCHAR ou SQL_VARCHAR|DBTYPE_WSTR ou DBTYPE_STR|Java.sql.String|String ou SqString|  
|**datetimeoffset**|AAAA-MM-JJ HH : mm : [.nnnnnnn] [+ &#124;-] HH : mm|SQL_WVARCHAR ou SQL_VARCHAR|DBTYPE_WSTR ou DBTYPE_STR|Java.sql.String|String ou SqString|  
  
## <a name="converting-date-and-time-data"></a>Conversion des données de date et d’heure
Lorsque vous effectuez une conversion vers des types de données date et heure, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rejette toutes les valeurs qu'il ne peut identifier comme dates ou heures. Pour plus d’informations sur l’utilisation des fonctions CAST et CONVERT avec des données de date et d’heure, consultez [CAST et CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
Lors de la conversion à **date**, l’année, mois et jour sont copiés. Le code suivant montre les résultats de la conversion d'une valeur `datetimeoffset(4)` en valeur `date`.  
  
```sql
DECLARE @datetimeoffset datetimeoffset(4) = '12-10-25 12:32:10 +01:00';  
DECLARE @date date= @datetimeoffset;  
  
SELECT @datetimeoffset AS '@datetimeoffset ', @date AS 'date';  
  
--Result  
--@datetimeoffset                date  
-------------------------------- ----------  
--2025-12-10 12:32:10.0000 +01:0 2025-12-10  
--  
--(1 row(s) affected)  
  
```  
  
Si la conversion consiste à **Time (n)**, notre, minutes, les secondes et fractions de seconde sont copiées. La valeur de fuseau horaire est tronquée. Lorsque la précision de la **DateTimeOffset (n)** valeur est supérieure à la précision de la **Time (n)** valeur, la valeur est arrondie. Le code suivant montre les résultats de la conversion d'une valeur `datetimeoffset(4)` en valeur `time(3)`.
  
```sql
DECLARE @datetimeoffset datetimeoffset(4) = '12-10-25 12:32:10.1237 +01:0';  
DECLARE @time time(3) = @datetimeoffset;  
  
SELECT @datetimeoffset AS '@datetimeoffset ', @time AS 'time';  
  
--Result  
--@datetimeoffset                time  
-------------------------------- ------------  
-- 2025-12-10 12:32:10.1237 +01:00    12:32:10.124  
  
--  
--(1 row(s) affected)  
  
```  
  
Lors de la conversion à**datetime**, les valeurs de date et d’heure sont copiées et le fuseau horaire est tronqué. Lorsque la précision de fraction de la **DateTimeOffset (n)** valeur est supérieure à trois chiffres, la valeur est tronquée. Le code suivant montre les résultats de la conversion d'une valeur `datetimeoffset(4)` en valeur `datetime`.
  
```sql
DECLARE @datetimeoffset datetimeoffset(4) = '12-10-25 12:32:10.1237 +01:0';  
DECLARE @datetime datetime = @datetimeoffset;  
  
SELECT @datetimeoffset AS '@datetimeoffset ', @datetime AS 'datetime';  
  
--Result  
--@datetimeoffset                datetime  
-------------------------------- -----------------------  
--2025-12-10 12:32:10.1237 +01:0 2025-12-10 12:32:10.123  
--  
--(1 row(s) affected)  
```  
  
Pour les conversions **smalldatetime**, la date et heures sont copiées. Les minutes sont arrondies selon la valeur des secondes et les secondes sont définies sur 0. Le code suivant montre les résultats de la conversion d'une valeur `datetimeoffset(3)` en valeur `smalldatetime`.  
  
```sql
DECLARE @datetimeoffset datetimeoffset(3) = '1912-10-25 12:24:32 +10:0';  
DECLARE @smalldatetime smalldatetime = @datetimeoffset;  
  
SELECT @datetimeoffset AS '@datetimeoffset', @smalldatetime AS '@smalldatetime';  
  
--Result  
--@datetimeoffset                @smalldatetime  
-------------------------------- -----------------------  
--1912-10-25 12:24:32.000 +10:00 1912-10-25 12:25:00  
--  
--(1 row(s) affected)  
```  
  
Si la conversion consiste à **datetime2**, la date et l’heure sont copiés vers le **datetime2** valeur et le fuseau horaire est tronqué. Lorsque la précision de la **datetime2** valeur est supérieure à la précision de la **DateTimeOffset (n)** valeur, les fractions de seconde sont tronquées en fonction. Le code suivant montre les résultats de la conversion d'une valeur `datetimeoffset(4)` en valeur `datetime2(3)`.
  
```sql
DECLARE @datetimeoffset datetimeoffset(4) = '1912-10-25 12:24:32.1277 +10:0';  
DECLARE @datetime2 datetime2(3)=@datetimeoffset;  
  
SELECT @datetimeoffset AS '@datetimeoffset', @datetime2 AS '@datetime2';  
  
--Result  
@datetimeoffset                    @datetime2  
---------------------------------- ----------------------  
1912-10-25 12:24:32.1277 +10:00    1912-10-25 12:24:32.12  
  
--(1 row(s) affected)  
```  
  
### <a name="converting-datetimeoffset-data-type-to-other-date-and-time-types"></a>Conversion de type de données datetimeoffset vers une autre date types et d’heure
Le tableau suivant décrit ce qui se produit lorsqu’un **datetimeoffset** type de données est converti en autres types de données de date et d’heure.
  
### <a name="converting-string-literals-to-datetimeoffset"></a>Conversion de littéraux de chaîne en datetimeoffset
Les conversions de littéraux de chaîne en types de date et d'heure sont autorisées si toutes les parties des chaînes sont dans des formats valides. Sinon, une erreur d'exécution est déclenchée. Les conversions implicites ou explicites qui ne spécifient pas de style à partir de types de date et d'heure en littéraux de chaîne seront au format par défaut de la session active. Le tableau suivant présente les règles de conversion d’une chaîne littérale pour le **datetimeoffset** type de données.
  
|Littéral de chaîne d'entrée|**DateTimeOffset (n)**|  
|---|---|
|ODBC DATE|Littéraux de chaîne ODBC sont mappées à la **datetime** type de données. Toute opération d’affectation de littéraux ODBC DATETIME en **datetimeoffset** provoquent une conversion implicite entre types **datetime** et ce type, tel que défini par les règles de conversion.|  
|ODBC TIME|Consultez la règle DATE ODBC précédente.|  
|ODBC DATETIME|Consultez la règle DATE ODBC précédente.|  
|DATE uniquement|La partie TIME a pour valeur par défaut 00:00:00. TIMEZONE a pour valeur par défaut +00:00.|  
|TIME uniquement|La partie DATE a pour valeur par défaut 1900-1-1. TIMEZONE aura pour valeur par défaut +00:00.|  
|TIMEZONE uniquement|Les valeurs par défaut sont fournies|  
|DATE + TIME|TIMEZONE a pour valeur par défaut +00:00.|  
|DATE + TIMEZONE|Non autorisées|  
|TIME + TIMEZONE|La partie DATE a pour valeur par défaut 1900-1-1.|  
|DATE + TIME + TIMEZONE|Trivial|  
  
## <a name="examples"></a>Exemples  
L’exemple suivant compare les résultats de la conversion d’une chaîne en chaque **date** et **temps** type de données.
  
```sql
SELECT   
     CAST('2007-05-08 12:35:29. 1234567 +12:15' AS time(7)) AS 'time'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS date) AS 'date'   
    ,CAST('2007-05-08 12:35:29.123' AS smalldatetime) AS   
        'smalldatetime'   
    ,CAST('2007-05-08 12:35:29.123' AS datetime) AS 'datetime'   
    ,CAST('2007-05-08 12:35:29.1234567+12:15' AS datetime2(7)) AS   
        'datetime2'  
    ,CAST('2007-05-08 12:35:29.1234567 +12:15' AS datetimeoffset(7)) AS   
        'datetimeoffset'  
    ,CAST('2007-05-08 12:35:29.1234567+12:15' AS datetimeoffset(7)) AS  
        'datetimeoffset IS08601';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
|Type de données|Sortie|  
|---|---|
|**Time**|12:35:29. 1234567|  
|**Date**|2007-05-08|  
|**Smalldatetime**|2007-05-08 12:35:00|  
|**DateTime**|2007-05-08 12:35:29.123|  
|**datetime2**|2007-05-08 12:35:29. 1234567|  
|**DateTimeOffset**|2007-05-08 12:35:29.1234567 +12:15|  
  
## <a name="see-also"></a>Voir aussi
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[FUSEAU horaire &AMP; #40 ; Transact-SQL &#41;](../../t-sql/queries/at-time-zone-transact-sql.md)
  
  


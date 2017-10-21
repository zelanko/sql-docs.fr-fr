---
title: Date (Transact-SQL) | Documents Microsoft
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
- date_TSQL
- date
dev_langs:
- TSQL
helpviewer_keywords:
- data types [SQL Server], date
- date and time [SQL Server], date
- dates [SQL Server], data types
- date data type [SQL Server]
- data types [SQL Server], date and time
ms.assetid: c963e8b4-5a85-4bd0-9d48-3f8da8f6516b
caps.latest.revision: 44
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5c5d3a52b6163f375850b22e27baf9a858ef8ed8
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="date-transact-sql"></a>date (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Définit une date dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
## <a name="date-description"></a>description de la date
  
|Propriété|Valeur|  
|--------------|-----------|  
|Syntaxe|**date**|  
|Utilisation|DÉCLARER @MyDate **date**<br /><br /> CRÉER une TABLE Table1 (Column1 **date** )|  
|Format de littéral de chaîne par défaut<br /><br /> (utilisé pour le client de bas niveau)|AAAA-MM-JJ<br /><br /> Pour plus d’informations, consultez la section « Compatibilité descendante pour les Clients de bas niveau » qui suit.|  
|Plage|0001-01-01 et 9999-12-31 (1582-10-15 et 9999-12-31 pour Informatica)<br /><br /> Le 1er janvier 1 CE et le 31 décembre 9999 CE (CE 15 octobre 1582 et le 31 décembre, CE 9999 pour Informatica)|  
|Plages d'éléments|AAAA représente les quatre chiffres à 0001 et 9999 qui représente une année. Pour Informatica, AAAA est limitée à 1582 à 9999.<br /><br /> MM comprend deux chiffres, entre 01 et 12, qui représentent un mois de l'année spécifiée.<br /><br /> DD comprend deux chiffres, entre 01 et 31 selon le mois, qui représentent un jour du mois spécifié.|  
|Longueur de caractère|10 positions|  
|Précision, échelle|10, 0|  
|Taille de stockage|3 octets, fixe|  
|Structure de stockage|Un entier sur 1 ou 3 octets stocke la date.|  
|Analyse de précision|Un jour|  
|Valeur par défaut|1900-01-01<br /><br /> Cette valeur est utilisée pour la partie date ajoutée pour la conversion implicite de **temps** à **datetime2** ou **datetimeoffset**.|  
|Calendrier|Grégorien|  
|Précision à la fraction de seconde définie par l'utilisateur|Non|  
|Prise en charge et conservation du décalage de fuseau horaire|Non|  
|Prise en charge de l'heure d'été|Non|  
  
## <a name="supported-string-literal-formats-for-date"></a>Prise en charge des formats de littéraux de chaîne de date
Les tableaux suivants indiquent la chaîne valide pour les formats de littéraux le **date** type de données.
  
|Numérique| Description|  
|-------------|-----------------|  
|mja<br /><br /> [m]m/jj/[aa]aa<br /><br /> [m]m-jj-[aa]aa<br /><br /> [m]m.jj.[aa]aa<br /><br /> maj<br /><br /> mm/[aa]aa/jj<br /><br /> mm-[aa] AA/jj<br /><br /> [m]m.[aa]aa.jj<br /><br /> jma<br /><br /> jj/[m]m/[aa]aa<br /><br /> jj-[m]m-[aa]aa<br /><br /> jj.[m]m.[aa]aa<br /><br /> jam<br /><br /> jj/[aa]aa/[m]m<br /><br /> jj-[aa]aa-[m]m<br /><br /> jj.[aa]aa.[m]m<br /><br /> amj<br /><br /> [aa] AA / [m] m/jj<br /><br /> [aa]aa-[m]m-jj<br /><br /> [aa]aa-[m]m-jj|[m]m, jj et [aa]aa représentent le mois, le jour et l'année dans une chaîne qui utilise des barres obliques (/), des traits d'union (-) ou des points (.) comme séparateurs.<br /><br /> Seules les années à deux ou quatre chiffres sont prises en charge. Utilisez des années à quatre chiffres chaque fois que possible. Pour spécifier un entier compris entre 0001 et 9999 qui représente l’année de coupure pour interpréter les années à deux chiffres comme des années à quatre chiffres, utilisez le [configurer l’année à deux chiffres cutoff Server Configuration Option](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).<br /><br /> **Remarque** Pour Informatica, AAAA est limitée à 1582 à 9999.<br /><br /> Une année à deux chiffres inférieure ou égale aux deux derniers chiffres de l'année de coupure appartient au même siècle que l'année de coupure. Une année à deux chiffres supérieure aux deux derniers chiffres de l'année de coupure appartient au siècle qui précède l'année de coupure. Par exemple, si l'année de coupure à deux chiffres est l'année par défaut 2049, l'année à deux chiffres 49 est interprétée comme étant 2049 et l'année 50 comme étant 1950<br /><br /> Le format de date par défaut est déterminé par le paramètre de langue actuel. Vous pouvez modifier le format de date à l’aide de la [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md) et [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md) instructions.<br /><br /> Le **ydm** format n’est pas pris en charge pour **date**.|  
  
|Alphabétique| Description|  
|------------------|-----------------|  
|mois [jj][,] aaaa<br /><br /> mois jj[,] [aa]aa<br /><br /> mois aaaa [jj]<br /><br /> [jj] mois[,] aaaa<br /><br /> jj mois[,][aa]aa<br /><br /> jj [aa]aa mois<br /><br /> [jj] aaaa mois<br /><br /> aaaa mois [jj]<br /><br /> aaaa [jj] mois|**LUN** représente le nom complet du mois ou l’abréviation du mois donné dans la langue actuelle. Les virgules sont facultatives et les majuscules sont ignorées.<br /><br /> Pour éviter toute ambiguïté, représentez les années à l'aide de quatre chiffres.<br /><br /> Si le jour n'est pas précisé, le premier jour du mois est rajouté.|  
  
|ISO 8601|Description|  
|--------------|----------------|  
|AAAA-MM-JJ<br /><br /> AAAAMMJJ|Identique à la norme SQL. Il s'agit du seul format qui est défini comme une norme internationale.|  
  
|Non séparé| Description|  
|-----------------|-----------------|  
|[aa]aammjj<br /><br /> aaaa[mm][jj]|Le **date** données peuvent être spécifiées avec quatre, six ou huit chiffres. Une chaîne de six ou huit chiffres est toujours interprétée comme **ymd**. Le jour et le mois doivent toujours comporter deux chiffres. Une chaîne de quatre chiffres est interprétée comme l'année.|  
  
|ODBC| Description|  
|----------|-----------------|  
|{ d 'aaaa-mm-jj' }|Spécifique à l'API ODBC.|  
  
|Format XML W3C| Description|  
|--------------------|-----------------|  
|aaaa-mm-jjTZD|Spécifiquement pris en charge pour une utilisation XML/SOAP.<br /><br /> TZD est l'indicateur de fuseau horaire (Z ou +hh:mm ou -hh:mm) :<br /><br /> -hh : mm représente le décalage de fuseau horaire. hh comprend deux chiffres, entre 0 et 14, qui représentent le nombre d'heures dans le décalage de fuseau horaire.<br />-Est MM les deux chiffres, entre 0 et 59, représentant le nombre de minutes supplémentaires dans le décalage de fuseau horaire.<br />-+ (plus) ou – (moins) le signe obligatoire du décalage de fuseau horaire. Cela indique si le décalage de fuseau horaire est ajouté au temps universel coordonné ou soustrait de celui-ci pour obtenir l'heure locale. La plage valide du décalage de fuseau horaire se situe entre -14:00 et +14:00.|  
  
## <a name="ansi-and-iso-8601-compliance"></a>Conformité ANSI et ISO 8601  
**date** est conforme à la définition standard SQL ANSI pour le calendrier grégorien : « NOTE 85 - Datetime, types de données va permettre aux dates au format grégorien à stocker dans l’estimation de cardinalité date plage 0001 – 01 – 01 à 9999 – 12 – 31 CE. »
  
Le format de littéral de chaîne par défaut (utilisé pour les clients de bas niveau) s'alignera avec le format standard SQL qui est défini comme AAAA-MM-JJ. Ce format est le même que la définition ISO 8601 pour DATE.
  
> [!NOTE]  
>  Pour Informatica, la plage est limitée à 1582-10-15 (15 octobre 1582 CE) à 9999-12-31 (31 décembre 9999 de notre ère).  
  
## <a name="backward-compatibility-for-down-level-clients"></a>Compatibilité descendante pour les clients de bas niveau
Certains clients de bas niveau ne gèrent pas la **temps**, **date**, **datetime2** et **datetimeoffset** des types de données. Le tableau suivant présente le type de mappage entre une instance de haut niveau de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et des clients de bas niveau.
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de données|Format de littéral de chaîne par défaut passé au client de bas niveau|ODBC de bas niveau|OLEDB de bas niveau|JDBC de bas niveau|SQLCLIENT de bas niveau|  
| --- | --- | --- | --- | --- | --- |
|**time**|hh:mm:ss [.nnnnnnn]|SQL_WVARCHAR ou SQL_VARCHAR|DBTYPE_WSTR ou DBTYPE_STR|Java.sql.String|String ou SqString|  
|**date**|AAAA-MM-JJ|SQL_WVARCHAR ou SQL_VARCHAR|DBTYPE_WSTR ou DBTYPE_STR|Java.sql.String|String ou SqString|  
|**datetime2**|AAAA-MM-JJ hh:mm:ss[.nnnnnnn]|SQL_WVARCHAR ou SQL_VARCHAR|DBTYPE_WSTR ou DBTYPE_STR|Java.sql.String|String ou SqString|  
|**datetimeoffset**|AAAA-MM-JJ HH : mm : [.nnnnnnn] [+ &#124;-] HH : mm|SQL_WVARCHAR ou SQL_VARCHAR|DBTYPE_WSTR ou DBTYPE_STR|Java.sql.String|String ou SqString|  
  
## <a name="converting-date-and-time-data"></a>Conversion des données de date et d’heure
Lorsque vous effectuez une conversion vers des types de données date et heure, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rejette toutes les valeurs qu'il ne peut identifier comme dates ou heures. Pour plus d’informations sur l’utilisation des fonctions CAST et CONVERT avec des données de date et d’heure, consultez [CAST et CONVERT &#40; Transact-SQL &#41; ](../../t-sql/functions/cast-and-convert-transact-sql.md).
  
Lorsque la conversion consiste à **Time (n)**, la conversion échoue et le message d’erreur 206 est généré : « types d’opérandes : date est incompatible avec time ».
  
Si la conversion consiste à **datetime**, la date est copiée et le composant heure est défini à 00:00:00.000. Le code suivant montre les résultats de la conversion d'une valeur `date` en valeur `datetime`.  
  
```sql
DECLARE @date date= '12-10-25';  
DECLARE @datetime datetime= @date;  
  
SELECT @date AS '@date', @datetime AS '@datetime';  
  
--Result  
--@date      @datetime  
------------ -----------------------  
--2025-12-10 2025-12-10 00:00:00.000  
--  
--(1 row(s) affected)  
```  
  
Dans le cas de conversion en **smalldatetime**, lorsque le **date** valeur se trouve dans la plage d’un [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md), le composant date est copié et le composant heure est défini à 00:00:00. Lorsque le **date** valeur est en dehors de la plage d’un **smalldatetime** valeur, le message d’erreur 242 est déclenché : » la conversion d’un **date** type de données à un **smalldatetime** résultats de type de données dans une valeur hors limites ; et le **smalldatetime** a la valeur NULL. Le code suivant montre les résultats de la conversion d'une valeur `date` en valeur `smalldatetime`.
  
```sql
DECLARE @date date= '1912-10-25';  
DECLARE @smalldatetime smalldatetime = @date;  
  
SELECT @date AS '@date', @smalldatetime AS '@smalldatetime';  
  
--Result  
--@date      @smalldatetime  
------------ -----------------------  
--1912-10-25 1912-10-25 00:00:00  
--  
--(1 row(s) affected)  
```  
  
Lorsque la conversion consiste à **DateTimeOffset (n)**, la date est copiée et l’heure est définie à 00 : 00.0000000 + 00:00. Le code suivant montre les résultats de la conversion d'une valeur `date` en valeur `datetimeoffset(3)`.
  
```sql
DECLARE @date date = '1912-10-25';  
DECLARE @datetimeoffset datetimeoffset(3) = @date;  
  
SELECT @date AS '@date', @datetimeoffset AS '@datetimeoffset';  
  
--Result  
--@date      @datetimeoffset  
------------ ------------------------------  
--1912-10-25 1912-10-25 00:00:00.000 +00:00  
--  
--(1 row(s) affected)  
```  
  
Si la conversion consiste à **datetime2**, le composant date est copié et le composant heure est défini à 00:00:00.00, quelle que soit la valeur de (n). Le code suivant montre les résultats de la conversion d'une valeur `date` en valeur `datetime2(3)`.
  
```sql
DECLARE @date date = '1912-10-25';  
DECLARE @datetime2 datetime2(3) = @date;  
  
SELECT @date AS '@date', @datetime2 AS '@datetime2(3)';  
  
--Result  
--@date      @datetime2(3)  
------------ -----------------------  
--1912-10-25 1912-10-25 00:00:00.00  
--  
--(1 row(s) affected)  
```  
  
### <a name="converting-date-to-other-date-and-time-types"></a>Conversion de la date à d’autres types de date et d’heure
Cette section décrit ce qui se produit lorsqu’un **date** type de données est converti en autres types de données de date et d’heure.
  
Lorsque la conversion consiste à **Time (n)**, la conversion échoue et le message d’erreur 206 est généré : « types d’opérandes : date est incompatible avec time ».
  
Si la conversion consiste à **datetime**, date est copiée. Le code suivant montre les résultats de la conversion d'une valeur `date` en valeur `datetime`.
  
```sql
DECLARE @date date= '12-10-25';  
DECLARE @datetime datetime= @date;  
  
SELECT @date AS '@date', @datetime AS '@datetime';  
  
--Result  
--@date      @datetime  
------------ -----------------------  
--2025-12-10 2025-12-10 00:00:00.000  
--  
--(1 row(s) affected)  
```  
  
Lorsque la conversion consiste à **smalldatetime**, le **date** valeur se trouve dans la plage d’un [smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md), le composant date est copié et le composant heure est défini à 00:00:00.000. Lorsque le **date** valeur est en dehors de la plage d’un **smalldatetime** valeur, le message d’erreur 242 est déclenché : « la conversion d’un type de données date en type de données smalldatetime a généré une valeur hors limites. » et le **smalldatetime** a la valeur NULL. Le code suivant montre les résultats de la conversion d'une valeur `date` en valeur `smalldatetime`.
  
```sql
DECLARE @date date= '1912-10-25';  
DECLARE @smalldatetime smalldatetime = @date;  
  
SELECT @date AS '@date', @smalldatetime AS '@smalldatetime';  
  
--Result  
--@date      @smalldatetime  
------------ -----------------------  
--1912-10-25 1912-10-25 00:00:00  
--  
--(1 row(s) affected)  
```  
  
Pour la conversion en **DateTimeOffset (n)**, la date est copiée, et l’heure est définie à 00 : 00.0000000 + 00:00. Le code suivant montre les résultats de la conversion d'une valeur `date` en valeur `datetimeoffset(3)`.
  
```sql
DECLARE @date date = '1912-10-25';  
DECLARE @datetimeoffset datetimeoffset(3) = @date;  
  
SELECT @date AS '@date', @datetimeoffset AS '@datetimeoffset';  
  
--Result  
--@date      @datetimeoffset  
------------ ------------------------------  
--1912-10-25 1912-10-25 00:00:00.000 +00:00  
--  
--(1 row(s) affected)  
```  
  
Lorsque la conversion consiste à **datetime2**, le composant date est copié et le composant heure est défini sur 00 : 00 000000. Le code suivant montre les résultats de la conversion d'une valeur `date` en valeur `datetime2(3)`.
  
```sql
DECLARE @date date = '1912-10-25'  
DECLARE @datetime2 datetime2(3) = @date;  
  
SELECT @date AS '@date', @datetime2 AS '@datetime2(3)';  
  
--Result  
--@date      @datetime2(3)  
------------ -----------------------  
--1912-10-25 1912-10-25 00:00:00.000  
--  
--(1 row(s) affected)  
```  
  
### <a name="converting-string-literals-to-date"></a>Conversion de littéraux de chaîne en date
Les conversions de littéraux de chaîne en types de date et d'heure sont autorisées si toutes les parties des chaînes sont dans des formats valides. Sinon, une erreur d'exécution est déclenchée. Les conversions implicites ou explicites qui ne spécifient pas de style à partir de types de date et d'heure en littéraux de chaîne seront au format par défaut de la session active. Le tableau suivant présente les règles de conversion d’une chaîne littérale pour le **date** type de données.
  
|Littéral de chaîne d'entrée|**date**|  
|---|---|
|ODBC DATE|Littéraux de chaîne ODBC sont mappées à la **datetime** type de données. Toute opération d’affectation de littéraux ODBC DATETIME en une **date** type provoque une conversion implicite entre **datetime** et ce type, tel que défini par les règles de conversion.|  
|ODBC TIME|Consultez la règle DATE ODBC précédente.|  
|ODBC DATETIME|Consultez la règle DATE ODBC précédente.|  
|DATE uniquement|Trivial|  
|TIME uniquement|Les valeurs par défaut sont fournies.|  
|TIMEZONE uniquement|Les valeurs par défaut sont fournies.|  
|DATE + TIME|La partie DATE de la chaîne d'entrée est utilisée.|  
|DATE + TIMEZONE|Non autorisé.|  
|TIME + TIMEZONE|Les valeurs par défaut sont fournies.|  
|DATE + TIME + TIMEZONE|La partie DATE du DATETIME local sera utilisée.|  
  
## <a name="examples"></a>Exemples  
L'exemple suivant compare les résultats de la conversion d'une chaîne en chaque type de données de date et d'heure.
  
```sql
SELECT   
     CAST('2007-05-08 12:35:29. 1234567 +12:15' AS time(7)) AS 'time'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS date) AS 'date'   
    ,CAST('2007-05-08 12:35:29.123' AS smalldatetime) AS   
        'smalldatetime'   
    ,CAST('2007-05-08 12:35:29.123' AS datetime) AS 'datetime'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS datetime2(7)) AS   
        'datetime2'  
    ,CAST('2007-05-08 12:35:29.1234567 +12:15' AS datetimeoffset(7)) AS   
        'datetimeoffset';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
|Type de données|Sortie|  
|---------------|------------|  
|**time**|12:35:29. 1234567|  
|**date**|2007-05-08|  
|**smalldatetime**|2007-05-08 12:35:00|  
|**datetime**|2007-05-08 12:35:29.123|  
|**datetime2**|2007-05-08 12:35:29. 1234567|  
|**datetimeoffset**|2007-05-08 12:35:29.1234567 +12:15|  
  
## <a name="see-also"></a>Voir aussi
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  


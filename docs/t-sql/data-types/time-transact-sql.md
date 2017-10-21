---
title: heure (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 6/7/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- time_TSQL
- time
dev_langs:
- TSQL
helpviewer_keywords:
- time [SQL Server], data types
- time [SQL Server]
- date and time [SQL Server], time
- data types [SQL Server], date and time
- time data type [SQL Server]
ms.assetid: 30a6c681-8190-48e4-94d0-78182290a402
caps.latest.revision: 45
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: b6d6655b1640eff66182c78ea919849194d9714c
ms.openlocfilehash: fc0a9e68c9dc3ad664a4f091b73b073038c7f4c1
ms.contentlocale: fr-fr
ms.lasthandoff: 10/05/2017

---
# <a name="time-transact-sql"></a>time (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Définit une heure d'un jour. L'heure ne prend pas en charge les fuseaux horaires et se présente au format 24 heures.  
  
  > [!NOTE]  
  > Vous trouverez des informations de Informatica pour les clients PDW à l’aide du connecteur Informatica. 
  
## <a name="time-description"></a>Description de time  
  
|Propriété|Valeur|  
|--------------|-----------|  
|Syntaxe|**temps** [(*fractionnaire deuxième échelle*)]|  
|Utilisation|DÉCLARER @MyTime **Time (7)**<br /><br /> CRÉER la TABLE Table1 (Column1 **Time (7)** )|  
|*échelle de fractions de seconde*|Spécifie le nombre de chiffres pour la partie fractionnaire des secondes.<br /><br /> Il peut s'agir d'un entier compris entre 0 et 7. Pour Informatica, cela peut être un entier compris entre 0 et 3.<br /><br /> L’échelle de fractions de seconde par défaut est 7 (100 NS).|  
|Format de littéral de chaîne par défaut<br /><br /> (utilisé pour le client de bas niveau)|hh : mm : [.nnnnnnn] (hh : mm : [.nnn] pour Informatica)<br /><br /> Pour plus d'informations, consultez la section « Compatibilité descendante pour les clients de bas niveau » qui suit.|  
|Plage|00:00:00.0000000 via 23:59:59.9999999 (00:00:00.000 via 23:59:59.999 pour Informatica)|  
|Plages d'éléments|hh comprend deux chiffres, entre 0 et 23, qui représentent l'heure.<br /><br /> mm comprend deux chiffres, entre 0 et 59, qui représentent la minute.<br /><br /> ss comprend deux chiffres, entre 0 et 59, qui représentent la seconde.<br /><br /> n\*est égal à zéro et sept chiffres, entre 0 et 9999999, qui représentent les fractions de seconde. Pour Informatica, n\* est égal à zéro et trois chiffres, entre 0 et 999.|  
|Longueur de caractère|8 positions au minimum (HH) à 16 au maximum (.nnnnnnn). Pour Informatica, la valeur maximale est de 12 (hh:mm:ss.nnn).|  
|Précision, échelle<br /><br /> (l'utilisateur spécifie l'échelle uniquement)|Consultez le tableau ci-dessous.|  
|Taille de stockage|5 octets, fixes, sont la valeur par défaut avec une précision à la fraction de seconde de 100 ns par défaut. Dans Informatica, la valeur par défaut est de 4 octets, fixés, avec la valeur par défaut de 1 MS fractionnaire deuxième précision.|  
|Analyse de précision|100 nanosecondes (1 milliseconde dans Informatica)|  
|Valeur par défaut|00:00:00<br /><br /> Cette valeur est utilisée pour la partie heure ajoutée pour la conversion implicite de **date** à **datetime2** ou **datetimeoffset**.|  
|Précision à la fraction de seconde définie par l'utilisateur|Oui|  
|Prise en charge et conservation du décalage de fuseau horaire|Non|  
|Prise en charge de l'heure d'été|Non|  
  
|Échelle spécifiée|Résultat (précision, échelle)|Longueur de colonne (octets)|Fraction<br /><br /> secondes<br /><br /> precision|  
|---------------------|---------------------------------|-----------------------------|------------------------------------------|  
|**time**|(16,7) [Informatica en (12,3)]|5 (4 dans Informatica)|7 (3 dans Informatica)|  
|**time(0)**|(8,0)|3|0-2|  
|**Time(1)**|(10,1)|3|0-2|  
|**Time(2)**|(11,2)|3|0-2|  
|**Time(3)**|(12,3)|4|3-4|  
|**Time(4)**<br /><br /> Non pris en charge dans Informatica.|(13,4)|4|3-4|  
|**Time(5)**<br /><br /> Non pris en charge dans Informatica.|(14,5)|5|5-7|  
|**Time(6)**<br /><br /> Non pris en charge dans Informatica.|(15,6)|5|5-7|  
|**time(7)**<br /><br /> Non pris en charge dans Informatica.|(16,7)|5|5-7|  
  
## <a name="supported-string-literal-formats-for-time"></a>Formats de littéraux de chaîne pris en charge pour l'heure  
 Le tableau suivant montre la chaîne valide pour les formats de littéraux le **temps** type de données.  
  
|SQL Server| Description|  
|----------------|-----------------|  
|hh:mm[:ss][:fractions de seconde][AM][PM]<br /><br /> hh:mm[:ss][.fractions de seconde][AM][PM]<br /><br /> hhAM[PM]<br /><br /> hh AM[PM]|La valeur d'heure 0 représente l'heure après minuit (AM), que l'élément AM soit ou non spécifié. PM ne peut pas être spécifié quand l'heure est égale à 0.<br /><br /> Les valeurs d'heure comprises entre 01 et 11 représentent les heures avant midi si ni AM ni PM n'est spécifié. Elles représentent les heures avant midi si AM est spécifié et les heures après midi si PM est spécifié.<br /><br /> La valeur 12 pour les heures représente l'heure qui démarre à midi si ni AM ni PM n'est spécifié. Elle représente l'heure qui démarre à minuit si AM est spécifié et l'heure qui démarre à midi si PM est spécifié. Par exemple, 12:01 correspond à 1 minute après midi, comme 12:01 PM, alors que 12:01 AM équivaut à 1 minute après minuit. La spécification de 12:01 AM équivaut à 00:01 ou 00:01 AM.<br /><br /> Les heures situées entre 13 et 23 représentent les heures après midi si ni AM ni PM n'est spécifié. Les valeurs représentent également les heures après midi si PM est spécifié. Vous ne pouvez pas spécifier AM lorsque la valeur d'heure est comprise entre 13 et 23.<br /><br /> Une valeur d'heure de 24 n'est pas valide. Pour représenter minuit, utilisez 12:00 AM ou 00:00.<br /><br /> Les millisecondes peuvent être précédées du signe deux-points (:) ou d'un point (.). Si le signe deux-points est utilisé, il s'agit de millièmes de secondes. Si un point est utilisé, un chiffre unique représente les dixièmes de seconde, deux chiffres, centièmes de seconde et trois chiffres, des millièmes de seconde. Par exemple, 12:30:20:1 indique 20 secondes et un millième après 12:30 ; 12:30:20.1 indique 20 secondes et un dixième après 12:30.|  
  
|ISO 8601|Remarques|  
|--------------|-----------|  
|hh:mm:ss<br /><br /> hh:mm[:ss][.fractions de seconde]|hh comprend deux chiffres, entre 0 et 14, qui représentent le nombre d'heures dans le décalage de fuseau horaire.<br /><br /> mm comprend deux chiffres, entre 0 et 59, qui représentent le nombre de minutes supplémentaires dans le décalage de fuseau horaire.|  
  
|ODBC|Remarques|  
|----------|-----------|  
|{t 'hh:mm:ss[.fractions de seconde]'}|Spécifique à l'API ODBC.|  
  
## <a name="compliance-with-ansi-and-iso-8601-standards"></a>Conformité avec les normes ANSI et ISO 8601  
 L'utilisation de l'heure 24 pour représenter minuit et du saut de seconde au-delà de 59 comme défini par ISO 8601 (5.3.2 et 5.3) n'est pas prise en charge comme étant à compatibilité descendante et cohérente avec les types de date et d'heure existants.  
  
 Le format de littéral de chaîne par défaut (utilisé pour le client de bas niveau) s'alignera avec le format standard SQL qui est défini comme hh:mm:ss[.nnnnnnn]. Ce format ressemble à la définition ISO 8601 pour TIME à l'exclusion des fractions de seconde.  
  
##  <a name="BackwardCompatibilityforDownlevelClients"></a>Compatibilité descendante pour les Clients de bas niveau  
 Certains clients de bas niveau ne gèrent pas la **temps**, **date**, **datetime2** et **datetimeoffset** des types de données. Le tableau suivant présente le type de mappage entre une instance de haut niveau de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et des clients de bas niveau.  
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de données|Format de littéral de chaîne par défaut passé au client de bas niveau|ODBC de bas niveau|OLEDB de bas niveau|JDBC de bas niveau|SQLCLIENT de bas niveau|  
|-----------------------------------------|----------------------------------------------------------------|----------------------|-----------------------|----------------------|---------------------------|  
|**time**|hh:mm:ss [.nnnnnnn]|SQL_WVARCHAR ou SQL_VARCHAR|DBTYPE_WSTR ou DBTYPE_STR|Java.sql.String|String ou SqString|  
|**date**|AAAA-MM-JJ|SQL_WVARCHAR ou SQL_VARCHAR|DBTYPE_WSTR ou DBTYPE_STR|Java.sql.String|String ou SqString|  
|**datetime2**|AAAA-MM-JJ hh:mm:ss[.nnnnnnn]|SQL_WVARCHAR ou SQL_VARCHAR|DBTYPE_WSTR ou DBTYPE_STR|Java.sql.String|String ou SqString|  
|**datetimeoffset**|AAAA-MM-JJ HH : mm : [.nnnnnnn] [+ &#124;-] HH : mm|SQL_WVARCHAR ou SQL_VARCHAR|DBTYPE_WSTR ou DBTYPE_STR|Java.sql.String|String ou SqString|  
  
## <a name="converting-date-and-time-data"></a>Conversion de données de date et d'heure  
 Lorsque vous effectuez une conversion vers des types de données date et heure, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rejette toutes les valeurs qu'il ne peut identifier comme dates ou heures. Pour plus d’informations sur l’utilisation des fonctions CAST et CONVERT avec des données de date et d’heure, consultez [CAST et CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
### <a name="converting-timen-data-type-to-other-date-and-time-types"></a>Conversion de types de données time(n) vers d'autres types de date et d'heure  
 Cette section décrit ce qui se produit lorsqu’un **temps** type de données est converti en autres types de données de date et d’heure.  
  
 Lorsque la conversion consiste à **Time (n)**, l’heure, les minutes et les secondes sont copiées. Lorsque la précision de destination est inférieure à la précision source, les fractions de seconde sont arrondies selon la précision de destination. L'exemple suivant montre les résultats de la conversion d'une valeur `time(4)` en valeur `time(3)`.  
  
```  
DECLARE @timeFrom time(4) = '12:34:54.1237';  
DECLARE @timeTo time(3) = @timeFrom;  
  
SELECT @timeTo AS 'time(3)', @timeFrom AS 'time(4)';  
  
--Results  
--time(3)      time(4)  
-------------- -------------  
--12:34:54.124 12:34:54.1237  
--  
--(1 row(s) affected)  
```  
  
 Si la conversion consiste à  
                    **date**, la conversion échoue et le message d’erreur 206 est généré : « types d’opérandes : date est incompatible avec time ».  
  
 Lorsque la conversion consiste à **datetime**, heure, minute et seconde valeurs sont copiées et le composant date est défini sur ' 1900-01-01 ». Lorsque la précision en fractions de seconde de la **Time (n)** valeur est supérieure à trois chiffres, le **datetime** résultat sera tronqué. Le code suivant montre les résultats de la conversion d'une valeur `time(4)` en valeur `datetime`.  
  
```  
DECLARE @time time(4) = '12:15:04.1237';  
DECLARE @datetime datetime= @time;  
SELECT @time AS '@time', @datetime AS '@datetime';  
  
--Result  
--@time         @datetime  
--------------- -----------------------  
--12:15:04.1237 1900-01-01 12:15:04.123  
--  
--(1 row(s) affected)  
  
```  
  
 Lorsque la conversion consiste à **smalldatetime**, la date est définie sur ' 1900-01-01 » et les valeurs d’heure et les minutes sont arrondies. Les secondes et fractions de seconde sont définies sur 0. Le code suivant montre les résultats de la conversion d'une valeur `time(4)` en valeur `smalldatetime`.  
  
```  
-- Shows rounding up of the minute value.  
DECLARE @time time(4) = '12:15:59.9999';   
DECLARE @smalldatetime smalldatetime= @time;    
SELECT @time AS '@time', @smalldatetime AS '@smalldatetime';   
  
--Result  
@time            @smalldatetime  
---------------- -----------------------  
12:15:59.9999    1900-01-01 12:16:00--  
--(1 row(s) affected)  
  
-- Shows rounding up of the hour value.  
DECLARE @time time(4) = '12:59:59.9999';   
DECLARE @smalldatetime smalldatetime= @time;    
  
SELECT @time AS '@time', @smalldatetime AS '@smalldatetime';  
@time            @smalldatetime  
---------------- -----------------------  
12:59:59.9999    1900-01-01 13:00:00  
  
(1 row(s) affected)  
  
```  
  
 Si la conversion consiste à **DateTimeOffset (n)**, la date est définie sur ' 1900-01-01' et l’heure est copié. Le décalage de fuseau horaire est défini sur +00:00. Lorsque la précision en fractions de seconde de la **Time (n)** valeur est supérieure à la précision de la **DateTimeOffset (n)** valeur, la valeur est arrondie en fonction. L'exemple suivant montre les résultats de la conversion d'une valeur `time(4)` en type `datetimeoffset(3)`.  
  
```  
DECLARE @time time(4) = '12:15:04.1237';  
DECLARE @datetimeoffset datetimeoffset(3) = @time;  
  
SELECT @time AS '@time', @datetimeoffset AS '@datetimeoffset';  
  
--Result  
--@time         @datetimeoffset  
--------------- ------------------------------  
--12:15:04.1237 1900-01-01 12:15:04.124 +00:00  
--  
--(1 row(s) affected)  
  
```  
  
 Lors de la conversion à **datetime2**, la date est définie sur ' 1900-01-01', le composant heure est copié et le décalage de fuseau horaire est défini à 00:00. Lorsque la précision en fractions de seconde de la **datetime2** valeur est supérieure à la **Time (n)** valeur, la valeur sera arrondie à ajuster.  L'exemple suivant montre les résultats de la conversion d'une valeur `time(4)` en valeur `datetime2(2)`.  
  
```  
DECLARE @time time(4) = '12:15:04.1237';  
DECLARE @datetime2 datetime2(3) = @time;  
  
SELECT @datetime2 AS '@datetime2', @time AS '@time';  
  
--Result  
--@datetime2              @time  
------------------------- -------------  
--1900-01-01 12:15:04.124 12:15:04.1237  
--  
--(1 row(s) affected)  
```  
  
### <a name="converting-string-literals-to-timen"></a>Conversion de littéraux de chaîne en time(n)  
 Les conversions de littéraux de chaîne en types de date et d'heure sont autorisées si toutes les parties des chaînes sont dans des formats valides. Sinon, une erreur d'exécution est déclenchée. Les conversions implicites ou explicites qui ne spécifient pas de style à partir de types de date et d'heure en littéraux de chaîne seront au format par défaut de la session active. Le tableau suivant présente les règles de conversion d’une chaîne littérale pour le **temps** type de données.  
  
|Littéral de chaîne d'entrée|Règle de conversion|  
|--------------------------|---------------------|  
|ODBC DATE|Littéraux de chaîne ODBC sont mappées à la **datetime** type de données. Toute opération d’affectation de littéraux ODBC DATETIME en **temps**provoquent une conversion implicite entre types **datetime** et ce type, tel que défini par les règles de conversion.|  
|ODBC TIME|Voir la règle DATE ODBC plus haut.|  
|ODBC DATETIME|Voir la règle DATE ODBC plus haut.|  
|DATE uniquement|Les valeurs par défaut sont fournies.|  
|TIME uniquement|Trivial|  
|TIMEZONE uniquement|Les valeurs par défaut sont fournies.|  
|DATE + TIME|La partie TIME de la chaîne d'entrée est utilisée.|  
|DATE + TIMEZONE|Non autorisé.|  
|TIME + TIMEZONE|La partie TIME de la chaîne d'entrée est utilisée.|  
|DATE + TIME + TIMEZONE|La partie TIME du DATETIME local sera utilisée.|  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-comparing-date-and-time-data-types"></a>A. Comparaison de types de données de date et d'heure  
 L’exemple suivant compare les résultats de la conversion d’une chaîne en chaque **date** et **temps** type de données.  
  
```  
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
  
|Type de données|Sortie|  
|---------------|------------|  
|**time**|12:35:29. 1234567|  
|**date**|2007-05-08|  
|**smalldatetime**|2007-05-08 12:35:00|  
|**datetime**|2007-05-08 12:35:29.123|  
|**datetime2**|2007-05-08 12:35:29. 1234567|  
|**datetimeoffset**|2007-05-08 12:35:29.1234567 +12:15|  
  
###  <a name="ExampleB"></a> B. Insertion de littéraux de chaîne d'heure valides dans une colonne time(7)  
 Le tableau suivant répertorie différents littéraux de chaîne qui peuvent être insérées dans une colonne de type de données **Time (7)** avec les valeurs qui sont ensuite stockées dans cette colonne.  
  
|Type de format du littéral de chaîne|Littéral de chaîne inséré|Valeur time(7) qui est stockée| Description|  
|--------------------------------|-----------------------------|------------------------------------|-----------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|'01:01:01:123AM'|01:01:01.1230000|Lorsqu'un signe deux-points (:) précède la précision en fractions de seconde, l'échelle ne peut pas dépasser trois positions ou une erreur sera déclenchée.|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|'01:01:01.1234567 AM'|01:01:01.1234567|Lorsque l'élément AM ou PM est spécifié, l'heure est stockée au format 24 heures sans le littéral AM ou PM|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|'01:01:01.1234567 PM'|13:01:01.1234567|Lorsque l'élément AM ou PM est spécifié, l'heure est stockée au format 24 heures sans le littéral AM ou PM|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|'01:01:01.1234567PM'|13:01:01.1234567|Un espace avant AM ou PM est facultatif.|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|'01AM'|01:00:00.0000000|Lorsque seule l'heure est spécifiée, toutes les autres valeurs sont égales à 0.|  
|SQL Server|'01 AM'|01:00:00.0000000|Un espace avant AM ou PM est facultatif.|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|'01:01:01'|01:01:01.0000000|Lorsque la précision en fractions de seconde n'est pas spécifiée, chaque position qui est définie par le type de données est égale à 0.|  
|ISO 8601|'01:01:01.1234567'|01:01:01.1234567|Pour la conformité avec ISO 8601, utilisez le format 24 heures, et non AM ou PM.|  
|ISO 8601|'01:01:01.1234567 +01:01'|01:01:01.1234567|La différence de fuseau horaire facultative (TZD) est autorisée dans l'entrée, mais n'est pas stockée.|  
  
### <a name="c-inserting-time-string-literal-into-columns-of-each-date-and-time-date-type"></a>C. Insertion du littéral de chaîne d'heure dans les colonnes de chaque type de données de date et d'heure  
 Dans le tableau suivant, la première colonne affiche un littéral de chaîne d'heure à insérer dans une colonne de table de base de données du type de données de date et d'heure indiqué dans la deuxième colonne. La troisième colonne affiche la valeur qui sera stockée dans la colonne de table de base de données.  
  
|Littéral de chaîne inséré|Type de données de la colonne|Valeur qui est stockée dans la colonne| Description|  
|-----------------------------|----------------------|------------------------------------|-----------------|  
|'12:12:12.1234567'|**time(7)**|12:12:12.1234567|Si la précision en fractions de seconde dépasse la valeur spécifiée pour la colonne, la chaîne sera tronquée sans erreur.|  
|'2007-05-07'|**date**|NULL|Toute valeur d'heure provoquera l'échec de l'instruction INSERT.|  
|'12:12:12'|**smalldatetime**|1900-01-01 12:12:00|Toute valeur de précision en fractions de seconde provoquera l'échec de l'instruction INSERT.|  
|'12:12:12.123'|**datetime**|1900-01-01 12:12:12.123|Toute précision de seconde supérieure à trois positions provoquera l'échec de l'instruction INSERT.|  
|'12:12:12.1234567'|**datetime2(7)**|1900-01-01 12:12:12.1234567|Si la précision en fractions de seconde dépasse la valeur spécifiée pour la colonne, la chaîne sera tronquée sans erreur.|  
|'12:12:12.1234567'|**DateTimeOffset(7)**|1900-01-01 12:12:12.1234567 +00:00|Si la précision en fractions de seconde dépasse la valeur spécifiée pour la colonne, la chaîne sera tronquée sans erreur.|  
  
## <a name="see-also"></a>Voir aussi  
 [CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  


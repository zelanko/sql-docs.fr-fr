---
title: Règles de conversion de type de données Dwloader
description: Cette rubrique décrit les formats de données d’entrée et les conversions de types de données implicites prises en charge par le chargeur de ligne de commande dwloader lorsqu’il charge des données dans des Data Warehouse parallèles (PDW).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: fe5d8790b5adb8477c994d265f458cdb1ceda61a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401179"
---
# <a name="data-type-conversion-rules-for-dwloader---parallel-data-warehouse"></a>Règles de conversion de type de données pour dwloader-Parallel Data Warehouse
Cette rubrique décrit les formats de données d’entrée et les conversions de types de données implicites prises en charge par le [chargeur de ligne de commande dwloader](dwloader.md) lorsqu’il charge des données dans PDW. Les conversions de données implicites se produisent lorsque les données d’entrée ne correspondent pas au type de données dans la table cible SQL Server PDW. Utilisez ces informations lors de la conception de votre processus de chargement pour vous assurer que vos données seront chargées correctement dans SQL Server PDW.  
   
  
## <a name="inserting-literals-into-binary-types"></a><a name="InsertBinaryTypes"></a>Insertion de littéraux dans des types binaires  
Le tableau suivant définit les types de littéraux, le format et les règles de conversion acceptés pour le chargement d’une valeur littérale dans une colonne SQL Server PDW de type **Binary** (*n*) ou **varbinary**(*n*).  
  
|Type de données d’entrée|Exemples de données d’entrée|Conversion en type de données binary ou varbinary|  
|-------------------|-----------------------|-----------------------------------------------|  
|Littéral binaire|0x *hexidecimal_string*<br /><br />Exemple : 12Ef ou 0x12Ef|Le préfixe 0x est facultatif.<br /><br />La longueur de la source de données ne peut pas dépasser le nombre d’octets spécifié pour le type de données.<br /><br />Si la longueur de la source de données est inférieure à la taille du type de données **Binary** , les données sont complétées à droite avec des zéros pour atteindre la taille du type de données.|  
  
## <a name="inserting-literals-into-date-and-time-types"></a><a name="InsertDateTimeTypes"></a>Insertion de littéraux dans des types de date et d’heure  
Les littéraux de date et d’heure sont représentés à l’aide de littéraux de chaîne dans des formats spécifiques, placés entre guillemets simples. Les tableaux suivants définissent les types de littéraux, le format et les règles de conversion autorisés pour le chargement d’un littéral de date ou d’heure dans une colonne de type **DateTime**, **smalldatetime**, **Date**, **Time**, **DateTimeOffset**ou **datetime2**. Les tables définissent le format par défaut pour le type de données spécifié. Les autres formats qui peuvent être spécifiés sont définis dans la section [formats DateTime](#DateFormats). Les littéraux de date et d’heure ne peuvent pas inclure d’espaces de début ou de fin. les valeurs de **Date**, **smalldatetime**et NULL ne peuvent pas être chargées en mode de largeur fixe.  
  
### <a name="datetime-data-type"></a>Type de données datetime  
Le tableau suivant définit le format et les règles par défaut pour le chargement de valeurs littérales dans une colonne de type **DateTime**. Une chaîne vide (' ') est convertie en valeur par défaut' 1900-01-01 12:00:00.000 '. Les chaînes qui contiennent uniquement des espaces (' ') génèrent une erreur.  
  
|Type de données d’entrée|Exemples de données d’entrée|Conversion en type de données DateTime|  
|-------------------|-----------------------|------------------------------------|  
|Littéral de chaîne au format **DateTime**|'AAAA-MM-JJ hh : mm : SS [. fff] '<br /><br />Exemple : « 2007-05-08 12:35:29.123 »|Les chiffres fractionnaires manquants sont définis sur 0 lorsque la valeur est insérée. Par exemple, le littéral « 2007-05-08 12:35 » est inséré en tant que « 2007-05-08 12:35:00.000 ».|  
|Littéral de chaîne au format **smalldatetime**|'AAAA-MM-JJ hh : mm'<br /><br />Exemple : « 2007-05-08 12:35 »|Les secondes et les chiffres fractionnaires restants sont définis sur 0 lorsque la valeur est insérée.|  
|Littéral de chaîne dans le format de **Date**|'AAAA-MM-JJ'<br /><br />Exemple : « 2007-05-08 »|Les valeurs d’heure (heure, minutes, secondes et fractions) sont définies sur 12:00:00.000 lorsque la valeur est insérée.|  
|Littéral de chaîne au format **datetime2**|'AAAA-MM-JJ hh : mm : SS. fffffff'<br /><br />Exemple : « 2007-05-08 12:35:29.1234567 »|Les données sources ne peuvent pas dépasser trois chiffres fractionnaires. Par exemple, le littéral « 2007-05-08 12:35:29.123 » sera inséré, mais la valeur « 2007-05-8 12:35:29.1234567 » génère une erreur.|  
  
### <a name="smalldatetime-data-type"></a>Type de données smalldatetime  
Le tableau suivant définit le format et les règles par défaut pour le chargement de valeurs littérales dans une colonne de type **smalldatetime**. Une chaîne vide (' ') est convertie en valeur par défaut' 1900-01-01 12:00 '. Les chaînes qui contiennent uniquement des espaces (' ') génèrent une erreur.  
  
|Type de données d’entrée|Exemples de données d’entrée|Conversion en type de données smalldatetime|  
|-------------------|-----------------------|-----------------------------------------|  
|Littéral de chaîne au format **smalldatetime**|'AAAA-MM-JJ hh : mm’ou’AAAA-MM-JJ hh : mm : SS'<br /><br />Exemple : « 2007-05-08 12:00 » ou « 2007-05-08 12:00:15 »|Les données sources doivent avoir des valeurs pour l’année, le mois, la date, l’heure et la minute. Les secondes sont facultatives et, le cas échéant, doivent être définies sur la valeur 00. Toute autre valeur génère une erreur.<br /><br />Les secondes sont facultatives. Lors du chargement dans une colonne smalldatetime, dwloader arrondit les secondes et les fractions de seconde. Par exemple, 1999-01-05 20:10:35.123 sera chargé en tant que 01-05 20:11.|  
|Littéral de chaîne dans le format de **Date**|'AAAA-MM-JJ'<br /><br />Exemple : « 2007-05-08 »|Les valeurs d’heure (heure, minutes, secondes et fractions) sont définies sur 0 lorsque la valeur est insérée.|  
  
### <a name="date-data-type"></a>Type de données date  
Le tableau suivant définit le format et les règles par défaut pour le chargement de valeurs littérales dans une colonne de type **Date**. Une chaîne vide (' ') est convertie en valeur par défaut' 1900-01-01 '. Les chaînes qui contiennent uniquement des espaces (' ') génèrent une erreur.  
  
|Type de données d’entrée|Exemples de données d’entrée|Conversion en type de données date|  
|-------------------|-----------------------|--------------------------------|  
|Littéral de chaîne dans le format de **Date**|'AAAA-MM-JJ'<br /><br />Exemple : « 2007-05-08 »||  
  
### <a name="time-data-type"></a>Type de données Time  
Le tableau suivant définit le format et les règles par défaut pour le chargement de valeurs littérales dans une colonne de type **Time**. Une chaîne vide (« ») est convertie en valeur par défaut «00:00:00.0000 ». Les chaînes qui contiennent uniquement des espaces (' ') génèrent une erreur.  
  
|Type de données d’entrée|Exemples de données d’entrée|Conversion en type de données Time|  
|-------------------|-----------------------|--------------------------------|  
|Littéral de chaîne dans le format d' **heure**|« hh : mm : SS. fffffff »<br /><br />Exemple : « 12:35:29.1234567 »|Si la source de données a une précision inférieure ou égale (nombre de chiffres fractionnaires) par rapport à la précision du type de données **Time** , les données sont complétées à droite par des zéros. Par exemple, une valeur littérale « 12:35:29.123 » est insérée en tant que « 12:35:29.1230000 ».|  
  
### <a name="datetimeoffset-data-type"></a>DateTimeOffset (type de données)  
Le tableau suivant définit le format et les règles par défaut pour le chargement de valeurs littérales dans une colonne de type **DateTimeOffset** (*n*). Le format par défaut est « AAAA-MM-JJ hh : mm : SS. fffffff {+ |-} hh : mm ». Une chaîne vide (« ») est convertie en valeur par défaut «1900-01-01 12:00:00.0000000 + 00:00 ». Les chaînes qui contiennent uniquement des espaces (' ') génèrent une erreur. Le nombre de chiffres fractionnaires dépend de la définition de la colonne. Par exemple, une colonne définie en tant que **DateTimeOffset** (2) aura deux chiffres fractionnaires.  
  
|Type de données d’entrée|Exemples de données d’entrée|Conversion en type de données DateTimeOffset|  
|-------------------|-----------------------|------------------------------------------|  
|Littéral de chaîne au format **DateTime**|'AAAA-MM-JJ hh : mm : SS [. fff] '<br /><br />Exemple : « 2007-05-08 12:35:29.123 »|Les chiffres fractionnaires manquants et les valeurs de décalage sont définis sur 0 lorsque la valeur est insérée. Par exemple, le littéral « 2007-05-08 12:35:29.123 » est inséré en tant que « 2007-05-08 12:35:29.1230000 + 00:00 ».|  
|Littéral de chaîne au format **smalldatetime**|'AAAA-MM-JJ hh : mm'<br /><br />Exemple : « 2007-05-08 12:35 »|Secondes, les chiffres fractionnaires restants et les valeurs de décalage sont définis sur 0 lorsque la valeur est insérée.|  
|Littéral de chaîne dans le format de **Date**|'AAAA-MM-JJ'<br /><br />Exemple : « 2007-05-08 »|Les valeurs d’heure (heure, minutes, secondes et fractions) sont définies sur 0 lorsque la valeur est insérée. Par exemple, le littéral « 2007-05-08 » est inséré en tant que « 2007-05-08 00:00:00.0000000 + 00:00 ».|  
|Littéral de chaîne au format **datetime2**|'AAAA-MM-JJ hh : mm : SS. fffffff'<br /><br />Exemple : « 2007-05-08 12:35:29.1234567 »|Les données sources ne peuvent pas dépasser le nombre spécifié de fractions de seconde dans la colonne DateTimeOffset. Si la source de données a un nombre inférieur ou égal de fractions de seconde, les données sont complétées à droite par des zéros. Par exemple, si le type de données est DateTimeOffset (5), la valeur littérale « 2007-05-08 12:35:29.123 + 12:15 » est insérée en tant que « 12:35:29.12300 + 12:15 ».|  
|Littéral de chaîne au format **DateTimeOffset**|'AAAA-MM-JJ hh : mm : SS. fffffff {+&#124;-} hh : mm'<br /><br />Exemple : « 2007-05-08 12:35:29.1234567 + 12:15 »|Les données sources ne peuvent pas dépasser le nombre spécifié de fractions de seconde dans la colonne DateTimeOffset. Si la source de données a un nombre inférieur ou égal de fractions de seconde, les données sont complétées à droite par des zéros. Par exemple, si le type de données est DateTimeOffset (5), la valeur littérale « 2007-05-08 12:35:29.123 + 12:15 » est insérée en tant que « 12:35:29.12300 + 12:15 ».|  
  
### <a name="datetime2-data-type"></a>Type de données datetime2  
Le tableau suivant définit le format et les règles par défaut pour le chargement de valeurs littérales dans une colonne de type **datetime2** (*n*). Le format par défaut est « AAAA-MM-JJ hh : mm : SS. fffffff ». Une chaîne vide (' ') est convertie en valeur par défaut' 1900-01-01 12:00:00 '. Les chaînes qui contiennent uniquement des espaces (' ') génèrent une erreur. Le nombre de chiffres fractionnaires dépend de la définition de la colonne. Par exemple, une colonne définie en tant que **datetime2** (2) aura deux chiffres fractionnaires.  
  
|Type de données d’entrée|Exemples de données d’entrée|Conversion en type de données datetime2|  
|-------------------|-----------------------|-------------------------------------|  
|Littéral de chaîne au format **DateTime**|'AAAA-MM-JJ hh : mm : SS [. fff] '<br /><br />Exemple : « 2007-05-08 12:35:29.123 »|Les fractions de seconde sont facultatives et sont définies sur 0 lorsque la valeur est insérée.|  
|Littéral de chaîne au format **smalldatetime**|'AAAA-MM-JJ hh : mm'<br /><br />Exemple : « 2007-05-08 12 »|Les secondes facultatives et les chiffres fractionnaires restants sont définis sur 0 lorsque la valeur est insérée.|  
|Littéral de chaîne dans le format de **Date**|'AAAA-MM-JJ'<br /><br />Exemple : « 2007-05-08 »|Les valeurs d’heure (heure, minutes, secondes et fractions) sont définies sur 0 lorsque la valeur est insérée. Par exemple, le littéral « 2007-05-08 » est inséré en tant que « 2007-05-08 12:00:00.0000000 ».|  
|Littéral de chaîne au format **datetime2**|'AAAA-MM-JJ hh : mm : SS : fffffff'<br /><br />Exemple : « 2007-05-08 12:35:29.1234567 »|Si la source de données contient des composants de données et d’heure qui sont inférieurs ou égaux à la valeur spécifiée dans **datetime2**(*n*), les données sont insérées. dans le cas contraire, une erreur est générée.|  
  
### <a name="datetime-formats"></a><a name="DateFormats"></a>Formats DateTime  
Dwloader prend en charge les formats de données suivants pour les données d’entrée qu’il charge dans SQL Server PDW. Plus de détails sont répertoriés après le tableau.  
  
|DATETIME|smalldatetime|Date|datetime2|datetimeoffset|  
|------------|-----------------|--------|-------------|------------------|  
|[M[M]]M-[d]d-[yy]yy HH:mm:ss[.fff]|[M[M]]M-[d]d-[yy]yy HH:mm[:00]|[M[M]]M-[d]d-[yy]yy|[M[M]]M-[d]d-[yy]yy HH:mm:ss[.fffffff]|[M[M]]M-[d]d-[yy]yy HH:mm:ss[.fffffff] zzz|  
|[M[M]]M-[d]d-[yy]yy hh:mm:ss[.fff][tt]|[M[M]]M-[d]d-[yy]yy hh:mm[:00][tt]||[M[M]]M-[d]d-[yy]yy hh:mm:ss[.fffffff][tt]|[M[M]]M-[d]d-[yy]yy hh:mm:ss[.fffffff][tt] zzz|  
|[M[M]]M-[yy]yy-[d]d HH:mm:ss[.fff]|[M[M]]M-[yy]yy-[d]d HH:mm[:00]|[M[M]]M-[yy]yy-[d]d|[M[M]]M-[yy]yy-[d]d HH:mm:ss[.fffffff]|[M[M]]M-[yy]yy-[d]d HH:mm:ss[.fffffff] zzz|  
|[M[M]]M-[yy]yy-[d]d hh:mm:ss[.fff][tt]|[M[M]]M-[yy]yy-[d]d hh:mm[:00][tt]||[M[M]]M-[yy]yy-[d]d hh:mm:ss[.fffffff][tt]|[M[M]]M-[yy]yy-[d]d hh:mm:ss[.fffffff][tt] zzz|  
|[yy]yy-[M[M]]M-[d]d HH:mm:ss[.fff]|[yy]yy-[M[M]]M-[d]d HH:mm[:00]|[yy]yy-[M[M]]M-[d]d|[yy]yy-[M[M]]M-[d]d HH:mm:ss[.fffffff]|[yy]yy-[M[M]]M-[d]d HH:mm:ss[.fffffff]  zzz|  
|[yy]yy-[M[M]]M-[d]d hh:mm:ss[.fff][tt]|[yy]yy-[M[M]]M-[d]d hh:mm[:00][tt]||[yy]yy-[M[M]]M-[d]d hh:mm:ss[.fffffff][tt]|[yy]yy-[M[M]]M-[d]d hh:mm:ss[.fffffff][tt] zzz|  
|[yy]yy-[d]d-[M[M]]M HH:mm:ss[.fff]|[yy]yy-[d]d-[M[M]]M HH:mm[:00]|[yy]yy-[d]d-[M[M]]M|[yy]yy-[d]d-[M[M]]M HH:mm:ss[.fffffff]|[yy]yy-[d]d-[M[M]]M HH:mm:ss[.fffffff]  zzz|  
|[yy]yy-[d]d-[M[M]]M hh:mm:ss[.fff][tt]|[yy]yy-[d]d-[M[M]]M hh:mm[:00][tt]||[yy]yy-[d]d-[M[M]]M hh:mm:ss[.fffffff][tt]|[yy]yy-[d]d-[M[M]]M hh:mm:ss[.fffffff][tt] zzz|  
|[d]d-[M[M]]M-[yy]yy HH:mm:ss[.fff]|[d]d-[M[M]]M-[yy]yy HH:mm[:00]|[d]d-[M[M]]M-[yy]yy|[d]d-[M[M]]M-[yy]yy HH:mm:ss[.fffffff]|[d]d-[M[M]]M-[yy]yy HH:mm:ss[.fffffff] zzz|  
|[d]d-[M[M]]M-[yy]yy hh:mm:ss[.fff][tt]|[d]d-[M[M]]M-[yy]yy hh:mm[:00][tt]||[d]d-[M[M]]M-[yy]yy hh:mm:ss[.fffffff][tt]|[d]d-[M[M]]M-[yy]yy hh:mm:ss[.fffffff][tt] zzz|  
|[d]d-[yy]yy-[M[M]]M HH:mm:ss[.fff]|[d]d-[yy]yy-[M[M]]M HH:mm[:00]|[d]d-[yy]yy-[M[M]]M|[d]d-[yy]yy-[M[M]]M HH:mm:ss[.fffffff]|[d]d-[yy]yy-[M[M]]M HH:mm:ss[.fffffff]  zzz|  
|[d]d-[yy]yy-[M[M]]M hh:mm:ss[.fff][tt]|[d]d-[yy]yy-[M[M]]M hh:mm[:00][tt]||[d]d-[yy]yy-[M[M]]M hh:mm:ss[.fffffff][tt]|[d]d-[yy]yy-[M[M]]M hh:mm:ss[.fffffff][tt] zzz|  
  
Détails :  
  
-   Pour séparer les valeurs du mois, du jour et de l’année, vous pouvez utiliser « - », « / » ou «». '. Par souci de simplicité, le tableau utilise uniquement le séparateur « - ».  
  
-   Pour spécifier le mois en tant que texte, utilisez au moins trois caractères. Les mois avec 1 ou 2 caractères seront interprétés comme un nombre.  
  
-   Pour séparer les valeurs d’heure, utilisez le symbole' : '.  
  
-   Les lettres entre crochets sont facultatives.  
  
-   Les lettres « tt » correspondent aux mentions [AM|PM|am|pm]. AM est la valeur par défaut. Lorsque « tt » est spécifié, la valeur d’heure (hh) doit être comprise entre 0 et 12.  
  
-   Les lettres « zzz » désignent le décalage par rapport au fuseau horaire du système, au format {+|-}HH:ss].  
  
## <a name="inserting-literals-into-numeric-types"></a><a name="InsertNumerictypes"></a>Insertion de littéraux dans des types numériques  
Les tableaux suivants définissent le format et les règles de conversion par défaut pour le chargement d’une valeur littérale dans une colonne SQL Server PDW qui utilise un type numérique.  
  
### <a name="bit-data-type"></a>bit, type de données  
Le tableau suivant définit le format et les règles par défaut pour le chargement de valeurs littérales dans une colonne de type **bit**. Une chaîne vide (' ') ou une chaîne qui contient uniquement des espaces (' ') est convertie en 0.  
  
|Type de données d’entrée|Exemples de données d’entrée|Conversion en type de données bit|  
|-------------------|-----------------------|-------------------------------|  
|Littéral de chaîne au format **entier**|'ffffffffff'<br /><br />Exemple : ' 1 'ou' 321 '|Une valeur entière mise en forme en tant que littéral de chaîne ne peut pas contenir de valeur négative. Par exemple, la valeur « -123 » génère une erreur.<br /><br />Une valeur supérieure à 1 est convertie en 1. Par exemple, la valeur « 123 » est convertie en 1.|  
|Littéral de chaîne|« TRUE » ou « FALSe »<br /><br />Exemple : « true »|La valeur « TRUE » est convertie en 1 ; la valeur « FALSe » est convertie en 0.|  
|Littéral d’entier|fffffffn<br /><br />Exemple : 1 ou 321|Une valeur supérieure à 1 ou inférieure à 0 est convertie en 1. Par exemple, les valeurs 123 et-123 sont converties en 1.|  
|Littéral décimal|fffnn.fffn<br /><br />Exemple : 1234,5678|Une valeur supérieure à 1 ou inférieure à 0 est convertie en 1. Par exemple, les valeurs 123,45 et-123,45 sont converties en 1.|  
  
### <a name="decimal-data-type"></a>Type de données decimal  
Le tableau suivant définit les règles de chargement des valeurs littérales dans une colonne de type **Decimal** (*p, s*). Les règles de conversion de données sont les mêmes que pour les SQL Server. Pour plus d’informations, consultez [conversion de type de données (moteur de base de données)](https://go.microsoft.com/fwlink/?LinkId=202128) sur MSDN.  
  
|Type de données d’entrée|Exemples de données d’entrée|  
|-------------------|-----------------------|  
|Littéral d’entier|321312313123|  
|Littéral décimal|123344,34455|  
  
### <a name="float-and-real-data-types"></a>Types de données float et Real  
Le tableau suivant définit les règles de chargement des valeurs littérales dans une colonne de type **float** ou **Real**. Les règles de conversion de données sont les mêmes que pour les SQL Server. Pour plus d’informations, consultez [conversion de type de données (moteur de base de données)](../t-sql/data-types/data-type-conversion-database-engine.md) sur MSDN.  
  
|Type de données d’entrée|Exemples de données d’entrée|  
|-------------------|-----------------------|  
|Littéral d’entier|321312313123|  
|Littéral décimal|123344,34455|  
|Littéral à virgule flottante|3.12323 e + 14|  
  
### <a name="int-bigint-tinyint-smallint-data-types"></a>int, bigint, tinyint, smallint, types de données  
Le tableau suivant définit les règles de chargement des valeurs littérales dans une colonne de type **int**, **bigint**, **tinyint**ou **smallint**. La source de données ne peut pas dépasser la plage autorisée pour le type de données spécifié. Par exemple, la plage de **tinyint** est comprise entre 0 et 255 et la plage de **int** est-2 147 483 648 à 2 147 483 647.  
  
|Type de données d’entrée|Exemples de données d’entrée|Conversion en types de données Integer|  
|-------------------|-----------------------|------------------------------------|  
|Littéral d’entier|321312313123||  
|Littéral décimal|123344,34455|Les valeurs à droite de la virgule décimale sont tronquées.|  
  
### <a name="money-and-smallmoney-data-types"></a>Types de données Money et smallmoney  
Les valeurs littérales monétaires sont représentées sous la forme d’une chaîne de nombres avec une virgule décimale facultative et d’un symbole monétaire facultatif en tant que préfixe. La source de données ne peut pas dépasser la plage autorisée pour le type de données spécifié. Par exemple, la plage de **smallmoney** est comprise entre-214 748,3648 et 214 748,3647 et la plage pour **money** est-922 337 203 685 477,5808 à 922 337 203 685 477,5807. Le tableau suivant définit les règles de chargement des valeurs littérales dans une colonne de type **Money** ou **smallmoney**.  
  
|Type de données d’entrée|Exemples de données d’entrée|Conversion en type de données Money ou smallmoney|  
|-------------------|-----------------------|-----------------------------------------------|  
|Littéral d’entier|321312|Les chiffres manquants après la virgule décimale ont la valeur 0 lorsque la valeur est insérée. Par exemple, le littéral 12345 est inséré en tant que 12345,0000|  
|Littéral décimal|123344,34455|Si le nombre de chiffres après la virgule décimale dépasse 4, la valeur est arrondie à la valeur la plus proche. Par exemple, la valeur 123344,34455 est insérée sous la forme 123344,3446.|  
|Littéral Money|$123456,7890|Le symbole monétaire n’est pas inséré avec la valeur.<br /><br />Si le nombre de chiffres après la virgule décimale dépasse 4, la valeur est arrondie à la valeur la plus proche.|  
  
## <a name="inserting-literals-into-string-types"></a><a name="InsertStringTypes"></a>Insertion de littéraux dans des types String  
Les tableaux suivants définissent le format et les règles de conversion par défaut pour le chargement d’une valeur littérale dans une colonne SQL Server PDW qui utilise un type chaîne.  
  
### <a name="char-varchar-nchar-and-nvarchar-data-types"></a>Types de données char, varchar, nchar et nvarchar  
Le tableau suivant définit le format et les règles par défaut pour le chargement de valeurs littérales dans une colonne de type **char**, **varchar**, **nchar** et **nvarchar**. La longueur de la source de données ne peut pas dépasser la taille spécifiée pour le type de données. Si la longueur de la source de données est inférieure à la taille du type de données **char** ou **nchar** , les données sont complétées à droite avec des espaces vides pour atteindre la taille du type de données.  
  
|Type de données d’entrée|Exemples de données d’entrée|Conversion en types de données caractères|  
|---------------|-------------------|----------------------------------|  
|Littéral de chaîne|Format : 'chaîne de caractères'<br /><br />Exemple : « ABC »| NA |  
|Littéral de chaîne Unicode|Format : N’character chaîne'<br /><br />Exemple : N’abc'| NA |  
|Littéral d’entier|Format : ffffffffffn<br /><br />Exemple : 321312313123| NA |  
|Littéral décimal|Format : FFFFFF. fffffff<br /><br />Exemple : 12344,34455| NA |  
|Littéral Money|Format : $ffffff. fffnn<br /><br />Exemple : $123456,99|Le symbole monétaire facultatif n’est pas inséré avec la valeur. Pour insérer le symbole monétaire, insérez la valeur en tant que littéral de chaîne. Cela correspond au format du chargeur, qui traite chaque littéral comme un littéral de chaîne.<br /><br />Les virgules ne sont pas autorisées.<br /><br />Si le nombre de chiffres après la virgule décimale dépasse 2, la valeur est arrondie à la valeur la plus proche. Par exemple, la valeur 123,946789 est insérée sous la forme 123,95.<br /><br />Seul le style par défaut 0 (aucune virgule et 2 chiffres après la virgule décimale) est autorisé lors de l’utilisation de la fonction CONVERT pour insérer des littéraux Money.|  
  
### <a name="general-remarks"></a>Remarques d'ordre général  
**dwloader** effectue les mêmes conversions implicites que celles exécutées par SMP SQL Server, mais ne prend pas en charge toutes les conversions implicites prises en charge par SMP SQL Server.  
 
<!-- MISSING LINKS 
## See Also  
[Grant Permissions to Load Data &#40;SQL Server PDW&#41;](../sqlpdw/grant-permissions-to-load-data-sql-server-pdw.md)  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  

-->
  

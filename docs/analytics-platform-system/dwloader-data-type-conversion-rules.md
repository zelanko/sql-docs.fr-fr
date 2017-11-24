---
title: "Type de données des règles de conversion de dwloader"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.suite: sql
ms.custom: 
ms.technology: mpp-data-warehouse
description: "Cette rubrique décrit les formats de données d’entrée et les conversions de types de données implicites qui dwloader que chargeur de ligne de commande prend en charge lors du chargement des données dans PDW."
ms.date: 10/20/2016
ms.topic: article
ms.assetid: 79c48520-b08b-4b15-a943-a551cc90a2c4
caps.latest.revision: "30"
ms.openlocfilehash: 2ac1325b3765bafbe34dc61f65f7641431afdfa0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="data-type-conversion-rules-for-dwloader"></a>Type de données des règles de conversion de dwloader
Cette rubrique décrit les formats de données d’entrée et les conversions de types de données implicites qui [dwloader de ligne de commande chargeur](dwloader.md) prend en charge lors du chargement des données dans PDW. Les conversions implicites de données se produisent lorsque les données d’entrée ne correspondent pas le type de données dans la table cible de SQL Server PDW. Utilisez ces informations lorsque vous concevez votre processus de chargement pour vous assurer de vos données sera chargé avec succès dans SQL Server PDW.  
   
  
## <a name="InsertBinaryTypes"></a>Insertion de littéraux dans les Types de données binaires  
Le tableau suivant définit les types de littéral acceptés, format et les règles de conversion pour le chargement d’une valeur littérale dans une colonne SQL Server PDW de type **binaire** (*n*) ou  **varbinary**(*n*).  
  
|Type de données d’entrée|Exemples de données d’entrée|Conversion en type binary ou varbinary, Type de données|  
|-------------------|-----------------------|-----------------------------------------------|  
|Littéral binaire|[0 x] *hexidecimal_string*<br /><br />Exemple : 12Ef ou 0x12Ef|Le préfixe 0 x est facultatif.<br /><br />La longueur de source de données ne peut pas dépasser le nombre d’octets spécifié pour le type de données.<br /><br />Si la longueur de source de données est inférieure à la taille de la **binaire** de type de données, les données sont complétées à droite avec des zéros non significatifs pour atteindre la taille de type de données.|  
  
## <a name="InsertDateTimeTypes"></a>Insertion de littéraux dans les Types de Date et heure  
Les littéraux de date et d’heure sont représentées à l’aide de littéraux de chaîne dans un format spécifique, placé entre guillemets simples. Les tableaux suivants décrivent les types de littéral autorisées, le format et les règles de conversion pour le chargement d’une date ou un littéral d’heure dans une colonne de type **datetime**, **smalldatetime**, **date**, **temps**, **datetimeoffset**, ou **datetime2**. Les tableaux définissent le format par défaut pour le type de données spécifiée. Autres formats qui peuvent être spécifiées sont définies dans la section [Formats Datetime](#DateFormats). Les littéraux de date et d’heure ne peut pas inclure des espaces de début ou de fin. **date**, **smalldatetime**, et les valeurs null ne peut pas être chargés en mode de largeur fixe.  
  
### <a name="datetime-data-type"></a>Type de données datetime  
Le tableau suivant définit le format par défaut et les règles pour le chargement des valeurs littérales dans une colonne de type **datetime**. Une chaîne vide (") est convertie en la valeur par défaut ' 1900-01-01 12:00:00.000'. Les chaînes qui contiennent uniquement des espaces à droite (' ') génère une erreur.  
  
|Type de données d’entrée|Exemples de données d’entrée|Conversion en Type de données datetime|  
|-------------------|-----------------------|------------------------------------|  
|Littéral de chaîne dans **datetime** format|'AAAA-MM-JJ HH : mm : [.fff]'<br /><br />Exemple : « 2007-05-08 12:35:29.123'|Les chiffres fractionnaires manquantes sont définies à 0 lorsque la valeur est insérée. Par exemple, le littéral ' 2007-05-08 12:35 ' est inséré en tant que « 2007-05-08 12:35:00.000'.|  
|Littéral de chaîne dans **smalldatetime** format|'AAAA-MM-JJ HH'<br /><br />Exemple : « 2007-05-08 12:35 '|Secondes et fractions restantes sont définies à 0 lorsque la valeur est insérée.|  
|Littéral de chaîne dans **date** format|« AAAA-MM-JJ »<br /><br />Exemple : « 2007-05-08'|Les valeurs de temps (heures, minutes, secondes et fractions) sont définies sur 12:00:00.000 lorsque la valeur est insérée.|  
|Littéral de chaîne dans **datetime2** format|'AAAA-MM-JJ ss.fffffff'<br /><br />Exemple : « 2007-05-08 12:35:29.1234567'|La source de données ne peut pas dépasser trois chiffres fractionnaires. Par exemple, le littéral ' 2007-05-08 12:35:29.123' sera inséré, mais la valeur « 2007-05-8 12:35:29.1234567' génère une erreur.|  
  
### <a name="smalldatetime-data-type"></a>Type de données smalldatetime  
Le tableau suivant définit le format par défaut et les règles pour le chargement des valeurs littérales dans une colonne de type **smalldatetime**. Une chaîne vide (") est convertie en la valeur par défaut ' 01 / 01/1900 12:00 ». Les chaînes qui contiennent uniquement des espaces à droite (' ') génère une erreur.  
  
|Type de données d’entrée|Exemples de données d’entrée|Conversion en Type de données smalldatetime|  
|-------------------|-----------------------|-----------------------------------------|  
|Littéral de chaîne dans **smalldatetime** format|« AAAA-MM-JJ HH : mm » ou « AAAA-MM-JJ HH : mm : »<br /><br />Exemple : « 2007-05-08 12:00 ' ou ' 2007-05-08-12:00:15 '|La source de données doit avoir des valeurs pour l’année, mois, date, heure et minute. Secondes sont facultatives et, s’il est présent, doivent être définies à la valeur 00. Toute autre valeur génère une erreur.<br /><br />Les secondes sont facultatives. Lors du chargement dans une colonne de smalldatetime, dwloader arrondit les secondes et fractions de seconde. Par exemple, 1999-05-01 20:10:35.123 chargera 01-05 20:11.|  
|Littéral de chaîne dans **date** format|« AAAA-MM-JJ »<br /><br />Exemple : « 2007-05-08'|Valeurs d’heure (heures, minutes, secondes et fractions) sont définies à 0 lorsque la valeur est insérée.|  
  
### <a name="date-data-type"></a>Type de données date  
Le tableau suivant définit le format par défaut et les règles pour le chargement des valeurs littérales dans une colonne de type **date**. Une chaîne vide (") est convertie en la valeur par défaut ' 1900-01-01 ». Les chaînes qui contiennent uniquement des espaces à droite (' ') génère une erreur.  
  
|Type de données d’entrée|Exemples de données d’entrée|Conversion en Type de données de date|  
|-------------------|-----------------------|--------------------------------|  
|Littéral de chaîne dans **date** format|« AAAA-MM-JJ »<br /><br />Exemple : « 2007-05-08'||  
  
### <a name="time-data-type"></a>Type de données heure  
Le tableau suivant définit le format par défaut et les règles pour le chargement des valeurs littérales dans une colonne de type **temps**. Une chaîne vide (") est convertie en la valeur par défaut '00:00:00.0000'. Les chaînes qui contiennent uniquement des espaces à droite (' ') génère une erreur.  
  
|Type de données d’entrée|Exemples de données d’entrée|Conversion en Type de données heure|  
|-------------------|-----------------------|--------------------------------|  
|Littéral de chaîne dans **temps** format|'ss.fffffff'<br /><br />Exemple : '12:35:29.1234567'|Si la source de données a une précision inférieure ou égale (nombre de chiffres fractionnaires) à la précision de la **temps** type de données, les données sont complétées à droite avec des zéros. Par exemple, une valeur littérale '12:35:29.123' est insérée en tant que '12:35:29.1230000'.|  
  
### <a name="datetimeoffset-data-type"></a>Types de données DateTimeOffset  
Le tableau suivant définit le format par défaut et les règles pour le chargement des valeurs littérales dans une colonne de type **datetimeoffset** (*n*). Le format par défaut est ' : ss.fffffff AAAA-MM-JJ {+ |-} HH : mm ». Une chaîne vide (") est convertie en la valeur par défaut ' 1900-01-01 12:00:00.0000000 + 00:00 ». Les chaînes qui contiennent uniquement des espaces à droite (' ') génère une erreur. Le nombre de chiffres fractionnaires dépend de la définition de colonne. Par exemple, une colonne définie en tant que **datetimeoffset** (2) aura deux chiffres fractionnaires.  
  
|Type de données d’entrée|Exemples de données d’entrée|Conversion en types de données datetimeoffset|  
|-------------------|-----------------------|------------------------------------------|  
|Littéral de chaîne dans **datetime** format|'AAAA-MM-JJ HH : mm : [.fff]'<br /><br />Exemple : « 2007-05-08 12:35:29.123'|Les chiffres fractionnaires manquantes et les valeurs de décalage sont définies à 0 lorsque la valeur est insérée. Par exemple, le littéral ' 2007-05-08 12:35:29.123 » est inséré en tant que « 2007-05-08 12:35:29.1230000 + 00:00 ».|  
|Littéral de chaîne dans **smalldatetime** format|'AAAA-MM-JJ HH'<br /><br />Exemple : « 2007-05-08 12:35 '|Secondes, les chiffres fractionnaires restants et les valeurs de décalage sont définies à 0 lorsque la valeur est insérée.|  
|Littéral de chaîne dans **date** format|« AAAA-MM-JJ »<br /><br />Exemple : « 2007-05-08'|Valeurs d’heure (heures, minutes, secondes et fractions) sont définies à 0 lorsque la valeur est insérée. Par exemple, le littéral ' 2007-05-08' est inséré en tant que « 2007-05-08 00:00:00.0000000 + 00:00 ».|  
|Littéral de chaîne dans **datetime2** format|'AAAA-MM-JJ ss.fffffff'<br /><br />Exemple : « 2007-05-08 12:35:29.1234567'|La source de données ne peut pas dépasser le nombre spécifié de fraction de seconde dans la colonne de datetimeoffset. Si la source de données possède un nombre plus petit ou égal de fraction de seconde, les données sont complétées à droite avec des zéros. Par exemple, si le type de données est datetimeoffset (5), la valeur littérale ' 2007-05-08 12:35:29.123 + 12:15 ' est inséré en tant que ' 12:35:29.12300 + 12:15 '.|  
|Littéral de chaîne dans **datetimeoffset** format|' : ss.fffffff AAAA-MM-JJ {+ &#124; ;-} hh : mm '<br /><br />Exemple : « 2007-05-08 12:35:29.1234567 + 12:15 '|La source de données ne peut pas dépasser le nombre spécifié de fraction de seconde dans la colonne de datetimeoffset. Si la source de données possède un nombre plus petit ou égal de fraction de seconde, les données sont complétées à droite avec des zéros. Par exemple, si le type de données est datetimeoffset (5), la valeur littérale ' 2007-05-08 12:35:29.123 + 12:15 ' est inséré en tant que ' 12:35:29.12300 + 12:15 '.|  
  
### <a name="datetime2-data-type"></a>Type de données datetime2  
Le tableau suivant définit le format par défaut et les règles pour le chargement des valeurs littérales dans une colonne de type **datetime2** (*n*). Le format par défaut est 'AAAA-MM-JJ ss.fffffff'. Une chaîne vide (") est convertie en la valeur par défaut ' 1900-01-01-12:00:00 ». Les chaînes qui contiennent uniquement des espaces à droite (' ') génère une erreur. Le nombre de chiffres fractionnaires dépend de la définition de colonne. Par exemple, une colonne définie en tant que **datetime2** (2) aura deux chiffres fractionnaires.  
  
|Type de données d’entrée|Exemples de données d’entrée|Conversion en Type de données datetime2|  
|-------------------|-----------------------|-------------------------------------|  
|Littéral de chaîne dans **datetime** format|'AAAA-MM-JJ HH : mm : [.fff]'<br /><br />Exemple : « 2007-05-08 12:35:29.123'|Les fractions de secondes sont facultatives et sont définies sur 0 lorsque la valeur est insérée.|  
|Littéral de chaîne dans **smalldatetime** format|'AAAA-MM-JJ HH'<br /><br />Exemple : « 2007-05-08 12'|Secondes facultatif et chiffres fractionnaires restants sont égales à 0 lorsque la valeur est insérée.|  
|Littéral de chaîne dans **date** format|« AAAA-MM-JJ »<br /><br />Exemple : « 2007-05-08'|Valeurs d’heure (heures, minutes, secondes et fractions) sont définies à 0 lorsque la valeur est insérée. Par exemple, le littéral ' 2007-05-08' est inséré en tant que « 2007-05-08 12:00:00.0000000'.|  
|Littéral de chaîne dans **datetime2** format|'AAAA-MM-JJ hh:mm:ss:fffffff'<br /><br />Exemple : « 2007-05-08 12:35:29.1234567'|Si la source de données contient des composants de date et d’heure qui sont inférieur ou égal à la valeur spécifiée dans **datetime2**(*n*), les données sont insérées ; sinon, une erreur est générée.|  
  
### <a name="DateFormats"></a>Formats de date/heure  
Dwloader prend en charge les formats de données suivants pour les données d’entrée son chargement dans SQL Server PDW. Plus de détails sont répertoriés après le tableau.  
  
|datetime|smalldatetime|date|datetime2|datetimeoffset|  
|------------|-----------------|--------|-------------|------------------|  
|[M [M]] M-[d] [aa] d-yy HH : mm : [.fff]|[M [M]] M-[d] [aa] d-yy HH : mm [ : 00]|[M [M]] M-[d] d-[aa] AA|[M [M]] M-[d] [aa] d-yy HH : mm : [.fffffff]|[M [M]] M-[d] [aa] d-yy HH : mm : [.fffffff] zzz|  
|[M [M]] M-[d] [aa] d-yy HH : mm : [.fff] [tt]|[M [M]] M-[d] [aa] d-yy HH : mm [ : 00] [tt]||[M [M]] M-[d] [aa] d-yy HH : mm : [.fffffff] [tt]|[M [M]] M-[d] [aa] d-yy HH : mm : [.fffffff] [tt] zzz|  
|[M [M]] M [aa] AA-[d]-d hh : mm : [.fff]|[M [M]] M [aa] AA-[d]-d hh : mm [ : 00]|[M [M]] M [aa] AA-[d]-d|[M [M]] M [aa] AA-[d]-d hh : mm : [.fffffff]|[M [M]] M [aa] AA-[d]-d hh : mm : [.fffffff] zzz|  
|[M [M]] M-[aa] AA-[d] HH : mm : d [.fff] [tt]|[M [M]] M-[aa] AA-[d] HH : mm d [ : 00] [tt]||[M [M]] M-[aa] AA-[d] HH : mm : d [.fffffff] [tt]|[M [M]] M-[aa] AA-[d] HH : mm : d [.fffffff] [tt] zzz|  
|[aa] AA-[M [M]] [d] M-d hh : mm : [.fff]|[aa] AA-[M [M]] [d] M-d hh : mm [ : 00]|[aa] AA-[M [M]] [d] M-d|[aa] AA-[M [M]] [d] M-d hh : mm : [.fffffff]|[aa] AA-[M [M]] HH : mm : d [.fffffff] zzz de M-[d]|  
|[aa] AA-[M [M]] [d] M-d hh : mm : [.fff] [tt]|[aa] AA-[M [M]] [d] M-d hh : mm [ : 00] [tt]||[aa] AA-[M [M]] [d] M-d hh : mm : [.fffffff] [tt]|[aa] AA-[M [M]] [d] M-d hh : mm : [.fffffff] [tt] zzz|  
|[aa] AA-[d] [M [M]] d-M hh : mm : [.fff]|[aa] AA-[d] [M [M]] d-M hh : mm [ : 00]|[aa] AA - d [d]-[M [M]] M|[aa] AA-[d] [M [M]] d-M hh : mm : [.fffffff]|[aa] AA-[d] M hh : mm : [.fffffff] zzz de d-[M [M]]|  
|[aa] AA-[d] [M [M]] d-M hh : mm : [.fff] [tt]|[aa] AA-[d] [M [M]] d-M hh : mm [ : 00] [tt]||[aa] AA-[d] [M [M]] d-M hh : mm : [.fffffff] [tt]|[aa] AA-[d] [M [M]] d-M hh : mm : [.fffffff] [tt] zzz|  
|[d] [M [M]] d-M-[aa] AA HH : mm : [.fff]|[d] [M [M]] d-M-[aa] AA HH : mm [ : 00]|[d] [M [M]] d-M-[aa] AA|[d] [M [M]] d-M-[aa] AA HH : mm : [.fffffff]|[d] [M [M]] d-M-[aa] AA HH : mm : [.fffffff] zzz|  
|[d] [M [M]] d-M-[aa] AA HH : mm : [.fff] [tt]|[d] [M [M]] d-M-[aa] AA HH : mm [ : 00] [tt]||[d] [M [M]] d-M-[aa] AA HH : mm : [.fffffff] [tt]|[d] [M [M]] d-M-[aa] AA HH : mm : [.fffffff] [tt] zzz|  
|d [d]-[aa] AA-[M [M]] M hh : mm : [.fff]|d [d]-[aa] AA-[M [M]] M hh : mm [ : 00]|d [d]-[aa] AA-[M [M]] M|d [d]-[aa] AA-[M [M]] M hh : mm : [.fffffff]|[d] d-[aa] AA-[M [M]] M hh : mm : [.fffffff] zzz|  
|[d] d-[aa] AA-[M [M]] M hh : mm : [.fff] [tt]|[d] d-[aa] AA-[M [M]] M hh : mm [ : 00] [tt]||[d] d-[aa] AA-[M [M]] M hh : mm : [.fffffff] [tt]|[d] d-[aa] AA-[M [M]] M hh : mm : [.fffffff] [tt] zzz|  
  
Détails :  
  
-   Pour séparer les valeurs mois, jour et année, vous pouvez utiliser ':', '/' ou '. '. Par souci de simplicité, la table utilise uniquement le séparateur ':'.  
  
-   Pour spécifier le mois sous forme de texte utilisez trois caractères ou plus. Mois avec 1 ou 2 caractères seront interprétés comme un nombre.  
  
-   Pour séparer les valeurs d’heure, utilisez le ' : ' symbole.  
  
-   Lettres entourés crochets sont facultatifs.  
  
-   Les lettres « tt » désigner [AM | PM | am | pm]. AM est la valeur par défaut. Lorsque « tt » est spécifié, la valeur d’heure (hh) doit être dans la plage de 0 à 12.  
  
-   Les lettres « zzz » désigne le décalage de fuseau horaire pour fuseau horaire du système dans le format {+ |-} HH:ss].  
  
## <a name="InsertNumerictypes"></a>Insertion de littéraux dans les Types numériques  
Les tableaux suivants définissent les règles de format et de conversion de valeur par défaut pour le chargement d’une valeur littérale dans une colonne SQL Server PDW qui utilise un type numérique.  
  
### <a name="bit-data-type"></a>Type de données bit  
Le tableau suivant définit le format par défaut et les règles pour le chargement des valeurs littérales dans une colonne de type **bits**. Une chaîne vide (") ou une chaîne qui contiennent uniquement des espaces à droite (' ') est convertie en 0.  
  
|Type de données d’entrée|Exemples de données d’entrée|Conversion en Type de données bit|  
|-------------------|-----------------------|-------------------------------|  
|Littéral de chaîne dans **entier** format|'ffffffffff'<br /><br />Exemple : '1' ou '321'|Une valeur entière mise en forme comme un littéral de chaîne ne peut pas contenir une valeur négative. Par exemple, la valeur '-' 123 génère une erreur.<br /><br />Une valeur supérieure à 1 est convertie en 1. Par exemple, la valeur « 123 » est convertie 1.|  
|Littéral de chaîne|'TRUE' ou 'FALSE'<br /><br />Exemple : 'true'|La valeur 'TRUE' est converti en 1 ; la valeur 'FALSE' est convertie en 0.|  
|Littéral d’entier|fffffffn<br /><br />Exemple : 1 ou 321|Une valeur supérieure à 1 ou inférieure à 0 est convertie en 1. Par exemple, les valeurs 123 et -123 sont converties à 1.|  
|Littéral décimal|fffnn.fffn<br /><br />Exemple : 1234.5678|Une valeur supérieure à 1 ou inférieure à 0 est convertie en 1. Par exemple, les valeurs 123,45 et -123,45 sont converties à 1.|  
  
### <a name="decimal-data-type"></a>Type de données Decimal  
Le tableau suivant définit les règles pour le chargement des valeurs littérales dans une colonne de type **décimal** (*p, s*). Les règles de conversion de données sont les mêmes que pour SQL Server. Pour plus d’informations, consultez [Conversion de Type de données (moteur de base de données)](http://go.microsoft.com/fwlink/?LinkId=202128) sur MSDN.  
  
|Type de données d’entrée|Exemples de données d’entrée|  
|-------------------|-----------------------|  
|Littéral d’entier|321312313123|  
|Littéral décimal|123344.34455|  
  
### <a name="float-and-real-data-types"></a>Types de données float et real  
Le tableau suivant définit les règles pour le chargement des valeurs littérales dans une colonne de type **float** ou **réel**. Les règles de conversion de données sont les mêmes que pour SQL Server. Pour plus d’informations, consultez [Conversion de Type de données (moteur de base de données)](../t-sql/data-types/data-type-conversion-database-engine.md) sur MSDN.  
  
|Type de données d’entrée|Exemples de données d’entrée|  
|-------------------|-----------------------|  
|Littéral d’entier|321312313123|  
|Littéral décimal|123344.34455|  
|Littéral de point flottant|3.12323E + 14.|  
  
### <a name="int-bigint-tinyint-smallint-data-types"></a>int, bigint, tinyint, smallint des Types de données  
Le tableau suivant définit les règles pour le chargement des valeurs littérales dans une colonne de type **int**, **bigint**, **tinyint**, ou **smallint**. La source de données ne peut pas dépasser la plage autorisée pour le type de données spécifiée. Par exemple, la plage de **tinyint** est comprise entre 0 et 255 et la plage pour **int** est allant de -2,147,483,648 à 2 147 483 647.  
  
|Type de données d’entrée|Exemples de données d’entrée|Conversion en Types de données Integer|  
|-------------------|-----------------------|------------------------------------|  
|Littéral d’entier|321312313123||  
|Littéral décimal|123344.34455|Les valeurs à droite du séparateur décimal sont tronquées.|  
  
### <a name="money-and-smallmoney-data-types"></a>Types de données Money et smallmoney  
Les valeurs littérales Money sont représentées sous forme de chaîne de nombres avec un séparateur décimal facultatif et un symbole monétaire en tant que préfixe. La source de données ne peut pas dépasser la plage autorisée pour le type de données spécifiée. Par exemple, la plage de **smallmoney** est entre-214 748,3648 et 214 748,3647 la plage pour **money** est -922,337,203,685,477.5808 à 922,337,203,685,477.5807. Le tableau suivant définit les règles pour le chargement des valeurs littérales dans une colonne de type **money** ou **smallmoney**.  
  
|Type de données d’entrée|Exemples de données d’entrée|Conversion en money ou smallmoney, Type de données|  
|-------------------|-----------------------|-----------------------------------------------|  
|Littéral d’entier|321312|Chiffres manquants après la virgule décimale sont définies à 0 lorsque la valeur est insérée. Par exemple, le littéral 12345 est inséré en tant que 12345.0000|  
|Littéral décimal|123344.34455|Si le nombre de chiffres après la virgule décimale dépasse 4, la valeur est arrondie à la valeur la plus proche. Par exemple, la valeur 123344.34455 est insérée en tant que 123344.3446.|  
|Money littéral|$123456.7890|Le symbole de devise n’est pas inséré avec la valeur.<br /><br />Si le nombre de chiffres après la virgule décimale dépasse 4, la valeur est arrondie à la valeur la plus proche.|  
  
## <a name="InsertStringTypes"></a>Insertion de littéraux dans les Types de chaînes  
Les tableaux suivants définissent les règles de format et de conversion par défaut pour le chargement d’une valeur littérale dans une colonne SQL Server PDW qui utilise un type chaîne.  
  
### <a name="char-varchar-nchar-and-nvarchar-data-types"></a>Types de données char, varchar, nchar et nvarchar  
Le tableau suivant définit le format par défaut et les règles pour le chargement des valeurs littérales dans une colonne de type **char**, **varchar**, **nchar** et **nvarchar** . La longueur de source de données ne peut pas dépasser la taille spécifiée pour le type de données. Si la longueur de source de données est inférieure à la taille de la **char** ou **nchar** type de données, les données sont complétées à droite avec des espaces vides pour atteindre la taille de type de données.  
  
|Type de données d’entrée|Exemples de données d’entrée|Conversion en Types de données caractère|  
|---------------|-------------------|----------------------------------|  
|Littéral de chaîne|Format : « chaîne de caractères'<br /><br />Exemple : 'abc'| N/A |  
|Littéral de chaîne Unicode|Format : Chaîne N'character'<br /><br />Exemple : N’ABC »| N/A |  
|Littéral d’entier|Format : ffffffffffn<br /><br />Exemple : 321312313123| N/A |  
|Littéral décimal|Format : ffffff.fffffff<br /><br />Exemple : 12344.34455| N/A |  
|Money littéral|Format : $ffffff.fffnn<br /><br />Exemple : $123456.99|Le symbole monétaire n’est pas inséré avec la valeur. Pour insérer le symbole de devise, insérez la valeur comme un littéral de chaîne. Cela fera correspondre le format du chargeur, lequel traite chaque littéral comme un littéral de chaîne.<br /><br />Des virgules ne sont pas autorisés.<br /><br />Si le nombre de chiffres après la virgule décimale dépasse 2, la valeur est arrondie à la valeur la plus proche. Par exemple, la valeur 123.946789 est insérée en tant que 123.95.<br /><br />Seul le style par défaut 0 (pas de virgule et 2 chiffres après la virgule décimale) est autorisé lors de l’utilisation de la fonction CONVERT pour insérer des littéraux de l’argent.|  
  
### <a name="general-remarks"></a>Remarques d'ordre général  
**dwloader** effectue des conversions implicites mêmes que SMP SQL Server effectue, mais ne prend pas en charge toutes les conversions implicites qui prend en charge SMP SQL Server.  
 
<!-- MISSING LINKS 
## See Also  
[Grant Permissions to Load Data &#40;SQL Server PDW&#41;](../sqlpdw/grant-permissions-to-load-data-sql-server-pdw.md)  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  

-->
  

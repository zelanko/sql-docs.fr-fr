---
title: Charger des données avec INSERT
description: Utilisation de l’instruction T-SQL INSERT pour charger des données dans une table en parallèle Data Warehouse (PDW) distribuée ou répliquée.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: bbcf1a8bd16d7446841bb6d7dd86bd1ad350280d
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401021"
---
# <a name="load-data-with-insert-into-parallel-data-warehouse"></a>Charger des données avec INSERT dans Parallel Data Warehouse

Vous pouvez utiliser l’instruction TSQL INSERT pour charger des données dans une table SQL Server parallèle Data Warehouse (PDW) distribuée ou répliquée. Pour plus d’informations sur INSERT, consultez [Insert](../t-sql/statements/insert-transact-sql.md). Pour les tables répliquées et toutes les colonnes de non-distribution dans une table distribuée, PDW utilise SQL Server pour convertir implicitement les valeurs de données spécifiées dans l’instruction dans le type de données de la colonne de destination. Pour plus d’informations sur SQL Server règles de conversion de données, consultez [conversion de types de données pour SQL](../t-sql/data-types/data-type-conversion-database-engine.md). Toutefois, pour les colonnes de distribution, PDW ne prend en charge qu’un sous-ensemble de conversions implicites prises en charge par SQL Server. Par conséquent, lorsque vous utilisez l’instruction INSERT pour charger des données dans une colonne de distribution, les données sources doivent être spécifiées dans l’un des formats définis dans les tableaux suivants.  
  
  
## <a name="InsertingLiteralsBinary"></a>Insérer des littéraux dans des types binaires  
Le tableau suivant définit les types de littéraux, le format et les règles de conversion acceptés pour l’insertion d’une valeur littérale dans une colonne de distribution de type **Binary** (*n*) ou **varbinary**(*n*).  
  
|Type littéral|Format|Règles de conversion|  
|----------------|----------|--------------------|  
|Littéral binaire|0x*hexidecimal_string*<br /><br />Exemple : 0x12Ef|Les littéraux binaires doivent être précédés de 0x.<br /><br />La longueur de la source de données ne peut pas dépasser le nombre d’octets spécifié pour le type de données.<br /><br />Si la longueur de la source de données est inférieure à la taille du type de données **Binary** , les données sont complétées à droite avec des zéros pour atteindre la taille du type de données.|  
  
## <a name="InsertingLiteralsDateTime"></a>Insérer des littéraux dans des types de date et d’heure  
Les littéraux de date et d’heure sont représentés à l’aide de valeurs de caractères dans des formats spécifiques, placés entre guillemets simples. Les tableaux suivants définissent les types de littéraux, le format et les règles de conversion autorisés pour l’insertion d’un littéral de date ou d’heure dans une colonne de distribution SQL Server PDW de type **DateTime**, **smalldatetime**, **Date**, **Time**, **DateTimeOffset**ou **datetime2**.  
  
### <a name="datetime-data-type"></a>datetime (type de données)  
Le tableau suivant définit les formats et les règles acceptés pour l’insertion de valeurs littérales dans une colonne de distribution de type **DateTime**. Toute chaîne vide (' ') est convertie en valeur par défaut' 1900-01-01 12:00:00.000 '. Les chaînes qui contiennent uniquement des espaces (' ') génèrent une erreur.  
  
|Type littéral|Format|Règles de conversion|  
|----------------|----------|--------------------|  
|Littéral de chaîne au format **DateTime**|'AAAA-MM-JJ hh : mm : SS [. nnn] '<br /><br />Exemple : « 2007-05-08 12:35:29.123 »|Les chiffres fractionnaires manquants sont définis sur 0 lorsque la valeur est insérée. Par exemple, le littéral « 2007-05-08 12:35 » est inséré en tant que « 2007-05-08 12:35:00.000 ».|  
|Littéral de chaîne au format **smalldatetime**|'AAAA-MM-JJ hh : mm'<br /><br />Exemple : « 2007-05-08 12:35 »|Les secondes et les chiffres fractionnaires restants sont définis sur 0 lorsque la valeur est insérée.|  
|Littéral de chaîne dans le format de **Date**|'AAAA-MM-JJ'<br /><br />Exemple : « 2007-05-08 »|Les valeurs d’heure (heure, minutes, secondes et fractions) sont définies sur 12:00:00.000 lorsque la valeur est insérée.|  
|Littéral de chaîne au format **datetime2**|'AAAA-MM-JJ hh : mm : SS. nnnnnnn'<br /><br />Exemple : « 2007-05-08 12:35:29.1234567 »|Les données sources ne peuvent pas dépasser trois chiffres fractionnaires. Par exemple, le littéral « 2007-05-08 12:35:29.123 » sera inséré, mais la valeur « 2007-05-08 12:35:29.1234567 » génère une erreur.|  
  
### <a name="smalldatetime-data-type"></a>smalldatetime (type de données)  
Le tableau suivant définit les formats et les règles acceptés pour l’insertion de valeurs littérales dans une colonne de distribution de type **smalldatetime**. Toute chaîne vide (' ') est convertie en valeur par défaut' 1900-01-01 12:00 '. Les chaînes qui contiennent uniquement des espaces (' ') génèrent une erreur.  
  
|Type littéral|Format|Règles de conversion|  
|----------------|----------|--------------------|  
|Littéral de chaîne au format **smalldatetime**|« YYYY-MM-JJ hh : mm » ou « YYYY-MM-JJ hh : mm : 00 »<br /><br />Exemple : « 2007-05-08 12:00 » ou « 2007-05-08 12:00:00 »|Les données sources doivent avoir des valeurs pour l’année, le mois, la date, l’heure et la minute. Les secondes sont facultatives et, le cas échéant, doivent être définies sur la valeur 00. Toute autre valeur génère une erreur.|  
|Littéral de chaîne dans le format de **Date**|'AAAA-MM-JJ'<br /><br />Exemple : « 2007-05-08 »|Les valeurs d’heure (heure, minutes, secondes et fractions) sont définies sur 0 lorsque la valeur est insérée.|  
  
### <a name="date-data-type"></a>type de données date  
Le tableau suivant définit les formats et les règles acceptés pour l’insertion de valeurs littérales dans une colonne de distribution de type **Date**. Toute chaîne vide (' ') est convertie en valeur par défaut' 1900-01-01 '. Les chaînes qui contiennent uniquement des espaces (' ') génèrent une erreur.  
  
|Type littéral|Format|Règles de conversion|  
|----------------|----------|--------------------|  
|Littéral de chaîne dans le format de **Date**|'AAAA-MM-JJ'<br /><br />Exemple : « 2007-05-08 »|Il s’agit du seul format accepté.|  
  
### <a name="time-data-type"></a>time (types de données)  
Le tableau suivant définit les formats et les règles acceptés pour l’insertion de valeurs littérales dans une colonne de distribution de type **Time**. Toute chaîne vide (' ') est convertie en valeur par défaut' 00:00:00.0000 '. Les chaînes qui contiennent uniquement des espaces (' ') génèrent une erreur.  
  
|Type littéral|Format|Règles de conversion|  
|----------------|----------|--------------------|  
|Littéral de chaîne dans le format d' **heure**|« hh : mm : SS. nnnnnnn »<br /><br />Exemple : « 12:35:29.1234567 »|Si la source de données a une précision inférieure ou égale (nombre de chiffres fractionnaires) par rapport à la précision du type de données **Time** , les données sont complétées à droite par des zéros. Par exemple, une valeur littérale « 12:35:29.123 » est insérée en tant que « 12:35:29.1230000 ».<br /><br />Une valeur dont la précision est supérieure à celle du type de données cible est rejetée.|  
  
### <a name="datetimeoffset-data-type"></a>datetimeoffset (type de données)  
Le tableau suivant définit les formats et les règles acceptés pour l’insertion de valeurs littérales dans une colonne de distribution de type **DateTimeOffset** (*n*). Le format par défaut est « YYYY-MM-JJ hh : mm : SS. nnnnnnn {+ |-} hh : mm ». Une chaîne vide (« ») est convertie en valeur par défaut «1900-01-01 12:00:00.0000000 + 00:00 ». Les chaînes qui contiennent uniquement des espaces (' ') génèrent une erreur. Le nombre de chiffres fractionnaires dépend de la définition de la colonne. Par exemple, une colonne définie en tant que **DateTimeOffset** (2) aura deux chiffres fractionnaires.  
  
|Type littéral|Format|Règles de conversion|  
|----------------|----------|--------------------|  
|Littéral de chaîne au format **DateTime**|'AAAA-MM-JJ hh : mm : SS [. nnn] '<br /><br />Exemple : « 2007-05-08 12:35:29.123 »|Les chiffres fractionnaires manquants et les valeurs de décalage sont définis sur 0 lorsque la valeur est insérée. Par exemple, le littéral « 2007-05-08 12:35:29.123 » est inséré en tant que « 2007-05-08 12:35:29.1230000 + 00:00 ».|  
|Littéral de chaîne au format **smalldatetime**|'AAAA-MM-JJ hh : mm'<br /><br />Exemple : « 2007-05-08 12:35 »|Secondes, les chiffres fractionnaires restants et les valeurs de décalage sont définis sur 0 lorsque la valeur est insérée.|  
|Littéral de chaîne dans le format de **Date**|'AAAA-MM-JJ'<br /><br />Exemple : « 2007-05-08 »|Les valeurs d’heure (heure, minutes, secondes et fractions) sont définies sur 0 lorsque la valeur est insérée. Par exemple, le littéral « 2007-05-08 » est inséré en tant que « 2007-05-08 00:00:00.0000000 + 00:00 ».|  
|Littéral de chaîne au format **datetime2**|'AAAA-MM-JJ hh : mm : SS. nnnnnnn'<br /><br />Exemple : « 2007-05-08 12:35:29.1234567 »|Les données sources ne peuvent pas dépasser le nombre spécifié de fractions de seconde dans la colonne DateTimeOffset. Si la source de données a un nombre inférieur ou égal de fractions de seconde, les données sont complétées à droite par des zéros. Par exemple, si le type de données est DateTimeOffset (5), la valeur littérale « 2007-05-08 12:35:29.123 + 12:15 » est insérée en tant que « 12:35:29.12300 + 12:15 ».|  
|Littéral de chaîne au format **DateTimeOffset**|'AAAA-MM-JJ hh : mm : SS. nnnnnnn {+&#124;-} hh : mm'<br /><br />Exemple : « 2007-05-08 12:35:29.1234567 + 12:15 »|Les données sources ne peuvent pas dépasser le nombre spécifié de fractions de seconde dans la colonne DateTimeOffset. Si la source de données a un nombre inférieur ou égal de fractions de seconde, les données sont complétées à droite par des zéros. Par exemple, si le type de données est DateTimeOffset (5), la valeur littérale « 2007-05-08 12:35:29.123 + 12:15 » est insérée en tant que « 12:35:29.12300 + 12:15 ».|  
  
### <a name="datetime2-data-type"></a>datetime2 (type de données)  
Le tableau suivant définit les formats et les règles acceptés pour l’insertion de valeurs littérales dans une colonne de distribution de type **datetime2** (*n*). Le format par défaut est « AAAA-MM-JJ hh : mm : SS. nnnnnnn ». Une chaîne vide (' ') est convertie en valeur par défaut' 1900-01-01 12:00:00 '. Les chaînes qui contiennent uniquement des espaces (' ') génèrent une erreur. Le nombre de chiffres fractionnaires dépend de la définition de la colonne. Par exemple, une colonne définie en tant que **datetime2** (2) aura deux chiffres fractionnaires.  
  
|Type littéral|Format|Règles de conversion|  
|----------------|----------|--------------------|  
|Littéral de chaîne au format **DateTime**|'AAAA-MM-JJ hh : mm : SS [. nnn] '<br /><br />Exemple : « 2007-05-08 12:35:29.123 »|Les fractions de seconde sont facultatives et sont définies sur 0 lorsque la valeur est insérée.<br /><br />Valeur qui a plus de chiffres fractionnaires que le type de données cible est rejeté.|  
|Littéral de chaîne au format **smalldatetime**|'AAAA-MM-JJ hh : mm'<br /><br />Exemple : « 2007-05-08 12 »|Les secondes facultatives et les chiffres fractionnaires restants sont définis sur 0 lorsque la valeur est insérée.|  
|Littéral de chaîne dans le format de **Date**|'AAAA-MM-JJ'<br /><br />Exemple : « 2007-05-08 »|Les valeurs d’heure (heure, minutes, secondes et fractions) sont définies sur 0 lorsque la valeur est insérée. Par exemple, le littéral « 2007-05-08 » est inséré en tant que « 2007-05-08 12:00:00.0000000 ».|  
|Littéral de chaîne au format **datetime2**|'AAAA-MM-JJ hh : mm : SS : nnnnnnn'<br /><br />Exemple : « 2007-05-08 12:35:29.1234567 »|Si la source de données contient des composants de données et d’heure qui sont inférieurs ou égaux à la valeur spécifiée dans **datetime2**(*n*), les données sont insérées. dans le cas contraire, une erreur est générée.|  
  
## <a name="InsertLiteralsNumeric"></a>Insérer des littéraux dans des types numériques  
Les tableaux suivants définissent les formats et les règles de conversion acceptés pour l’insertion d’une valeur littérale dans une colonne de distribution SQL Server PDW qui utilise un type numérique.  
  
### <a name="bit-data-type"></a>type de données bit  
Le tableau suivant définit les formats et les règles acceptés pour l’insertion de valeurs littérales dans une colonne de distribution de type **bit**. Une chaîne vide (' ') ou une chaîne qui contient uniquement des espaces (' ') est convertie en 0.  
  
|Type littéral|format|Règles de conversion|  
|----------------|----------|--------------------|  
|Littéral de chaîne au format **entier**|'nnnnnnnnnn'<br /><br />Exemple : ' 1 'ou' 321 '|Une valeur entière mise en forme en tant que littéral de chaîne ne peut pas contenir de valeur négative. Par exemple, la valeur « -123 » génère une erreur.<br /><br />Une valeur supérieure à 1 est convertie en 1. Par exemple, la valeur « 123 » est convertie en 1.|  
|Littéral de chaîne|« TRUE » ou « FALSe »<br /><br />Exemple : « true »|La valeur « TRUE » est convertie en 1 ; la valeur « FALSe » est convertie en 0.|  
|Littéral d’entier|nnnnnnnn<br /><br />Exemple : 1 ou 321|Une valeur supérieure à 1 ou inférieure à 0 est convertie en 1. Par exemple, les valeurs 123 et-123 sont converties en 1.|  
|Littéral décimal|nnnnn. nnnn<br /><br />Exemple : 1234,5678|Une valeur supérieure à 1 ou inférieure à 0 est convertie en 1. Par exemple, les valeurs 123,45 et-123,45 sont converties en 1.|  
  
### <a name="decimal-data-type"></a>type de données decimal  
Le tableau suivant définit les formats et les règles acceptés pour l’insertion de valeurs littérales dans une colonne de distribution de type **Decimal** (*p, s*). Les règles de conversion de données sont les mêmes que pour les SQL Server. Pour plus d’informations, consultez [conversion de types de données](../t-sql/data-types/data-type-conversion-database-engine.md) sur MSDN.  
  
|Type littéral|Format|  
|----------------|----------|  
|Littéral de chaîne au format **entier**|nnnnnnnnnnnn<br /><br />Exemple : « 321312313123 »|  
|Littéral de chaîne au format **décimal**|'nnnnnn. nnnnn'<br /><br />Exemple : « 123344,34455 »|  
|Littéral d’entier|nnnnnnnnnnnn<br /><br />Exemple : 321312313123|  
|Littéral décimal|nnnnnn. nnnnn<br /><br />Exemple : « 123344,34455 »|  
  
### <a name="float-and-real-data-types"></a>types de données float et Real  
Le tableau suivant définit les formats et les règles acceptés pour l’insertion de valeurs littérales dans une colonne de distribution de type **float** ou **Real**. Les règles de conversion de données sont les mêmes que pour les SQL Server. Pour plus d’informations, consultez [conversion de types de données](../t-sql/data-types/data-type-conversion-database-engine.md) sur MSDN.  
  
|Type littéral|Format|  
|----------------|----------|  
|Littéral de chaîne au format **entier**|nnnnnnnnnnnn<br /><br />Exemple : « 321312313123 »|  
|Littéral de chaîne au format **décimal**|'nnnnnn. nnnnn'<br /><br />Exemple : « 123344,34455 »|  
|Littéral de chaîne au format à **virgule flottante**|'n. nnnnnE + nn'<br /><br />Exemple : ' 3.12323 E + 14 '|  
|Littéral d’entier|nnnnnnnnnnnn<br /><br />Exemple : 321312313123|  
|Littéral décimal|nnnnnn. nnnnn<br /><br />Exemple : 123344,34455|  
|Littéral à virgule flottante|n. nnnnnE + nn<br /><br />Exemple : 3.12323 E + 14|  
  
### <a name="int-bigint-tinyint-smallint-data-types"></a>int, bigint, tinyint, smallint, types de données  
Le tableau suivant définit les formats et les règles acceptés pour l’insertion de valeurs littérales dans une colonne de distribution de type **int**, **bigint**, **tinyint**ou **smallint**. La source de données ne peut pas dépasser la plage autorisée pour le type de données spécifié. Par exemple, la plage de **tinyint** est comprise entre 0 et 255 et la plage de **int** est-2 147 483 648 à 2 147 483 647.  
  
|Type littéral|Format|Règles de conversion|  
|------------|------|----------------|
|Littéral de chaîne au format **entier**|'nnnnnnnnnnnnnn'<br /><br />Exemple : « 321312313123 »| Aucune |  
|Littéral d’entier|nnnnnnnnnnnnnn<br /><br />Exemple : 321312313123| Aucune|  
|Littéral décimal|nnnnnn. nnnnn<br /><br />Exemple : 123344,34455|Les valeurs à droite de la virgule décimale sont tronquées.|  
  
### <a name="money-and-smallmoney-data-types"></a>types de données Money et smallmoney  
Les valeurs littérales monétaires sont représentées sous forme de nombres avec un symbole décimal facultatif et un symbole monétaire comme préfixe. La source de données ne peut pas dépasser la plage autorisée pour le type de données spécifié. Par exemple, la plage de **smallmoney** est comprise entre-214 748,3648 et 214 748,3647 et la plage pour **money** est-922 337 203 685 477,5808 à 922 337 203 685 477,5807. Le tableau suivant définit les formats et les règles acceptés pour l’insertion de valeurs littérales dans une colonne de distribution de type **Money** ou **smallmoney**.  
  
|Type littéral|Format|Règles de conversion|  
|----------------|----------|--------------------|  
|Littéral de chaîne au format **entier**|nnnnnnnn<br /><br />Exemple : « 123433 »|Les chiffres manquants après la virgule décimale ont la valeur 0 lorsque la valeur est insérée. Par exemple, le littéral « 12345 » est inséré en tant que 12345,0000.|  
|Littéral de chaîne au format **décimal**|'nnnnnn. nnnnn'<br /><br />Exemple : « 123344,34455 »|Si le nombre de chiffres après la virgule décimale dépasse 4, la valeur est arrondie à la valeur la plus proche. Par exemple, la valeur « 123344,34455 » est insérée sous la forme 123344,3446.|  
|Littéral de chaîne au format **Money**|' $nnnnnn. nnnn'<br /><br />Exemple : « $123456,7890 »|Le symbole monétaire facultatif n’est pas inséré avec la valeur.<br /><br />Si le nombre de chiffres après la virgule décimale dépasse 4, la valeur est arrondie à la valeur la plus proche.|  
|Littéral d’entier|nnnnnnnn<br /><br />Exemple : 123433|Les chiffres manquants après la virgule décimale ont la valeur 0 lorsque la valeur est insérée. Par exemple, le littéral 12345 est inséré en tant que 12345,0000.|  
|Littéral décimal|nnnnnn. nnnnn<br /><br />Exemple : 123344,34455|Si le nombre de chiffres après la virgule décimale dépasse 4, la valeur est arrondie à la valeur la plus proche. Par exemple, la valeur 123344,34455 est insérée sous la forme 123344,3446.|  
|Littéral Money|$nnnnnn. nnnn<br /><br />Exemple : $123456,7890|Le symbole monétaire facultatif n’est pas inséré avec la valeur.<br /><br />Si le nombre de chiffres après la virgule décimale dépasse 4, la valeur est arrondie à la valeur la plus proche.|  
  
## <a name="InsertLiteralsString"></a>Insertion de littéraux dans des types String  
Les tableaux suivants définissent les formats et les règles de conversion acceptés pour l’insertion d’une valeur littérale dans une colonne SQL Server PDW qui utilise un type chaîne.  
  
### <a name="char-varchar-nchar-and-nvarchar-data-types"></a>types de données char, varchar, nchar et nvarchar  
Le tableau suivant définit les formats et les règles acceptés pour l’insertion de valeurs littérales dans une colonne de distribution de type **char**, **varchar**, **nchar** et **nvarchar**. La longueur de la source de données ne peut pas dépasser la taille spécifiée pour le type de données. Si la longueur de la source de données est inférieure à la taille du type de données **char** ou **nchar** , les données sont complétées à droite avec des espaces vides pour atteindre la taille du type de données.  
  
|Type littéral|Format|Règles de conversion|  
|----------------|----------|--------------------|  
|Littéral de chaîne|Format : 'chaîne de caractères'<br /><br />Exemple : « ABC »| Aucune|  
|Littéral de chaîne Unicode|Format : N’character chaîne'<br /><br />Exemple : N’abc'|  Aucune |  
|Littéral d’entier|Format : NNNNNNNNNNN<br /><br />Exemple : 321312313123| Aucune |  
|Littéral décimal|Format : nnnnnn. nnnnnnn<br /><br />Exemple : 12344,34455| Aucune |  
|Littéral Money|Format : $nnnnnn. nnnnn<br /><br />Exemple : $123456,99|Le symbole monétaire n’est pas inséré avec la valeur. Pour insérer le symbole monétaire, insérez la valeur en tant que littéral de chaîne. Cela correspond au format de l’outil **dwloader** , qui traite chaque littéral comme un littéral de chaîne.<br /><br />Les virgules ne sont pas autorisées.<br /><br />Si le nombre de chiffres après la virgule décimale dépasse 2, la valeur est arrondie à la valeur la plus proche. Par exemple, la valeur 123,946789 est insérée sous la forme 123,95.<br /><br />Seul le style par défaut 0 (aucune virgule et 2 chiffres après la virgule décimale) est autorisé lors de l’utilisation de la fonction CONVERT pour insérer des littéraux Money.|  

  
## <a name="see-also"></a>Voir aussi  
 
[Données distribuées](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-distributed-data/)  
[Insérer](../t-sql/statements/insert-transact-sql.md)  
  
<!-- MISSING LINKS
[Grant permissions to load data](grant-permissions-to-load-data.md)  
[Metadata query examples](metadata-query-examples.md) 
-->

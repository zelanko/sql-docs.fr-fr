---
title: 'C en SQL : Caractère | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- character data type [ODBC]
- data conversions from C to SQL types [ODBC], character
- converting data from c to SQL types [ODBC], character
ms.assetid: be66188a-ebdb-4c9e-af72-c379886766fa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0158da62ed360e926cdb5382b89b1491c0723550
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63201628"
---
# <a name="c-to-sql-character"></a>C en SQL : Caractère
Les identificateurs pour le caractère de type de données ODBC C sont :  
  
 SQL_C_CHAR  
  
 SQL_C_WCHAR  
  
 Le tableau suivant présente les types de données à laquelle les données de caractères C peuvent être converties à ODBC SQL. Pour obtenir une explication des colonnes et des termes dans la table, consultez [conversion des données à partir de C en Types de données SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
> [!NOTE]  
>  Lorsque les données de caractères C sont converties en données Unicode SQL, la longueur des données Unicode doit être un nombre pair.  
  
|Identificateur de type SQL|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Longueur d’octet de données < = longueur de colonne.<br /><br /> Longueur d’octet de données > longueur de colonne.|n/a<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Longueur des données de caractère < = longueur de colonne.<br /><br /> Longueur des données de caractères > longueur de colonne.|n/a<br /><br /> 22001|  
|SQL_DECIMAL<br /><br /> SQL_NUMERIC<br /><br /> SQL_TINYINT<br /><br /> SQL_SMALLINT<br /><br /> SQL_INTEGER SQL_BIGINT|Données converties sans troncation<br /><br /> Les données converties avec troncation de chiffres fractionnaires [e]<br /><br /> Conversion de données entraînerait une perte de chiffres dans son ensemble (par opposition aux fractions de seconde) [e]<br /><br /> Valeur de données n’est pas un *littéral numérique*|n/a<br /><br /> 22001<br /><br /> 22001<br /><br /> 22018|  
|SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE|Les données sont dans la plage du type de données à laquelle le nombre est converti<br /><br /> Données sont en dehors de la plage du type de données à laquelle le nombre est converti<br /><br /> Valeur de données n’est pas un *littéral numérique*|n/a<br /><br /> 22003<br /><br /> 22018|  
|SQL_BIT|Les données sont 0 ou 1<br /><br /> Données sont supérieures à 0, inférieure à 2 et non égal à 1<br /><br /> Données sont inférieur à 0 ou supérieur ou égal à 2<br /><br /> Données ne sont pas un *littéral numérique*|n/a<br /><br /> 22001<br /><br /> 22003<br /><br /> 22018|  
|SQL_BINARY<br /><br /> SQL_VARBINARY<br /><br /> SQL_LONGVARBINARY|(Longueur d’octet de données) / 2 < = longueur d’octet de colonne<br /><br /> (Longueur d’octet de données) / 2 > longueur d’octet de colonne<br /><br /> Valeur de données n’est pas une valeur hexadécimale|n/a<br /><br /> 22001<br /><br /> 22018|  
|SQL_TYPE_DATE|Valeur de données est valide *littéral de date ODBC*<br /><br /> Valeur de données est valide *littéral de timestamp ODBC*; partie heure est égale à zéro<br /><br /> Valeur de données est valide *littéral de timestamp ODBC*; partie heure est différent de zéro [a]<br /><br /> Valeur de données n’est pas valide *littéral de date ODBC* ou *littéral de l’horodatage ODBC*|n/a<br /><br /> n/a<br /><br /> 22008<br /><br /> 22018|  
|SQL_TYPE_TIME|Valeur de données est valide *littéral d’heure ODBC*<br /><br /> Valeur de données est valide *littéral de timestamp ODBC*; fractions de seconde partie des secondes est zéro [b]<br /><br /> Valeur de données est valide *littéral de timestamp ODBC*; fractions de seconde partie des secondes est différente de zéro [b]<br /><br /> Valeur de données n’est pas valide *littéral d’heure ODBC* ou *littéral de l’horodatage ODBC*|n/a<br /><br /> n/a<br /><br /> 22008<br /><br /> 22018|  
|SQL_TYPE_TIMESTAMP|Valeur de données est valide *littéral de timestamp ODBC*; fractions de seconde partie secondes ne pas tronqué<br /><br /> Valeur de données est valide *littéral de timestamp ODBC*; fractions de seconde partie secondes tronqué<br /><br /> Valeur de données est valide *littéral de date ODBC*[c]<br /><br /> Valeur de données est valide *littéral d’heure ODBC*[d]<br /><br /> Valeur de données n’est pas valide *littéral de date ODBC*, *littéral d’heure ODBC*, ou *littéral de l’horodatage ODBC*|n/a<br /><br /> 22008<br /><br /> n/a<br /><br /> n/a<br /><br /> 22018|  
|Tous les types d’intervalle SQL|Valeur de données est valide *valeur d’intervalle*; n’est pas tronqué<br /><br /> Valeur de données est valide *valeur d’intervalle*; la valeur dans un des champs est tronquée<br /><br /> La valeur de données n’est pas un littéral d’intervalle valide|n/a<br /><br /> 22015<br /><br /> 22018|  
  
 [a] la partie heure de l’horodatage est tronquée.  
  
 [b] la partie date de l’horodatage est ignorée.  
  
 [c] la partie heure de l’horodatage est définie à zéro.  
  
 [d] la partie date de l’horodatage est définie à la date actuelle.  
  
 [e] la source de données/pilote efficacement attend la chaîne entière a été reçue (même si les données de caractère sont envoyées en plusieurs parties par des appels à **SQLPutData**) avant de tenter d’effectuer la conversion.  
  
 Lorsque les données de caractères C soient converti en numérique, date, heure ou timestamp de données SQL, de début et les espaces à droite sont ignorés.  
  
 Quand les données de caractères C sont converties en données binaires de SQL, chaque deux octets de données caractères sont converties en un seul octet (8 bits) de données binaires. Chaque deux octets de données caractère représente un nombre au format hexadécimal. Par exemple, « 01 » est convertie en un binaire 00000001 et « FF » est converti en un 11111111 binaire.  
  
 Le pilote convertit les paires de chiffres hexadécimaux en octets individuels toujours et ignore l’octet de caractère nul de terminaison. Pour cette raison, si la longueur de la chaîne de caractères est impaire, le dernier octet de la chaîne (à l’exclusion de l’octet de caractère nul de terminaison, le cas échéant) n’est pas converti.  
  
> [!NOTE]  
>  Les développeurs d’applications sont déconseillés à partir de la liaison de données de caractères C à un type de données SQL binaire. Cette conversion est généralement inefficace et lente.

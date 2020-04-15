---
title: 'C à SQL: Caractère Microsoft Docs'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: acde0d2a79492607185d56d3082797c79a100fa2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292030"
---
# <a name="c-to-sql-character"></a>C en SQL : Caractère
Les identifiants du type de données ODBC C sont les plus identitaires du type de données ODBC C :  
  
 SQL_C_CHAR  
  
 SQL_C_WCHAR  
  
 Le tableau suivant montre les types de données SQL ODBC auxquels les données de caractère C peuvent être converties. Pour une explication des colonnes et des termes dans le tableau, voir [convertir les données de C à SQL Data Types](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
> [!NOTE]  
>  Lorsque les données du caractère C sont converties en données Unicode SQL, la durée des données Unicode doit être un nombre pair.  
  
|Identifiant de type SQL|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Longueur d’aute des données <la longueur de la colonne.<br /><br /> Longueur d’aute des données > longueur de colonne.|n/a<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Longueur de caractère des données <la longueur de la colonne.<br /><br /> Longueur de caractère des données > longueur de colonne.|n/a<br /><br /> 22001|  
|SQL_DECIMAL<br /><br /> SQL_NUMERIC<br /><br /> SQL_TINYINT<br /><br /> SQL_SMALLINT<br /><br /> SQL_INTEGER SQL_BIGINT|Données converties sans troncation<br /><br /> Données converties avec troncation de chiffres fractionnels[e]<br /><br /> La conversion des données entraînerait une perte de chiffres entiers (par opposition à fractionnels)<br /><br /> La valeur des données *n’est* pas une|n/a<br /><br /> 22001<br /><br /> 22001<br /><br /> 22018|  
|SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE|Les données se situent dans la plage du type de données auquel le nombre est converti<br /><br /> Les données sont en dehors de la plage du type de données à laquelle le nombre est converti<br /><br /> La valeur des données *n’est* pas une|n/a<br /><br /> 22003<br /><br /> 22018|  
|SQL_BIT|Les données sont de 0 ou 1<br /><br /> Les données sont supérieures à 0, moins de 2, et n’égalent pas 1<br /><br /> Les données sont inférieures à 0 ou plus ou égales à 2<br /><br /> Les données ne sont pas *un*|n/a<br /><br /> 22001<br /><br /> 22003<br /><br /> 22018|  
|SQL_BINARY<br /><br /> SQL_VARBINARY<br /><br /> SQL_LONGVARBINARY|(Longueur de byte de données) / 2 <- longueur d’byte de colonne<br /><br /> (Longueur de byte de données) / 2 > longueur d’ente de colonne<br /><br /> La valeur des données n’est pas une valeur hexadecimal|n/a<br /><br /> 22001<br /><br /> 22018|  
|SQL_TYPE_DATE|La valeur des données est une valeur valide *ODBC-date-littérale*<br /><br /> La valeur des données est une *valeur valide ODBC-timestamp-littérale*; la portion de temps est nulle<br /><br /> La valeur des données est une *valeur valide ODBC-timestamp-littérale*; partie de temps est nonzero[a]<br /><br /> La valeur des données n’est pas une valeur valide *ODBC-date-littérale* ou *ODBC-timestamp-littéral*|n/a<br /><br /> n/a<br /><br /> 22008<br /><br /> 22018|  
|SQL_TYPE_TIME|La valeur des *ODBC-time-literal* données est une<br /><br /> La valeur des données est une *valeur valide ODBC-timestamp-littérale*; fractionnement de la partie secondes est zéro[b]<br /><br /> La valeur des données est une *valeur valide ODBC-timestamp-littérale*; fractionnement de la partie secondes est nonzero[b]<br /><br /> La valeur des données n’est pas une valeur valide *ODBC-temps-littérale* ou *ODBC-timestamp-littérale*|n/a<br /><br /> n/a<br /><br /> 22008<br /><br /> 22018|  
|SQL_TYPE_TIMESTAMP|La valeur des données est une *valeur valide ODBC-timestamp-littérale*; fractionnement de la partie secondes non tronquée<br /><br /> La valeur des données est une *valeur valide ODBC-timestamp-littérale*; fractionnement de la partie secondes tronquée<br /><br /> La valeur des données est une valeur de *données valide ODBC-date-littérale*[c]<br /><br /> La valeur des données est une *valeur valide ODBC-temps-littérale*[d]<br /><br /> La valeur des données n’est pas une *valeur valide ODBC-date-littérale*, *ODBC-time-littérale*, ou *ODBC-timestamp-littérale*|n/a<br /><br /> 22008<br /><br /> n/a<br /><br /> n/a<br /><br /> 22018|  
|Tous les types d’intervalle SQL|La valeur des données est une *valeur d’intervalle*valide ; aucune troncation ne se produit<br /><br /> La valeur des données est une *valeur d’intervalle*valide ; la valeur dans l’un des champs est tronquée<br /><br /> La valeur de données n’est pas un intervalle valide littéral|n/a<br /><br /> 22015<br /><br /> 22018|  
  
 [a] La partie temporelle de l’humidité du temps est tronquée.  
  
 [b] La partie date de l’humidité du temps est ignorée.  
  
 [c] La partie temporelle de l’humidité du temps est réglée à zéro.  
  
 [d] La partie date de l’humidité du temps est fixée à la date actuelle.  
  
 [e] Le conducteur/source de données attend effectivement que toute la chaîne ait été reçue (même si les données de caractère sont envoyées en morceaux par des appels à **SQLPutData**) avant de tenter d’effectuer la conversion.  
  
 Lorsque les données du caractère C sont converties en données SQL numériques, date, heure ou timetamp, les blancs de tête et de fuite sont ignorés.  
  
 Lorsque les données du caractère C sont converties en données SQL binaires, chacun des deux octets de données de caractère sont convertis en un seul octet (8 bits) de données binaires. Chacun des deux octets de données de caractère représentent un nombre sous forme hexadecimal. Par exemple, "01" est converti en un binaire 00000001 et "FF" est converti en un binaire 111111111.  
  
 Le conducteur convertit toujours des paires de chiffres hexadecimal en octets individuels et ignore le octet de non-terminaison. Pour cette raison, si la longueur de la chaîne de caractère est étrange, le dernier byte de la chaîne (à l’exclusion du byte de terminaison nulle, le cas échéant) n’est pas converti.  
  
> [!NOTE]  
>  Les développeurs d’applications sont découragés de lier les données de caractère C à un type de données SQL binaire. Cette conversion est généralement inefficace et lente.

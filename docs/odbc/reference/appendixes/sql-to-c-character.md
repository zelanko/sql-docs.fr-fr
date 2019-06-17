---
title: 'SQL à C : Caractère | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], character
- character data type [ODBC]
- data conversions from SQL to C types [ODBC], character
ms.assetid: 7fdb7f38-b64d-48f2-bcb4-1ca96b2bbdb6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e3a0a7036d67716a3d90bd8953a3c7ba2c575c92
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63259514"
---
# <a name="sql-to-c-character"></a>SQL à C : Caractère

Les identificateurs pour les types de données de caractères SQL ODBC sont les suivantes :

- SQL_CHAR
- SQL_VARCHAR
- SQL_LONGVARCHAR
- SQL_WCHAR
- SQL_WVARCHAR
- SQL_WLONGVARCHAR

Le tableau suivant présente les types de données à laquelle les données de caractères SQL peuvent être converties à la C ODBC. Pour obtenir une explication des colonnes et des termes dans la table, consultez [conversion des données à partir de SQL pour les Types de données C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  

|Identificateur de type C|Test|TargetValuePtr|StrLen_or_IndPtr|SQLSTATE|
|:----------------|:---|:-------------|:---------------|:-------|
|SQL_C_CHAR|Longueur d’octet de données < *BufferLength*<br /><br /> Longueur d’octet de données > = *BufferLength*|Données<br /><br /> Données tronquées|Longueur des données en octets<br /><br /> Longueur des données en octets|n/a<br /><br /> 01004|  
|SQL_C_WCHAR|Longueur des données de caractères < *BufferLength*<br /><br /> Longueur des données de caractères > = *BufferLength*|Données<br /><br /> Données tronquées|Longueur des données en caractères<br /><br /> Longueur des données en caractères|n/a<br /><br /> 01004|  
|SQL_C_STINYINT SQL_C_UTINYINT SQL_C_TINYINT SQL_C_SBIGINT SQL_C_UBIGINT SQL_C_SSHORT SQL_C_USHORT SQL_C_SHORT SQL_C_SLONG SQL_C_ULONG SQL_C_LONG SQL_C_NUMERIC|Les données converties sans troncation [b]<br /><br /> Les données converties avec troncation de chiffres fractionnaires [a]<br /><br /> Conversion de données entraînerait une perte de chiffres dans son ensemble (par opposition aux fractions de seconde) [a]<br /><br /> Données ne sont pas un *littéral numérique*[b].|Données<br /><br /> Données tronquées<br /><br /> Indéfini<br /><br /> Indéfini|Nombre d’octets du type de données C<br /><br /> Nombre d’octets du type de données C<br /><br /> Indéfini<br /><br /> Indéfini|n/a<br /><br /> 01S07<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_FLOAT SQL_C_DOUBLE|Les données sont dans la plage du type de données à laquelle le nombre est converti [a]<br /><br /> Données sont en dehors de la plage du type de données à laquelle le nombre est converti [a]<br /><br /> Données ne sont pas un *littéral numérique*[b].|Données<br /><br /> Indéfini<br /><br /> Indéfini|Taille du type de données C<br /><br /> Indéfini<br /><br /> Indéfini|n/a<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_BIT|Les données sont 0 ou 1<br /><br /> Données sont supérieures à 0, inférieure à 2 et non égal à 1<br /><br /> Données sont inférieur à 0 ou supérieur ou égal à 2<br /><br /> Données ne sont pas un *littéral numérique*|Données<br /><br /> Données tronquées<br /><br /> Indéfini<br /><br /> Indéfini|1[b]<br /><br /> 1[b]<br /><br /> Indéfini<br /><br /> Indéfini|n/a<br /><br /> 01S07<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_BINARY|Longueur d’octet de données < = *BufferLength*<br /><br /> Longueur d’octet de données > *BufferLength*|Données<br /><br /> Données tronquées|Longueur des données en octets<br /><br /> Longueur des données|n/a<br /><br /> 01004|  
|SQL_C_TYPE_DATE|Valeur de données est valide *valeur de date*[a]<br /><br /> Valeur de données est valide *valeur d’horodatage*; partie heure correspond à zéro [a]<br /><br /> Valeur de données est valide *valeur d’horodatage*; partie heure est différent de zéro [a], [c]<br /><br /> Valeur de données n’est pas valide *valeur de date* ou *valeur d’horodatage*[a]|Données<br /><br /> Données<br /><br /> Données tronquées<br /><br /> Indéfini|6[b]<br /><br /> 6[b]<br /><br /> 6[b]<br /><br /> Indéfini|n/a<br /><br /> n/a<br /><br /> 01S07<br /><br /> 22018|  
|SQL_C_TYPE_TIME|Valeur de données est valide *valeur d’heure et la valeur est 0 fraction de seconde*[a]<br /><br /> Valeur de données est valide *valeur d’horodatage ou une valeur d’heure valide*; fractions de seconde partie des secondes est égal à zéro [a], [d]<br /><br /> Valeur de données est valide *valeur d’horodatage*; fractions de seconde partie des secondes est différent de zéro [a], [d], [e]<br /><br /> Valeur de données n’est pas valide *valeur d’heure* ou *valeur d’horodatage*[a]|Données<br /><br /> Données<br /><br /> Données tronquées<br /><br /> Indéfini|6[b]<br /><br /> 6[b]<br /><br /> 6[b]<br /><br /> Indéfini|n/a<br /><br /> n/a<br /><br /> 01S07<br /><br /> 22018|  
|SQL_C_TYPE_TIMESTAMP|Valeur de données est valide *valeur d’horodatage ou une valeur d’heure valide*; fractions de seconde partie secondes ne pas tronqué [a]<br /><br /> Valeur de données est valide *valeur d’horodatage ou une valeur d’heure valide*; fractions de seconde partie secondes tronqué [a]<br /><br /> Valeur de données est valide *valeur de date*[a]<br /><br /> Valeur de données est valide *valeur d’heure*[a]<br /><br /> Valeur de données n’est pas valide *valeur de date*, *valeur d’heure*, ou *valeur d’horodatage*[a]|Données<br /><br /> Données tronquées<br /><br /> Données [f]<br /><br /> Données [g]<br /><br /> Indéfini|16[b]<br /><br /> 16[b]<br /><br /> 16[b]<br /><br /> 16[b]<br /><br /> Indéfini|n/a<br /><br /> 01S07<br /><br /> n/a<br /><br /> n/a<br /><br /> 22018|  
|Tous les types d’intervalle C|Valeur de données est valide *valeur d’intervalle*; aucune troncature<br /><br /> Valeur de données est valide *valeur d’intervalle*; troncation d’un ou plusieurs champs à droite<br /><br /> Les données sont intervalle valide ; précision significatif du champ d’en-tête est perdu<br /><br /> La valeur de données n’est pas une valeur d’intervalle valide|Données<br /><br /> Données tronquées<br /><br /> Indéfini<br /><br /> Indéfini|Longueur des données en octets<br /><br /> Longueur des données en octets<br /><br /> Indéfini<br /><br /> Indéfini|n/a<br /><br /> 01S07<br /><br /> 22015<br /><br /> 22018|  
|&nbsp;|&nbsp;|&nbsp;|&nbsp;|&nbsp;|

 [a] la valeur de *BufferLength* est ignorée pour cette conversion. Le pilote part du principe que la taille de **TargetValuePtr* est la taille du type de données C.  
  
 [b] Il s’agit de la taille du type de données C correspondant.  
  
 [c] la partie heure de la *valeur d’horodatage* est tronqué.  
  
 [d] la partie date de la *valeur d’horodatage* est ignoré.  
  
 [e] la partie fractions de secondes de l’horodatage est tronquée.  
  
 [f] les champs d’heure de la structure d’horodatage sont définies à zéro.  
  
 [g] les champs de date de la structure d’horodatage sont définies à la date actuelle.  

**Espaces supplémentaires**

Espaces à gauche et sont ignorés lorsque les données de caractères SQL sont converties à l’un des types suivants :

- date
- numeric
- time
- TIMESTAMP
- données d’intervalle C

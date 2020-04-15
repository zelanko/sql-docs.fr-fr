---
title: 'SQL à C: Caractère Microsoft Docs'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3486c0fcf5cefc39c4b85af814d7d3c1d609b4e3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296669"
---
# <a name="sql-to-c-character"></a>SQL à C : Caractère

Les identifiants pour les types de données ODBC SQL sont les suivants :

- SQL_CHAR
- SQL_VARCHAR
- SQL_LONGVARCHAR
- SQL_WCHAR
- SQL_WVARCHAR
- SQL_WLONGVARCHAR

Le tableau suivant montre les types de données ODBC C auxquels les données SQL peuvent être converties. Pour une explication des colonnes et des termes dans le tableau, voir [convertir les données de SQL à C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  

|Identifiant de type C|Test|TargetValuePtr (en)|StrLen_or_IndPtr|SQLSTATE|
|:----------------|:---|:-------------|:---------------|:-------|
|SQL_C_CHAR|Longueur d’enseille des données < *BufferLength*<br /><br /> Longueur d’enseille des données >*'BufferLength'*|Données<br /><br /> Données tronquées|Longueur des données dans les octets<br /><br /> Longueur des données dans les octets|n/a<br /><br /> 01004|  
|SQL_C_WCHAR|Longueur de caractère des données < *BufferLength*<br /><br /> Longueur de caractère des données >' *BufferLength*|Données<br /><br /> Données tronquées|Longueur des données en caractères<br /><br /> Longueur des données en caractères|n/a<br /><br /> 01004|  
|SQL_C_STINYINT SQL_C_UTINYINT SQL_C_TINYINT SQL_C_SBIGINT SQL_C_UBIGINT SQL_C_SSHORT SQL_C_USHORT SQL_C_SHORT SQL_C_SLONG SQL_C_ULONG SQL_C_LONG SQL_C_NUMERIC|Données converties sans troncation[b]<br /><br /> Données converties avec troncation de chiffres fractionnels[a]<br /><br /> La conversion des données entraînerait une perte de chiffres entiers (par opposition à fractionnels)<br /><br /> Les données ne sont pas un *[b] numérique-littéral*|Données<br /><br /> Données tronquées<br /><br /> Indéfini<br /><br /> Indéfini|Nombre d’octets du type de données C<br /><br /> Nombre d’octets du type de données C<br /><br /> Indéfini<br /><br /> Indéfini|n/a<br /><br /> 01S07<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_FLOAT SQL_C_DOUBLE|Les données se situent dans la plage du type de données auquel le nombre est converti[a]<br /><br /> Les données ne sont pas à la portée du type de données auquel le nombre est converti[a]<br /><br /> Les données ne sont pas un *[b] numérique-littéral*|Données<br /><br /> Indéfini<br /><br /> Indéfini|Taille du type de données C<br /><br /> Indéfini<br /><br /> Indéfini|n/a<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_BIT|Les données sont de 0 ou 1<br /><br /> Les données sont supérieures à 0, moins de 2, et n’égalent pas 1<br /><br /> Les données sont inférieures à 0 ou plus ou égales à 2<br /><br /> Les données ne sont pas *un*|Données<br /><br /> Données tronquées<br /><br /> Indéfini<br /><br /> Indéfini|1[b]<br /><br /> 1[b]<br /><br /> Indéfini<br /><br /> Indéfini|n/a<br /><br /> 01S07<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_BINARY|Longueur d’enseille des données <*'BufferLength'*<br /><br /> Longueur d’enseille des données > *BufferLength*|Données<br /><br /> Données tronquées|Longueur des données dans les octets<br /><br /> Longueur des données|n/a<br /><br /> 01004|  
|SQL_C_TYPE_DATE|La valeur des données est une *date-valeur*valide [a]<br /><br /> La valeur des données est une *valeur chronoluminale*valide ; la partie de temps est zéro[a]<br /><br /> La valeur des données est une *valeur chronoluminale*valide ; partie de temps est nonzero[a],[c]<br /><br /> La valeur des données n’est pas une *valeur de date* valide ou une valeur de *timestamp*[a]|Données<br /><br /> Données<br /><br /> Données tronquées<br /><br /> Indéfini|6[b]<br /><br /> 6[b]<br /><br /> 6[b]<br /><br /> Indéfini|n/a<br /><br /> n/a<br /><br /> 01S07<br /><br /> 22018|  
|SQL_C_TYPE_TIME|La valeur des données est une valeur temporelle valide *et la valeur fractionnelle des secondes est de 0*[a]<br /><br /> La valeur des données est une valeur temporelle valide *ou une valeur temporelle valide;* fractionnement de la partie secondes est zéro [a],[d]<br /><br /> La valeur des données est une *valeur chronoluminale*valide ; fractionnement de la partie secondes est nonzero[a],[d],[e]<br /><br /> La valeur des données n’est pas une *valeur temporelle* valide ou une *valeur temporelle*[a]|Données<br /><br /> Données<br /><br /> Données tronquées<br /><br /> Indéfini|6[b]<br /><br /> 6[b]<br /><br /> 6[b]<br /><br /> Indéfini|n/a<br /><br /> n/a<br /><br /> 01S07<br /><br /> 22018|  
|SQL_C_TYPE_TIMESTAMP|La valeur des données est une valeur temporelle valide *ou une valeur temporelle valide;* fractionnement de la partie secondes non tronquée[a]<br /><br /> La valeur des données est une valeur temporelle valide *ou une valeur temporelle valide;* fractionnement de la partie secondes tronquée[a]<br /><br /> La valeur des données est une *date-valeur*valide [a]<br /><br /> La valeur des données est une *valeur temporelle*valide [a]<br /><br /> La valeur des données n’est pas une *valeur de date*valide, une valeur *temporelle*ou une *valeur temporelle*[a]|Données<br /><br /> Données tronquées<br /><br /> Données[f]<br /><br /> Données[g]<br /><br /> Indéfini|16[b]<br /><br /> 16[b]<br /><br /> 16[b]<br /><br /> 16[b]<br /><br /> Indéfini|n/a<br /><br /> 01S07<br /><br /> n/a<br /><br /> n/a<br /><br /> 22018|  
|Tous les types d’intervalle C|La valeur des données est une *valeur d’intervalle*valide ; pas de troncation<br /><br /> La valeur des données est une *valeur d’intervalle*valide ; troncation d’un ou plusieurs champs de fuite<br /><br /> Les données sont des intervalles valides; champ de premier plan une précision significative est perdue<br /><br /> La valeur de données n’est pas une valeur d’intervalle valide|Données<br /><br /> Données tronquées<br /><br /> Indéfini<br /><br /> Indéfini|Longueur des données dans les octets<br /><br /> Longueur des données dans les octets<br /><br /> Indéfini<br /><br /> Indéfini|n/a<br /><br /> 01S07<br /><br /> 22015<br /><br /> 22018|  
|&nbsp;|&nbsp;|&nbsp;|&nbsp;|&nbsp;|

 [a] La valeur de *BufferLength* est ignorée pour cette conversion. Le conducteur suppose que la taille de*TargetValuePtr* est la taille du type de données C.  
  
 [b] C’est la taille du type de données C correspondant.  
  
 [c] La partie temporelle de la *valeur temporelle* est tronquée.  
  
 [d] La partie date de la *valeur de timestamp* est ignorée.  
  
 [e] La partie fractionnelle des secondes de l’humidité du temps est tronquée.  
  
 [f] Les champs de temps de la structure de timetamp sont réglés à zéro.  
  
 [g] Les champs de date de la structure de l’arrêt de l’époque sont fixés à la date actuelle.  

**Espaces supplémentaires**

Les espaces de tête et de fuite sont ignorés lorsque les données de caractère SQL sont converties en l’un des types suivants :

- Date
- numeric
- time
- timestamp
- données d’intervalle C

---
title: C pour les exemples de Conversion de données SQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], examples
- data conversions from C to SQL types [ODBC], examples
ms.assetid: 9f390afc-d8b8-4286-b559-98b3b8781f3d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 40cd9973bfdce68b1ccbe63edd8c875519dbd22b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63201594"
---
# <a name="c-to-sql-data-conversion-examples"></a>Exemples de conversion de données C en SQL
Les exemples suivants illustrent la façon dont le pilote convertit les données de C de données SQL :  
  
|Identificateur de type C|Valeur de données C|Type SQL<br /><br /> identificateur|colonne<br /><br /> length|Données SQL<br /><br /> valeur|SQLSTATE|  
|-----------------------|------------------|-----------------------------|-----------------------|------------------------|--------------|  
|SQL_C_CHAR|abcdef\0[a]|SQL_CHAR|6|abcdef|n/a|  
|SQL_C_CHAR|abcdef\0[a]|SQL_CHAR|5|abcde|22001|  
|SQL_C_CHAR|1234.56\0[a]|SQL_DECIMAL|8[b]|1234.56|n/a|  
|SQL_C_CHAR|1234.56\0[a]|SQL_DECIMAL|7[b]|1234.5|22001|  
|SQL_C_CHAR|1234.56\0[a]|SQL_DECIMAL|4|----|22003|  
|SQL_C_FLOAT|1234.56|SQL_FLOAT|n/a|1234.56|n/a|  
|SQL_C_FLOAT|1234.56|SQL_INTEGER|n/a|1234|22001|  
|SQL_C_FLOAT|1234.56|SQL_TINYINT|n/a|----|22003|  
|SQL_C_TYPE_DATE|1992,12,31[c]|SQL_CHAR|10|1992-12-31|n/a|  
|SQL_C_TYPE_DATE|1992,12,31[c]|SQL_CHAR|9|----|22003|  
|SQL_C_TYPE_DATE|1992,12,31[c]|SQL_TIMESTAMP|n/a|1992-12-31 00:00:00.0|n/a|  
|SQL_C_TYPE_TIMESTAMP|1992,12,31, 23,45,55, 120000000[d]|SQL_CHAR|22|1992-12-31 23:45:55.12|n/a|  
|SQL_C_TYPE_TIMESTAMP|1992,12,31, 23,45,55, 120000000[d]|SQL_CHAR|21|1992-12-31 23:45:55.1|22001|  
|SQL_C_TYPE_TIMESTAMP|1992,12,31, 23,45,55, 120000000[d]|SQL_CHAR|18|----|22003|  
  
 [a] « \0 » représente un octet de caractère nul de terminaison. L’octet de caractère nul de terminaison est requis uniquement si la longueur des données est SQL_NTS.  
  
 [b] en plus d’octets pour les nombres, un seul octet est requis pour une connexion et un autre octets est nécessaire pour la virgule décimale.  
  
 [c] les nombres dans cette liste sont les nombres stockés dans les champs de la structure SQL_DATE_STRUCT.  
  
 [d] les nombres dans cette liste sont les nombres stockés dans les champs de la structure SQL_TIMESTAMP_STRUCT.

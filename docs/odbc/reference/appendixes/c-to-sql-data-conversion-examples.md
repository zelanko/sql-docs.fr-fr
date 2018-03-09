---
title: "C pour les exemples de Conversion de données SQL | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- converting data from c to SQL types [ODBC], examples
- data conversions from C to SQL types [ODBC], examples
ms.assetid: 9f390afc-d8b8-4286-b559-98b3b8781f3d
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7d3270b142cb857876a558122b670bb329e08c93
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="c-to-sql-data-conversion-examples"></a>C pour les exemples de Conversion de données SQL
Les exemples suivants illustrent comment le pilote convertit les données C de données SQL :  
  
|Identificateur de type C|Valeur de données C|Type SQL<br /><br /> identificateur|colonne<br /><br /> length|Données SQL<br /><br /> valeur|SQLSTATE|  
|-----------------------|------------------|-----------------------------|-----------------------|------------------------|--------------|  
|SQL_C_CHAR|abcdef\0 [a]|SQL_CHAR|6|abcdef|n/a|  
|SQL_C_CHAR|abcdef\0 [a]|SQL_CHAR|5|abcde|22001|  
|SQL_C_CHAR|1234.56\0 [a]|SQL_DECIMAL|8 [b]|1234.56|n/a|  
|SQL_C_CHAR|1234.56\0 [a]|SQL_DECIMAL|7 [b]|1234.5|22001|  
|SQL_C_CHAR|1234.56\0 [a]|SQL_DECIMAL|4|----|22003|  
|SQL_C_FLOAT|1234.56|SQL_FLOAT|n/a|1234.56|n/a|  
|SQL_C_FLOAT|1234.56|SQL_INTEGER|n/a|1234|22001|  
|SQL_C_FLOAT|1234.56|SQL_TINYINT|n/a|----|22003|  
|SQL_C_TYPE_DATE|1992,12,31 (c)|SQL_CHAR|10|1992-12-31|n/a|  
|SQL_C_TYPE_DATE|1992,12,31 (c)|SQL_CHAR|9|----|22003|  
|SQL_C_TYPE_DATE|1992,12,31 (c)|SQL_TIMESTAMP|n/a|1992-12-31 00:00:00.0|n/a|  
|SQL_C_TYPE_TIMESTAMP|1992,12,31, 23,45,55, 120000000 [d]|SQL_CHAR|22|1992-12-31 23:45:55.12|n/a|  
|SQL_C_TYPE_TIMESTAMP|1992,12,31, 23,45,55, 120000000 [d]|SQL_CHAR|21|1992-12-31 23:45:55.1|22001|  
|SQL_C_TYPE_TIMESTAMP|1992,12,31, 23,45,55, 120000000 [d]|SQL_CHAR|18|----|22003|  
  
 [a] « \0 » représente un octet de valeur null. L’octet de fin de null est obligatoire uniquement si la longueur des données est SQL_NTS.  
  
 [b] en plus des octets pour les nombres, un seul octet est requis pour une connexion et un autre octets est requise pour la virgule décimale.  
  
 [c] les nombres dans cette liste sont les nombres stockés dans les champs de la structure SQL_DATE_STRUCT.  
  
 [d] les numéros de cette liste sont les nombres stockés dans les champs de la structure SQL_TIMESTAMP_STRUCT.

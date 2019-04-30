---
title: 'SQL à C : Binary | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to c types [ODBC], binary
- binary data type [ODBC]
- data conversions from SQL to C types [ODBC], binary
- binary data transfers [ODBC]
ms.assetid: 8c519072-ae4c-4d32-9d4e-775e3d3d6389
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 16112ca3b66e0218efd54d3bf385e04cb654e3e4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63270959"
---
# <a name="sql-to-c-binary"></a>SQL à C : Binaire
Les identificateurs pour les types de données ODBC SQL binaires sont :  
  
 SQL_BINARY  
  
 SQL_VARBINARY  
  
 SQL_LONGVARBINARY  
  
 Le tableau suivant présente les types de données à laquelle les données binaires de SQL peuvent être converties à la C ODBC. Pour obtenir une explication des colonnes et des termes dans la table, consultez [conversion des données à partir de SQL pour les Types de données C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Identificateur de type C|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|(Longueur d’octet de données) \* 2 < *BufferLength*<br /><br /> (Longueur d’octet de données) \* 2 > = *BufferLength*|Données<br /><br /> Données tronquées|Longueur des données en octets<br /><br /> Longueur des données en octets|n/a<br /><br /> 01004|  
|SQL_C_WCHAR|(Caractère de longueur de données) \* 2 < *BufferLength*<br /><br /> (Caractère de longueur de données) \* 2 > = *BufferLength*|Données<br /><br /> Données tronquées|Longueur des données en caractères<br /><br /> Longueur des données en caractères|n/a<br /><br /> 01004|  
|SQL_C_BINARY|Longueur d’octet de données < = *BufferLength*<br /><br /> Longueur d’octet de données > *BufferLength*|Données<br /><br /> Données tronquées|Longueur des données en octets<br /><br /> Longueur des données en octets|n/a<br /><br /> 01004|  
  
 Lorsque les données SQL binaire sont converti en données caractères C, chaque octet (8 bits) de la source de données est représenté comme deux caractères ASCII. Ces caractères sont la représentation sous forme de caractère ASCII du nombre figurant dans sa forme hexadécimale. Par exemple, un 00000001 binaire est converti en « 01 » et un 11111111 binaire est converti en « FF ».  
  
 Le pilote convertit chaque octet des paires de chiffres hexadécimaux toujours et met fin à la chaîne de caractères avec un octet null. Pour cette raison, si *BufferLength* pair et est inférieure à la longueur des données converties, le dernier octet de la **TargetValuePtr* mémoire tampon n’est pas utilisée. (Les données converties nécessitent un nombre pair d’octets, l’octet suivant la dernière est un octet null et le dernier octet ne peut pas être utilisé.)  
  
> [!NOTE]  
>  Les développeurs d’applications sont déconseillés à partir de la liaison de données SQL binaire en un type de données caractère C. Cette conversion est généralement inefficace et lente.

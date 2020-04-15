---
title: 'SQL à C: Binaire Microsoft Docs'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 70b0ce72f650e61b83ec99b0727752612d18da52
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298821"
---
# <a name="sql-to-c-binary"></a>SQL à C : Binary
Les identifiants pour les types binaires de données ODBC SQL sont les :  
  
 SQL_BINARY  
  
 SQL_VARBINARY  
  
 SQL_LONGVARBINARY  
  
 Le tableau suivant montre les types de données ODBC C auxquels les données SQL binaires peuvent être converties. Pour une explication des colonnes et des termes dans le tableau, voir [convertir les données de SQL à C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Identifiant de type C|Test|**TargetValuePtr (en)*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|(Durée des données) \* 2 < *BufferLength*<br /><br /> (Durée des données) \* 2 >*-BufferLength*|Données<br /><br /> Données tronquées|Longueur des données dans les octets<br /><br /> Longueur des données dans les octets|n/a<br /><br /> 01004|  
|SQL_C_WCHAR|(Longueur de caractère des données) \* 2 < *BufferLength*<br /><br /> (Longueur de caractère des données) \* 2 >*-BufferLength*|Données<br /><br /> Données tronquées|Longueur des données en caractères<br /><br /> Longueur des données en caractères|n/a<br /><br /> 01004|  
|SQL_C_BINARY|Longueur d’enseille des données <*'BufferLength'*<br /><br /> Longueur d’enseille des données > *BufferLength*|Données<br /><br /> Données tronquées|Longueur des données dans les octets<br /><br /> Longueur des données dans les octets|n/a<br /><br /> 01004|  
  
 Lorsque les données SQL binaires sont converties en données de caractère C, chaque byte (8 bits) de données sources est représenté comme deux caractères ASCII. Ces personnages sont la représentation de caractère ASCII du nombre dans sa forme hexadecimal. Par exemple, un binaire 00000001 est converti en "01" et un binaire 1111111111 est converti en "FF".  
  
 Le conducteur convertit toujours les octets individuels en paires de chiffres hexadecimal et met fin à la chaîne de caractère avec un octet nul. Pour cette raison, si *BufferLength* est égal et est inférieur à la longueur des données converties, le dernier byte du tampon*TargetValuePtr* n’est pas utilisé. (Les données converties nécessitent un nombre égal d’octets, le octet suivant-dernier est un octet nul, et le dernier octet ne peut pas être utilisé.)  
  
> [!NOTE]  
>  Les développeurs d’applications sont découragés de lier les données SQL binaires à un type de données de caractère C. Cette conversion est généralement inefficace et lente.

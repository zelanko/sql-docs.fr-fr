---
title: 'SQL à C: Date Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], date
- date data type [ODBC]
- data conversions from SQL to C types [ODBC], date
ms.assetid: 703c7960-9cf4-4d7a-9920-53b29c184f97
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fe9656c0c02c0ff5a10029525da3d38280530cc3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296529"
---
# <a name="sql-to-c-date"></a>SQL à C : Date
L’identifiant pour la date ODBC SQL type de données est:  
  
 SQL_TYPE_DATE  
  
 Le tableau suivant montre les types de données ODBC C à quelle date les données SQL peuvent être converties. Pour une explication des colonnes et des termes dans le tableau, voir [convertir les données de SQL à C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Identifiant de type C|Test|**TargetValuePtr (en)*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > Caractère byte longueur<br /><br /> 11 <' *BufferLength* <' Longueur de byte de caractère<br /><br /> *BufferLength* < 11|Données<br /><br /> Données tronquées<br /><br /> Indéfini|10<br /><br /> Longueur des données dans les octets<br /><br /> Indéfini|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > Longueur de caractère<br /><br /> 11 <' *BufferLength* <' Longueur de caractère<br /><br /> *BufferLength* < 11|Données<br /><br /> Données tronquées<br /><br /> Indéfini|10<br /><br /> Longueur des données en caractères<br /><br /> Indéfini|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Longueur d’enseille des données <*'BufferLength'*<br /><br /> Longueur d’enseille des données > *BufferLength*|Données<br /><br /> Indéfini|Longueur des données dans les octets<br /><br /> Indéfini|n/a<br /><br /> 22003|  
|SQL_C_TYPE_DATE|Aucun[a]|Données|6[c]|n/a|  
|SQL_C_TYPE_TIMESTAMP|Aucun[a]|Données[b]|16[c]|n/a|  
  
 [a] La valeur de *BufferLength* est ignorée pour cette conversion. Le conducteur suppose que la taille de*TargetValuePtr* est la taille du type de données C.  
  
 [b] Les champs de temps de la structure de timetamp sont réglés à zéro.  
  
 [c] C’est la taille du type de données C correspondant.  
  
 Lorsque les données SQL date sont converties en données de caractère C, la chaîne résultante est dans le format "*yyy*-*mm*-*dd*" format. Ce format n’est pas affecté par le paramètre de pays Windows®.

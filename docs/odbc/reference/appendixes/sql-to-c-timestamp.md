---
title: 'SQL à C: Timestamp (fr) Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- timestamp data type [ODBC]
- converting data from SQL to C types [ODBC], timestamp
- data conversions from SQL to C types [ODBC], timestamp
ms.assetid: 6a0617cf-d8c0-4316-8bb4-e6ddb45d7bf1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 552bab585e4480fd922c9b9a6b112830f5c11ad9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296349"
---
# <a name="sql-to-c-timestamp"></a>SQL à C : Timestamp

L’identifiant pour le type de données ODBC SQL est le suivant :

- SQL_TYPE_TIMESTAMP  

Le tableau suivant montre les types de données ODBC C auxquels les données SQL peuvent être converties. Pour une explication des colonnes et des termes dans le tableau, voir [convertir les données de SQL à C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  

|Identifiant de type C|Test|**TargetValuePtr (en)*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > Caractère byte longueur<br /><br /> 20 <' *BufferLength* <' Longueur de byte de caractère<br /><br /> *BufferLength* < 20|Données<br /><br /> Données tronquées[b]<br /><br /> Indéfini|Longueur des données dans les octets<br /><br /> Longueur des données dans les octets<br /><br /> Indéfini|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > Longueur de caractère<br /><br /> 20 <' *BufferLength* <' Longueur de caractère<br /><br /> *BufferLength* < 20|Données<br /><br /> Données tronquées[b]<br /><br /> Indéfini|Longueur des données en caractères<br /><br /> Longueur des données en caractères<br /><br /> Indéfini|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Longueur d’enseille des données <*'BufferLength'*<br /><br /> Longueur d’enseille des données > *BufferLength*|Données<br /><br /> Indéfini|Longueur des données dans les octets<br /><br /> Indéfini|n/a<br /><br /> 22003|  
|SQL_C_TYPE_DATE|La portion temporelle de timetamp est zéro[a]<br /><br /> La partie temporelle de timetamp n’est paszero[a]|Données<br /><br /> Données tronquées[c]|6[f]<br /><br /> 6[f]|n/a<br /><br /> 01S07|  
|SQL_C_TYPE_TIME|Fractionnelle partie de timestamp est zéro[a]<br /><br /> Fractionnelle secondes partie de timestamp est nonzero[a]|Données[d]<br /><br /> Données tronquées[d], [e]|6[f]<br /><br /> 6[f]|n/a<br /><br /> 01S07|  
|SQL_C_TYPE_TIMESTAMP|Fractionnelle partie de timestamp n’est pas tronqué[a]<br /><br /> Fractionnelle partie de timestamp est tronqué[a]|Données[e]<br /><br /> Données tronquées[e]|16[f]<br /><br /> 16[f]|n/a<br /><br /> 01S07|  

 [a] La valeur de *BufferLength* est ignorée pour cette conversion. Le conducteur suppose que la taille de*TargetValuePtr* est la taille du type de données C.  
  
 [b] Les fractions de secondes de l’humidité du temps sont tronquées.  
  
 [c] La partie temporelle de l’humidité du temps est tronquée.  
  
 [d] La partie date de l’humidité du temps est ignorée.  
  
 [e] La partie fractionnelle des secondes de l’humidité du temps est tronquée.  
  
 [f] C’est la taille du type de données C correspondant.  

Lorsque les données SQL de timestamp sont converties en données de caractère C, la chaîne résultante est dans le "*yyyy*-*mm*-*dd* *hh*:*mm*:*ss*[.* f...*]" format, où jusqu’à neuf chiffres peuvent être utilisés pendant des secondes fractionnées. Ce format n’est pas affecté par le paramètre de pays Windows®. (À l’exception du point décimal et des fractions de secondes, l’ensemble du format doit être utilisé, quelle que soit la précision du type de données SQL de l’horloge.)

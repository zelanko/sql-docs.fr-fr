---
title: 'SQL à C: Temps Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], time
- time data type [ODBC]
- data conversions from SQL to C types [ODBC], time
ms.assetid: 6dc59973-7bb5-40f1-87c8-5bf68b3bf2ee
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ebd146abf650861099a40bf91b2641df768b343d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296379"
---
# <a name="sql-to-c-time"></a>SQL à C : Temps
L’identifiant pour le moment ODBC SQL type de données est:  
  
 SQL_TYPE_TIME  
  
 Le tableau suivant montre les types de données ODBC C auxquels les données SQL peuvent être converties. Pour une explication des colonnes et des termes dans le tableau, voir [convertir les données de SQL à C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Identifiant de type C|Test|**TargetValuePtr (en)*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > Caractère byte longueur<br /><br /> *9* <= *BufferLength* <- Longueur de caractère byte<br /><br /> *BufferLength* < 9|Données<br /><br /> Données tronquées[a]<br /><br /> Indéfini|Longueur des données dans les octets<br /><br /> Longueur des données dans les octets<br /><br /> Indéfini|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > Longueur de caractère<br /><br /> *9* <= *BufferLength* <- Longueur de caractère<br /><br /> *BufferLength* < 9|Données<br /><br /> Données tronquées[a]<br /><br /> Indéfini|Longueur des données en caractères<br /><br /> Longueur des données en caractères<br /><br /> Indéfini|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Longueur d’enseille des données <*'BufferLength'*<br /><br /> Longueur d’enseille des données > *BufferLength*|Données<br /><br /> Indéfini|Longueur des données dans les octets<br /><br /> Indéfini|n/a<br /><br /> 22003|  
|SQL_C_TYPE_TIME|Aucun[b]|Données|6[d]|n/a|  
|SQL_C_TYPE_TIMESTAMP|Aucun[b]|Données[c]|16[d]|n/a|  
  
 [a] Les fractions de secondes du temps sont tronquées.  
  
 [b] La valeur de *BufferLength* est ignorée pour cette conversion. Le conducteur suppose que la taille de*TargetValuePtr* est la taille du type de données C.  
  
 [c] Les champs de date de la structure de l’arrêt de l’époque sont fixés à la date actuelle, et le champ fractionnel des secondes de la structure de l’humidité du temps est réglé à zéro.  
  
 [d] C’est la taille du type de données C correspondant.  
  
 Lorsque les données SQL de temps sont converties en données de caractère C, la chaîne qui en résulte est dans le format «*hh*:*mm*:*ss*». Ce format n’est pas affecté par le paramètre de pays Windows®.

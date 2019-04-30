---
title: 'SQL à C : Time | Microsoft Docs'
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e028502bd7bc6ac1a81006d340b6ce606a0ae337
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63259603"
---
# <a name="sql-to-c-time"></a>SQL à C : Time
L’identificateur de l’heure est de type de données ODBC SQL :  
  
 SQL_TYPE_TIME  
  
 Le tableau suivant présente les types de données à laquelle les données SQL de temps peuvent être converties à la C ODBC. Pour obtenir une explication des colonnes et des termes dans la table, consultez [conversion des données à partir de SQL pour les Types de données C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Identificateur de type C|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > longueur d’octet de caractère<br /><br /> *9* <= *BufferLength* < = longueur d’octet de caractère<br /><br /> *BufferLength* < 9|Données<br /><br /> Données tronquées [a]<br /><br /> Indéfini|Longueur des données en octets<br /><br /> Longueur des données en octets<br /><br /> Indéfini|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > longueur des caractères<br /><br /> *9* <= *BufferLength* < = longueur de caractère<br /><br /> *BufferLength* < 9|Données<br /><br /> Données tronquées [a]<br /><br /> Indéfini|Longueur des données en caractères<br /><br /> Longueur des données en caractères<br /><br /> Indéfini|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Longueur d’octet de données < = *BufferLength*<br /><br /> Longueur d’octet de données > *BufferLength*|Données<br /><br /> Indéfini|Longueur des données en octets<br /><br /> Indéfini|n/a<br /><br /> 22003|  
|SQL_C_TYPE_TIME|Aucun [b]|Données|6[d]|n/a|  
|SQL_C_TYPE_TIMESTAMP|Aucun [b]|Données [c]|16[d]|n/a|  
  
 [a] les fractions de secondes du temps sont tronqués.  
  
 [b] la valeur de *BufferLength* est ignorée pour cette conversion. Le pilote part du principe que la taille de **TargetValuePtr* est la taille du type de données C.  
  
 [c] les champs de date de la structure d’horodatage sont définies à la date actuelle, et le champ en fractions de seconde de la structure de l’horodatage est défini à zéro.  
  
 [d] Il s’agit de la taille du type de données C correspondant.  
  
 Lorsque les données SQL de temps sont converti en données caractères C, la chaîne résultante est dans le «*hh*:*mm*:*ss*« format. Ce format n’est pas affecté par le paramètre de pays Windows®.

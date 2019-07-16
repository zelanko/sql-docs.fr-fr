---
title: 'SQL à C : Date | Microsoft Docs'
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d282798a31ac9059ed3c1901ea01f1f3104f09c7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68056879"
---
# <a name="sql-to-c-date"></a>SQL à C : Date
L’identificateur pour le type de données de date ODBC SQL est :  
  
 SQL_TYPE_DATE  
  
 Le tableau suivant présente le ODBC C types de données à laquelle la date de données SQL peut-être être convertie. Pour obtenir une explication des colonnes et des termes dans la table, consultez [conversion des données à partir de SQL pour les Types de données C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Identificateur de type C|Tester|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > longueur d’octet de caractère<br /><br /> 11 < = *BufferLength* < = longueur d’octet de caractère<br /><br /> *BufferLength* < 11|Données<br /><br /> Données tronquées<br /><br /> Indéfini|10<br /><br /> Longueur des données en octets<br /><br /> Indéfini|N/A<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > longueur des caractères<br /><br /> 11 < = *BufferLength* < = longueur de caractère<br /><br /> *BufferLength* < 11|Données<br /><br /> Données tronquées<br /><br /> Indéfini|10<br /><br /> Longueur des données en caractères<br /><br /> Indéfini|N/A<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Longueur d’octet de données < = *BufferLength*<br /><br /> Longueur d’octet de données > *BufferLength*|Données<br /><br /> Indéfini|Longueur des données en octets<br /><br /> Indéfini|N/A<br /><br /> 22003|  
|SQL_C_TYPE_DATE|Aucun [a]|Données|6[c]|N/A|  
|SQL_C_TYPE_TIMESTAMP|Aucun [a]|Données [b]|16[c]|N/A|  
  
 [a] la valeur de *BufferLength* est ignorée pour cette conversion. Le pilote part du principe que la taille de **TargetValuePtr* est la taille du type de données C.  
  
 [b] les champs d’heure de la structure d’horodatage sont définies à zéro.  
  
 [c] Il s’agit de la taille du type de données C correspondant.  
  
 Lors de la date de données SQL est converti en données caractères C, la chaîne résultante est dans le «*aaaa*-*mm*-*jj*« format. Ce format n’est pas affecté par le paramètre de pays Windows®.

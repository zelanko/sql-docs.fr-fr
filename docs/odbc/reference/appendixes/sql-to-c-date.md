---
title: 'SQL en C : date | Microsoft Docs'
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81296529"
---
# <a name="sql-to-c-date"></a>SQL à C : Date
L’identificateur pour la date type de données SQL ODBC est le suivant :  
  
 SQL_TYPE_DATE  
  
 Le tableau suivant répertorie les types de données ODBC C dans lesquels les données SQL peuvent être converties. Pour obtenir une explication des colonnes et des termes du tableau, consultez [conversion de données SQL en types de données C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Identificateur de type C|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > la longueur en octets du caractère<br /><br /> 11 <= *BufferLength* <= longueur d’octet de caractère<br /><br /> *BufferLength* < 11|Données<br /><br /> Données tronquées<br /><br /> Indéfini|10<br /><br /> Longueur des données en octets<br /><br /> Indéfini|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > longueur de caractère<br /><br /> 11 <= *BufferLength* <= longueur de caractère<br /><br /> *BufferLength* < 11|Données<br /><br /> Données tronquées<br /><br /> Indéfini|10<br /><br /> Longueur des données en caractères<br /><br /> Indéfini|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Longueur en octets des données <= *BufferLength*<br /><br /> Longueur en octets des données > *BufferLength*|Données<br /><br /> Indéfini|Longueur des données en octets<br /><br /> Indéfini|n/a<br /><br /> 22003|  
|SQL_C_TYPE_DATE|Aucun [a]|Données|6 [c]|n/a|  
|SQL_C_TYPE_TIMESTAMP|Aucun [a]|Données [b]|16 [c]|n/a|  
  
 [a] la valeur de *BufferLength* est ignorée pour cette conversion. Le pilote suppose que la taille de **TargetValuePtr* est la taille du type de données C.  
  
 [b] les champs d’heure de la structure d’horodatage sont définis sur zéro.  
  
 [c] il s’agit de la taille du type de données C correspondant.  
  
 Lorsque les données SQL de date sont converties en données de type C, la chaîne résultante est au format «*yyyy*-*mm*-*JJ*». Ce format n’est pas affecté par le paramètre pays® Windows.

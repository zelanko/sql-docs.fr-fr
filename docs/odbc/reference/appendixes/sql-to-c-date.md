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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d282798a31ac9059ed3c1901ea01f1f3104f09c7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68056879"
---
# <a name="sql-to-c-date"></a>SQL en C : date
L’identificateur pour la date type de données SQL ODBC est le suivant :  
  
 SQL_TYPE_DATE  
  
 Le tableau suivant répertorie les types de données ODBC C dans lesquels les données SQL peuvent être converties. Pour obtenir une explication des colonnes et des termes du tableau, consultez [conversion de données SQL en types de données C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Identificateur de type C|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > la longueur en octets du caractère<br /><br /> 11 <= *BufferLength* <= longueur d’octet de caractère<br /><br /> *BufferLength* < 11|Données<br /><br /> Données tronquées<br /><br /> Non défini(e)|10<br /><br /> Longueur des données en octets<br /><br /> Non défini(e)|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > longueur de caractère<br /><br /> 11 <= *BufferLength* <= longueur de caractère<br /><br /> *BufferLength* < 11|Données<br /><br /> Données tronquées<br /><br /> Non défini(e)|10<br /><br /> Longueur des données en caractères<br /><br /> Non défini(e)|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Longueur en octets des données <= *BufferLength*<br /><br /> Longueur en octets des données > *BufferLength*|Données<br /><br /> Non défini(e)|Longueur des données en octets<br /><br /> Non défini(e)|n/a<br /><br /> 22003|  
|SQL_C_TYPE_DATE|Aucun [a]|Données|6 [c]|n/a|  
|SQL_C_TYPE_TIMESTAMP|Aucun [a]|Données [b]|16 [c]|n/a|  
  
 [a] la valeur de *BufferLength* est ignorée pour cette conversion. Le pilote suppose que la taille de **TargetValuePtr* est la taille du type de données C.  
  
 [b] les champs d’heure de la structure d’horodatage sont définis sur zéro.  
  
 [c] il s’agit de la taille du type de données C correspondant.  
  
 Lorsque les données SQL de date sont converties en données de type C, la chaîne résultante est au format «*yyyy*-*mm*-*JJ*». Ce format n’est pas affecté par le paramètre pays® Windows.

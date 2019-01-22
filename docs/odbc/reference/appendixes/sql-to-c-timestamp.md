---
title: 'SQL pour c : Timestamp | Microsoft Docs'
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 69c9f1258f35a69d6554783f5d1b4ca79be313d2
ms.sourcegitcommit: 480961f14405dc0b096aa8009855dc5a2964f177
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2019
ms.locfileid: "54419954"
---
# <a name="sql-to-c-timestamp"></a>SQL pour c : Horodateur

L’identificateur pour le type de données SQL ODBC timestamp est la suivante :

- SQL_TYPE_TIMESTAMP  

Le tableau suivant présente les types de données à laquelle les données timestamp SQL peuvent être converties à C ODBC. Pour obtenir une explication des colonnes et des termes dans la table, consultez [conversion des données à partir de SQL pour les Types de données C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  

|Identificateur de type C|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > longueur d’octet de caractère<br /><br /> 20 < = *BufferLength* < = longueur d’octet de caractère<br /><br /> *BufferLength* < 20|Données<br /><br /> Données tronquées [b]<br /><br /> Indéfini|Longueur des données en octets<br /><br /> Longueur des données en octets<br /><br /> Indéfini|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > longueur des caractères<br /><br /> 20 < = *BufferLength* < = longueur de caractère<br /><br /> *BufferLength* < 20|Données<br /><br /> Données tronquées [b]<br /><br /> Indéfini|Longueur des données en caractères<br /><br /> Longueur des données en caractères<br /><br /> Indéfini|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Longueur d’octet de données < = *BufferLength*<br /><br /> Longueur d’octet de données > *BufferLength*|Données<br /><br /> Indéfini|Longueur des données en octets<br /><br /> Indéfini|n/a<br /><br /> 22003|  
|SQL_C_TYPE_DATE|Partie heure d’horodatage est égale à zéro [a]<br /><br /> Partie heure d’horodatage est différente de zéro [a]|Données<br /><br /> Données tronquées [c]|6[f]<br /><br /> 6[f]|n/a<br /><br /> 01S07|  
|SQL_C_TYPE_TIME|Partie fractions de secondes de l’horodatage est égale à zéro [a]<br /><br /> Portion de fractions de timestamp est différente de zéro [a]|Données [d]<br /><br /> Données tronquées [d], [e]|6[f]<br /><br /> 6[f]|n/a<br /><br /> 01S07|  
|SQL_C_TYPE_TIMESTAMP|Partie des fractions d’horodatage n’est pas tronqué [a]<br /><br /> Portion de fractions de timestamp est tronquée [a]|Données [e]<br /><br /> Données tronquées [e]|16[f]<br /><br /> 16[f]|n/a<br /><br /> 01S07|  

 [a] la valeur de *BufferLength* est ignorée pour cette conversion. Le pilote part du principe que la taille de **TargetValuePtr* est la taille du type de données C.  
  
 [b] les fractions de secondes de l’horodatage sont tronqués.  
  
 [c] la partie heure de l’horodatage est tronquée.  
  
 [d] la partie date de l’horodatage est ignorée.  
  
 [e] la partie fractions de secondes de l’horodatage est tronquée.  
  
 [f] Il s’agit de la taille du type de données C correspondant.  

Lorsque les données SQL timestamp sont converti en données caractères C, la chaîne résultante est dans le «*aaaa*-*mm*-*jj* *hh* :*mm*:*ss*[.*f...*] « format, où jusqu'à neuf chiffres peut être utilisé pour les fractions. Ce format n’est pas affecté par le paramètre de pays Windows®. (À l’exception de la virgule décimale et les fractions de secondes, tout le format doit être utilisé, quel que soit la précision du type de données timestamp SQL.)

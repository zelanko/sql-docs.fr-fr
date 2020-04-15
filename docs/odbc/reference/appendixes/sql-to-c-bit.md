---
title: 'SQL à C: Bit Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to c types [ODBC], bit
- bit data type [ODBC]
- data conversions from SQL to C types [ODBC], bit
ms.assetid: 0eeaab8b-ad82-4a36-b464-9a1211d5f72c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 57688f34c504b221f77c1b66792bf9ee9398df27
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296749"
---
# <a name="sql-to-c-bit"></a>SQL à C : bit
L’identifiant pour le type de données ODBC SQL bit est :  
  
 SQL_BIT  
  
 Le tableau suivant montre les types de données ODBC C auxquels les données SQL peuvent être converties. Pour une explication des colonnes et des termes dans le tableau, voir [convertir les données de SQL à C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Identifiant de type C|Test|**TargetValuePtr (en)*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR<br /><br /> SQL_C_WCHAR|*BufferLength* > 1<br /><br /> *BufferLength* <1|Données<br /><br /> Indéfini|1<br /><br /> Indéfini|n/a<br /><br /> 22003|  
|SQL_C_STINYINT<br /><br /> SQL_C_UTINYINT<br /><br /> SQL_C_TINYINT<br /><br /> SQL_C_SBIGINT<br /><br /> SQL_C_UBIGINT<br /><br /> SQL_C_SSHORT<br /><br /> SQL_C_USHORT<br /><br /> SQL_C_SHORT<br /><br /> SQL_C_SLONG<br /><br /> SQL_C_ULONG<br /><br /> SQL_C_LONG<br /><br /> SQL_C_FLOAT<br /><br /> SQL_C_DOUBLE<br /><br /> SQL_C_NUMERIC|Aucun[a]|Données|Taille du type de données C|n/a|  
|SQL_C_BIT|Aucun[a]|Données|1[b]|n/a|  
|SQL_C_BINARY|*BufferLength* >1<br /><br /> *BufferLength* < 1|Données<br /><br /> Indéfini|1<br /><br /> Indéfini|n/a<br /><br /> 22003|  
  
 [a] La valeur de *BufferLength* est ignorée pour cette conversion. Le conducteur suppose que la taille de*TargetValuePtr* est la taille du type de données C.  
  
 [b] C’est la taille du type de données C correspondant.  
  
 Lorsque les données SQL bit est convertie en données de caractère C, les valeurs possibles sont "0" et "1".

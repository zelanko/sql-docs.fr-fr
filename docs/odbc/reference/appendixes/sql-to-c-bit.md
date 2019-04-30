---
title: 'SQL à C : Bit | Microsoft Docs'
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f7ff0bd2988460596623eb47ded276392dc3d443
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63270980"
---
# <a name="sql-to-c-bit"></a>SQL à C : bit
L’identificateur pour le type de données bit SQL ODBC est :  
  
 SQL_BIT  
  
 Le tableau suivant présente le ODBC C types de données à laquelle le bit de données SQL peuvent être converties. Pour obtenir une explication des colonnes et des termes dans la table, consultez [conversion des données à partir de SQL pour les Types de données C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Identificateur de type C|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR<br /><br /> SQL_C_WCHAR|*BufferLength* > 1<br /><br /> *BufferLength* <= 1|Données<br /><br /> Indéfini|1<br /><br /> Indéfini|n/a<br /><br /> 22003|  
|SQL_C_STINYINT<br /><br /> SQL_C_UTINYINT<br /><br /> SQL_C_TINYINT<br /><br /> SQL_C_SBIGINT<br /><br /> SQL_C_UBIGINT<br /><br /> SQL_C_SSHORT<br /><br /> SQL_C_USHORT<br /><br /> SQL_C_SHORT<br /><br /> SQL_C_SLONG<br /><br /> SQL_C_ULONG<br /><br /> SQL_C_LONG<br /><br /> SQL_C_FLOAT<br /><br /> SQL_C_DOUBLE<br /><br /> SQL_C_NUMERIC|Aucun [a]|Données|Taille du type de données C|n/a|  
|SQL_C_BIT|Aucun [a]|Données|1[b]|n/a|  
|SQL_C_BINARY|*BufferLength* >= 1<br /><br /> *BufferLength* < 1|Données<br /><br /> Indéfini|1<br /><br /> Indéfini|n/a<br /><br /> 22003|  
  
 [a] la valeur de *BufferLength* est ignorée pour cette conversion. Le pilote part du principe que la taille de **TargetValuePtr* est la taille du type de données C.  
  
 [b] Il s’agit de la taille du type de données C correspondant.  
  
 Lorsque des données SQL de bits sont converti en données caractères C, les valeurs possibles sont « 0 » et « 1 ».

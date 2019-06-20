---
title: 'SQL à C : GUID | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], GUID
- data conversions from SQL to C types [ODBC], guid
- GUID data type [ODBC]
ms.assetid: cf56c684-c261-4b89-994a-db14ab2241d6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 21054bdb3f869a0f06349b32e481144b3582de4e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63258814"
---
# <a name="sql-to-c-guid"></a>SQL à C : GUID
L’identificateur pour le type de données GUID ODBC SQL est :  
  
 SQL_GUID  
  
 Le tableau suivant présente les types de données à laquelle les données de GUID SQL peuvent être converties à la C ODBC. Pour obtenir une explication des colonnes et des termes dans la table, consultez [conversion des données à partir de SQL pour les Types de données C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Identificateur de type C|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > longueur d’octet de caractère|Données|36|n/a|  
||*BufferLength* < 37|Indéfini|Indéfini|22003|  
|SQL_C_WCHAR|*BufferLength* > longueur des caractères|Données|36|n/a|  
||*BufferLength* < 37|Indéfini|Indéfini|22003|  
|SQL_C_BINARY|Longueur d’octet de données \< =  *BufferLength*|Données|Longueur des données en octets|n/a|  
||Longueur d’octet de données > *BufferLength*|Indéfini|Indéfini|22003|  
|SQL_C_GUID|Aucun [a]|Données|16[b]|n/a|  
  
 [a] la valeur de *BufferLength* est ignorée pour cette conversion. Le pilote part du principe que la taille de **TargetValuePtr* est la taille du type de données C.  
  
 [b] Il s’agit de la taille du type de données C correspondant.

---
title: Jeu de résultats de SQLGetTypeInfo exemple | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL data types [ODBC], examples
- SQLGetTypeInfo function [ODBC], examples
- data types [ODBC], SQL data types
ms.assetid: dc1952cc-7581-4d69-9c72-7dc1cd370836
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 028b9be01439b122ff164aed68adb40eb1b4a46e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47662613"
---
# <a name="example-sqlgettypeinfo-result-set"></a>Exemple de jeu de résultats de SQLGetTypeInfo
Une application appelle **SQLGetTypeInfo** pour déterminer les types de données sont pris en charge par une source de données et les caractéristiques de ces types de données. Les tableaux suivants montrent un exemple de jeu de résultats retourné par **SQLGetTypeInfo** pour une source de données qui prend en charge SQL_CHAR, SQL_LONGVARCHAR, SQL_DECIMAL, SQL_REAL, SQL_DATETIME, SQL_INTERVAL_YEAR et SQL_INTERVAL_DAY_TO_SECOND.  
  
|TYPE_NAME|DATA_TYPE|COLUMN_SIZE|LITERAL_PREFIX|LITERAL_SUFFIX|CREATE_PARAMS|NULLABLE|  
|----------------|----------------|------------------|---------------------|---------------------|--------------------|--------------|  
|« char »|SQL_CHAR|255|"'"|"'"|« longueur »|SQL_TRUE|  
|"text"|SQL_LONGVARCHAR|2147483647|"'"|"'"|\<NULL >|SQL_TRUE|  
|« decimal »|SQL_DECIMAL|28|\<NULL >|\<NULL >|« precision,<br />mise à l’échelle »|SQL_TRUE|  
|« réelle »|SQL_REAL|7|\<NULL >|\<NULL >|\<NULL >|SQL_TRUE|  
|« datetime »|SQL_TYPE_TIMESTAMP|23|"'"|"'"|\<NULL >|SQL_TRUE|  
|« INTERVALLE YEAR() À L’ANNÉE »|SQL_INTERVAL_YEAR|9|"'"|"'"|« précision »|SQL_TRUE|  
|« INTERVALLE DAY() À FRACTION(5) »|SQL_INTERVAL_DAY_TO_SECOND|24|"'"|"'"|« précision »|SQL_TRUE|  
  
|DATA_TYPE|CASE_SENSITIVE|SEARCHABLE|UNSIGNED_ATTRIBUTE|FIXED_PREC_SCALE|AUTO_UNIQUE_VALUE|LOCAL_TYPE_NAME|  
|----------------|---------------------|----------------|-------------------------|------------------------|-------------------------|-----------------------|  
|**SQL_CHAR**|SQL_FALSE|SQL_SEARCHABLE|\<NULL >|SQL_FALSE|\<NULL >|« char »|  
|**SQL_LONGVARCHAR**|SQL_FALSE|SQL_PRED_CHAR|\<NULL >|SQL_FALSE|\<NULL >|"text"|  
|**SQL_DECIMAL**|SQL_FALSE|SQL_PRED_BASIC|SQL_FALSE|SQL_FALSE|SQL_FALSE|« decimal »|  
|**SQL_REAL**|SQL_FALSE|SQL_PRED_BASIC|SQL_FALSE|SQL_FALSE|SQL_FALSE|« réelle »|  
|**SQL_TYPE_TIMESTAMP**|SQL_FALSE|SQL_SEARCHABLE|\<NULL >|SQL_FALSE|\<NULL >|« datetime »|  
|**SQL_INTERVAL_YEAR**|SQL_FALSE|SQL_SEARCHABLE|\<NULL >|SQL_FALSE|\<NULL >|« INTERVALLE YEAR() À L’ANNÉE »|  
TERVAL_DAY_TO_SECOND **|SQL_FALSE|SQL_PRED_BASIC|\<NULL >|SQL_FALSE|\<NULL >|« INTERVALLE DAY() À FRACTION(5) »|  
  
|DATA_TYPE|MINIMUM_SCALE|MAXIMUM_SCALE|SQL_DATA_TYPE|SQL_DATETIME_SUB|NUM_PREC_RADIX|INTERVAL_PRECISION|  
|----------------|--------------------|--------------------|---------------------|------------------------|----------------------|-------------------------|  
|**SQL_CHAR**|\<NULL >|\<NULL >|SQL_CHAR|\<NULL >|\<NULL >|\<NULL >|  
|**SQL_LONGVARCHAR**|\<NULL >|\<NULL >|SQL_LONGVARCHAR|\<NULL >|\<NULL >|\<NULL >|  
|**SQL_DECIMAL**|0|28|SQL_DECIMAL|\<NULL >|10|\<NULL >|  
|**SQL_REAL**|\<NULL >|\<NULL >|SQL_REAL|\<NULL >|10|\<NULL >|  
|**SQL_TYPE_TIMESTAMP**|3|3|SQL_DATETIME|SQL_CODE_TIMESTAMP|\<NULL >|12|  
|**SQL_INTERVAL_YEAR**|0|0|SQL_INTERVAL|SQL_CODE_INTERVALYEAR|\<NULL >|9|  
ERVAL_DAY_TO_SECOND **|5|5|SQL_INTERVAL|SQL_CODE_INTERVALDAY_TO_SECOND|\<NULL >|9|

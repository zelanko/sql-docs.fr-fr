---
title: Exemple SQLGetTypeInfo Résultat Set (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a5cf62f8a95f4c91095c21a6d603317fe1f73500
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307010"
---
# <a name="example-sqlgettypeinfo-result-set"></a>Exemple de jeu de résultats de SQLGetTypeInfo
Une application appelle **SQLGetTypeInfo** pour déterminer quels types de données sont pris en charge par une source de données et les caractéristiques de ces types de données. Les tableaux suivants montrent un ensemble de résultats d’échantillon retourné par **SQLGetTypeInfo** pour une source de données qui prend en charge SQL_CHAR, SQL_LONGVARCHAR, SQL_DECIMAL, SQL_REAL, SQL_DATETIME, SQL_INTERVAL_YEAR et SQL_INTERVAL_DAY_TO_SECOND.  
  
|TYPE_NAME|DATA_TYPE|COLUMN_SIZE|LITERAL_PREFIX|LITERAL_SUFFIX|CREATE_PARAMS|NULLABLE|  
|----------------|----------------|------------------|---------------------|---------------------|--------------------|--------------|  
|"char"|SQL_CHAR|255|"'"|"'"|"longueur"|SQL_TRUE|  
|"text"|SQL_LONGVARCHAR|2147483647|"'"|"'"|\<Null>|SQL_TRUE|  
|"décimale"|SQL_DECIMAL|28|\<Null>|\<Null>|"précision,<br />échelle"|SQL_TRUE|  
|"réel"|SQL_REAL|7|\<Null>|\<Null>|\<Null>|SQL_TRUE|  
|"datetime"|SQL_TYPE_TIMESTAMP|23|"'"|"'"|\<Null>|SQL_TRUE|  
|"ANNÉE D’INTERVALLE() À L’ANNÉE"|SQL_INTERVAL_YEAR|9|"'"|"'"|"précision"|SQL_TRUE|  
|"JOUR D’INTERVALLE)) À FRACTION(5)"|SQL_INTERVAL_DAY_TO_SECOND|24|"'"|"'"|"précision"|SQL_TRUE|  
  
|DATA_TYPE|CASE_SENSITIVE|SEARCHABLE|UNSIGNED_ATTRIBUTE|FIXED_PREC_SCALE|AUTO_UNIQUE_VALUE|LOCAL_TYPE_NAME|  
|----------------|---------------------|----------------|-------------------------|------------------------|-------------------------|-----------------------|  
|**SQL_CHAR**|SQL_FALSE|SQL_SEARCHABLE|\<Null>|SQL_FALSE|\<Null>|"char"|  
|**SQL_LONGVARCHAR**|SQL_FALSE|SQL_PRED_CHAR|\<Null>|SQL_FALSE|\<Null>|"text"|  
|**SQL_DECIMAL**|SQL_FALSE|SQL_PRED_BASIC|SQL_FALSE|SQL_FALSE|SQL_FALSE|"décimale"|  
|**SQL_REAL**|SQL_FALSE|SQL_PRED_BASIC|SQL_FALSE|SQL_FALSE|SQL_FALSE|"réel"|  
|**SQL_TYPE_TIMESTAMP**|SQL_FALSE|SQL_SEARCHABLE|\<Null>|SQL_FALSE|\<Null>|"datetime"|  
|**SQL_INTERVAL_YEAR**|SQL_FALSE|SQL_SEARCHABLE|\<Null>|SQL_FALSE|\<Null>|"ANNÉE D’INTERVALLE() À L’ANNÉE"|  
|**SQL_INTERVAL_DAY_TO_SECOND**|SQL_FALSE|SQL_PRED_BASIC|\<Null>|SQL_FALSE|\<Null>|"JOUR D’INTERVALLE)) À FRACTION(5)"|  
  
|DATA_TYPE|MINIMUM_SCALE|MAXIMUM_SCALE|SQL_DATA_TYPE|SQL_DATETIME_SUB|NUM_PREC_RADIX|INTERVAL_PRECISION|  
|----------------|--------------------|--------------------|---------------------|------------------------|----------------------|-------------------------|  
|**SQL_CHAR**|\<Null>|\<Null>|SQL_CHAR|\<Null>|\<Null>|\<Null>|  
|**SQL_LONGVARCHAR**|\<Null>|\<Null>|SQL_LONGVARCHAR|\<Null>|\<Null>|\<Null>|  
|**SQL_DECIMAL**|0|28|SQL_DECIMAL|\<Null>|10|\<Null>|  
|**SQL_REAL**|\<Null>|\<Null>|SQL_REAL|\<Null>|10|\<Null>|  
|**SQL_TYPE_TIMESTAMP**|3|3|SQL_DATETIME|SQL_CODE_TIMESTAMP|\<Null>|12|  
|**SQL_INTERVAL_YEAR**|0|0|SQL_INTERVAL|SQL_CODE_INTERVALYEAR|\<Null>|9|  
|**SQL_INTERVAL_DAY_TO_SECOND**|5|5|SQL_INTERVAL|SQL_CODE_INTERVALDAY_TO_SECOND|\<Null>|9|

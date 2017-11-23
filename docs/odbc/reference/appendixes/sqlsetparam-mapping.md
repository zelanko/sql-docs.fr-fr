---
title: Mappage de SQLSetParam | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLSetParam
- SQLSetParam function [ODBC], mapping
ms.assetid: 022dfbc0-8d18-4c35-8a28-d9eb16063188
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 43f15984f487dec8e77fd429f823c083c6c08a5b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="sqlsetparam-mapping"></a>Mappage de SQLSetParam
**SQLSetParam** continue à être mappés sur des **SQLBindParameter** comme dans ODBC 2. *x*. Même s’il est conceptuellement semblable à **SQLBindParam**, le Gestionnaire de pilotes ne mappe pas **SQLSetParam** à **SQLBindParam**. C’est parce que certain existant ODBC 2. *x* pilotes utilisent la valeur spéciale *BufferLength* (SQL_SETPARAM_VALUE_MAX) que le Gestionnaire de pilotes génère lorsqu’il mappe **SQLSetParam** sur **SQLBindParameter** pour déterminer lorsqu’elle est appelée par un 1. *x* application ODBC.  
  
 Un appel à  
  
```  
SQLSetParam(hstmt, ipar, fCType, fSqlType, cbColDef, ibScale, rgbValue, pcbValue)  
```  
  
 provoque la commande suivante :  
  
```  
SQLBindParameter(StatementHandle, ParameterNumber, SQL_PARAM_INPUT_OUTPUT, ValueType, ParameterType, ColumnSize, DecimalDigits, ParameterValuePtr, SQL_SETPARAM_VALUE_MAX, StrLen_or_IndPtr)  
```

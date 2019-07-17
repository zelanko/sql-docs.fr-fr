---
title: SQLSetParam, mappage | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLSetParam
- SQLSetParam function [ODBC], mapping
ms.assetid: 022dfbc0-8d18-4c35-8a28-d9eb16063188
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6c8d2d567f899c30dfe91cd35445956cd6214da9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68125553"
---
# <a name="sqlsetparam-mapping"></a>SQLSetParam, mappage
**SQLSetParam** continue à être mappées sur des **SQLBindParameter** comme dans ODBC 2. *x*. Même s’il est conceptuellement semblable à **SQLBindParam**, le Gestionnaire de pilotes ne mappe pas **SQLSetParam** à **SQLBindParam**. Il s’agit, car certaine existant ODBC 2. *x* pilotes utilisent la valeur spéciale *BufferLength* (SQL_SETPARAM_VALUE_MAX) que le Gestionnaire de pilotes génère lorsqu’il est mappé **SQLSetParam** en haut de  **SQLBindParameter** pour déterminer quand elle est appelée par un 1. *x* application ODBC.  
  
 Un appel à  
  
```  
SQLSetParam(hstmt, ipar, fCType, fSqlType, cbColDef, ibScale, rgbValue, pcbValue)  
```  
  
 entraîne les éléments suivants :  
  
```  
SQLBindParameter(StatementHandle, ParameterNumber, SQL_PARAM_INPUT_OUTPUT, ValueType, ParameterType, ColumnSize, DecimalDigits, ParameterValuePtr, SQL_SETPARAM_VALUE_MAX, StrLen_or_IndPtr)  
```

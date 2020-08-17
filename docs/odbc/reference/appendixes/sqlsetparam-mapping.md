---
description: SQLSetParam, mappage
title: Mappage SQLSetParam, | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e2c16f942920b5fefff664cc647f4edfc9ab6d13
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339295"
---
# <a name="sqlsetparam-mapping"></a>SQLSetParam, mappage
**SQLSetParam,** continue à être mappé sur **SQLBINDPARAMETER** comme dans ODBC 2. *x*. Même s’il est similaire au concept de **SQLBindParam**, le gestionnaire de pilotes ne mappe pas **SQLSetParam,** à **SQLBindParam**. Cela est dû au fait que certains ODBC 2 existants. *x* les pilotes utilisent la valeur spéciale *BufferLength* (SQL_SETPARAM_VALUE_MAX) que le gestionnaire de pilotes génère lorsqu’il mappe **SQLSetParam,** sur **SQLBindParameter** pour déterminer quand il est appelé par un 1. *x* application ODBC.  
  
 Un appel à  
  
```  
SQLSetParam(hstmt, ipar, fCType, fSqlType, cbColDef, ibScale, rgbValue, pcbValue)  
```  
  
 se traduira par les éléments suivants :  
  
```  
SQLBindParameter(StatementHandle, ParameterNumber, SQL_PARAM_INPUT_OUTPUT, ValueType, ParameterType, ColumnSize, DecimalDigits, ParameterValuePtr, SQL_SETPARAM_VALUE_MAX, StrLen_or_IndPtr)  
```

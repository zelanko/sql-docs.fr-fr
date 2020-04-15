---
title: Cartographie SQLSetParam (fr) Microsoft Docs
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
ms.openlocfilehash: 4d8e632412965664e5cdd9c87dc1e26787dcdab2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300529"
---
# <a name="sqlsetparam-mapping"></a>SQLSetParam, mappage
**SQLSetParam** continue d’être cartographié au-dessus de **SQLBindParameter** comme dans ODBC 2. *x*. Même si elle est conceptuellement similaire à **SQLBindParam**, le gestionnaire de conducteur ne carte pas **SQLSetParam** à **SQLBindParam**. C’est parce que certains existants ODBC 2. *x* les conducteurs utilisent la valeur spéciale de *BufferLength* (SQL_SETPARAM_VALUE_MAX) que le gestionnaire de conducteur génère lorsqu’il cartographie **SQLSetParam** au-dessus de **SQLBindParameter** pour déterminer quand il est appelé par un 1. *x* application ODBC.  
  
 Un appel à  
  
```  
SQLSetParam(hstmt, ipar, fCType, fSqlType, cbColDef, ibScale, rgbValue, pcbValue)  
```  
  
 résultats dans les éléments suivants:  
  
```  
SQLBindParameter(StatementHandle, ParameterNumber, SQL_PARAM_INPUT_OUTPUT, ValueType, ParameterType, ColumnSize, DecimalDigits, ParameterValuePtr, SQL_SETPARAM_VALUE_MAX, StrLen_or_IndPtr)  
```

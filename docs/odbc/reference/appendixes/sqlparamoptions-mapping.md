---
title: Mappage SQLParamOptions, | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLParamOptions
- SQLParamOptions function [ODBC], mapping
ms.assetid: 57ed65f6-9620-4738-b331-19d2a2b5cae4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7f4fa71c06b4a9bf3b01d39fa02d4eadeb9b0778
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125718"
---
# <a name="sqlparamoptions-mapping"></a>SQLParamOptions, mappage
Quand une application appelle **SQLParamOptions,** via un pilote ODBC *3. x* , l’appel  
  
```  
SQLParamOptions(hstmt, crow, piRow);  
```  
  
 sera mappé à deux appels de **SQLSetStmtAttr** comme suit :  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMSET_SIZE, crow, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMS_PROCESSED_PTR, piRow, 0);  
```

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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3b083800b660b8ccd26da747e4caf745531188e5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300559"
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

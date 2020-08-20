---
description: SQLError, mappage
title: Mappage de SQLError | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLError
- SQLError function [ODBC], mapping
ms.assetid: 802ac711-7e5d-4152-9698-db0cafcf6047
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5d18d1b25acbbe56f29555274a7b8d995b7355d0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466021"
---
# <a name="sqlerror-mapping"></a>SQLError, mappage
Quand une application appelle **SQLError** par le biais d’un pilote ODBC *3. x* , l’appel à  
  
```  
SQLError(henv, hdbc, hstmt, szSqlState, pfNativeError, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)   
```  
  
 est mappé à  
  
```  
SQLGetDiagRec(HandleType, Handle, RecNumber, szSqlstate, pfNativeErrorPtr, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)  
```  
  
 avec l' *argument comme HandleType* défini sur la valeur SQL_HANDLE_ENV, SQL_HANDLE_DBC ou SQL_HANDLE_STMT, selon le cas, et l’argument *descripteur* défini sur la valeur dans *henv*, *hdbc*ou *HSTMT*, selon le cas. L’argument *recnumber* est déterminé par le gestionnaire de pilotes.

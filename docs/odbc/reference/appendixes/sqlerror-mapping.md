---
title: Mappage de SQLError | Documents Microsoft
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
- mapping deprecated functions [ODBC], SQLError
- SQLError function [ODBC], mapping
ms.assetid: 802ac711-7e5d-4152-9698-db0cafcf6047
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1c6cfbf06a9cbbbe635506bbe1e0191879defa1a
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="sqlerror-mapping"></a>Mappage de SQLError
Lorsqu’une application appelle **SQLError** via un ODBC 3*.x* pilote, l’appel à  
  
```  
SQLError(henv, hdbc, hstmt, szSqlState, pfNativeError, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)   
```  
  
 est mappée à  
  
```  
SQLGetDiagRec(HandleType, Handle, RecNumber, szSqlstate, pfNativeErrorPtr, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)  
```  
  
 avec la *HandleType* la valeur SQL_HANDLE_ENV, SQL_HANDLE_DBC ou SQL_HANDLE_STMT, selon le cas, l’argument et le *gérer* affectée à la valeur de l’argument *henv*, *pas*, ou *hstmt*, le cas échéant. Le *RecNumber* argument est déterminé par le Gestionnaire de pilotes.

---
title: Cartographie SQLError (fr) Microsoft Docs
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
ms.openlocfilehash: 1aa3b66b29af755099cb273f3a19ca4e8230cd0b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302073"
---
# <a name="sqlerror-mapping"></a>SQLError, mappage
Lorsqu’une demande appelle **SQLError** par l’intermédiaire d’un conducteur *ODBC 3.x,* l’appel à  
  
```  
SQLError(henv, hdbc, hstmt, szSqlState, pfNativeError, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)   
```  
  
 est cartographié pour  
  
```  
SQLGetDiagRec(HandleType, Handle, RecNumber, szSqlstate, pfNativeErrorPtr, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)  
```  
  
 avec *l’argument HandleType* réglé à la valeur SQL_HANDLE_ENV, SQL_HANDLE_DBC, ou SQL_HANDLE_STMT, le cas échéant, et *l’argument De poignée* réglé à la valeur dans *henv*, *hdbc*, ou *hstmt*, le cas échéant. *L’argument du RecNumber* est déterminé par le gestionnaire de conducteur.

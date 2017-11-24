---
title: "Instructions SQL saisies par l’utilisateur | Documents Microsoft"
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
- user-entered SQL statements [ODBC]
- SQL statements [ODBC], constructing
- SQL statements [ODBC], entered by user
ms.assetid: 109af162-93ba-425a-8fe5-49c7dc7cc784
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 91ae086fd7be4222c55a8fad9b8383846cc59949
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="sql-statements-entered-by-the-user"></a>Instructions SQL saisies par l’utilisateur
Les applications qui effectuent une analyse ad hoc couramment autorisent l’utilisateur à entrer des instructions SQL directement. Exemple :  
  
```  
SQLCHAR *     Statement, SqlState[6], Msg[SQL_MAX_MESSAGE_LENGTH];  
SQLSMALLINT   i, MsgLen;  
SQLINTEGER    NativeError;  
SQLRETURN     rc1, rc2;  
  
// Prompt user for SQL statement.  
GetSQLStatement(Statement);  
  
// Execute the statement directly. Because it will be executed only once,  
// do not prepare it.  
rc1 = SQLExecDirect(hstmt, Statement, SQL_NTS);  
  
// Process any errors or returned information.  
if ((rc1 == SQL_ERROR) || rc1 == SQL_SUCCESS_WITH_INFO) {  
   i = 1;  
   while ((rc2 = SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, i, SqlState, &NativeError,  
         Msg, sizeof(Msg), &MsgLen)) != SQL_NO_DATA) {  
      DisplayError(SqlState, NativeError, Msg, MsgLen);  
      i++;  
   }  
}  
```  
  
 Cette approche simplifie le codage de l’application ; l’application s’appuie sur l’utilisateur pour générer l’instruction SQL et sur la source de données pour vérifier la validité de l’instruction. Il est difficile d’écrire une interface utilisateur graphique qui expose de manière adéquate les complexités de SQL, simplement invite l’utilisateur à entrer le texte de l’instruction SQL peut-être ne pas être une alternative préférable. Toutefois, cela oblige l’utilisateur de savoir SQL, mais également le schéma de la source de données qui est interrogée. Certaines applications fournissent une interface utilisateur graphique à laquelle l’utilisateur peut créer une instruction SQL de base et également fournir une interface de texte avec lequel l’utilisateur peut modifier.

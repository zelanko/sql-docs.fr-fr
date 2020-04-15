---
title: Déclarations SQL saisies par l’utilisateur Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- user-entered SQL statements [ODBC]
- SQL statements [ODBC], constructing
- SQL statements [ODBC], entered by user
ms.assetid: 109af162-93ba-425a-8fe5-49c7dc7cc784
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bf2f8cf36be392cb42a970fa2fb0b19c35daeb39
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301960"
---
# <a name="sql-statements-entered-by-the-user"></a>Instructions SQL entrées par l’utilisateur
Les applications qui effectuent une analyse ad hoc permettent également généralement à l’utilisateur d’entrer directement les relevés SQL. Par exemple :  
  
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
  
 Cette approche simplifie le codage d’application ; l’application s’appuie sur l’utilisateur pour construire la déclaration SQL et sur la source de données pour vérifier la validité de l’instruction. Parce qu’il est difficile d’écrire une interface utilisateur graphique qui expose adéquatement les subtilités de SQL, il suffit de demander à l’utilisateur d’entrer le texte de déclaration SQL peut être une alternative préférable. Toutefois, cela exige de l’utilisateur qu’il sache non seulement SQL, mais aussi le schéma de la source de données interrogé. Certaines applications fournissent une interface utilisateur graphique par laquelle l’utilisateur peut créer une déclaration SQL de base et également fournir une interface texte avec laquelle l’utilisateur peut le modifier.

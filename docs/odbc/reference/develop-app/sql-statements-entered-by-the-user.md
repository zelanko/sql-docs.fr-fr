---
description: Instructions SQL entrées par l’utilisateur
title: Instructions SQL entrées par l’utilisateur | Microsoft Docs
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
ms.openlocfilehash: 6d7d7ee7ffc2a4c949173c3eee888e4c41b9e741
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424541"
---
# <a name="sql-statements-entered-by-the-user"></a>Instructions SQL entrées par l’utilisateur
Les applications qui effectuent une analyse ad hoc autorisent également généralement l’utilisateur à entrer des instructions SQL directement. Par exemple :  
  
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
  
 Cette approche simplifie le codage des applications. l’application s’appuie sur l’utilisateur pour créer l’instruction SQL et sur la source de données pour vérifier la validité de l’instruction. Étant donné qu’il est difficile d’écrire une interface utilisateur graphique qui expose correctement les subtilités de SQL, il est préférable de demander à l’utilisateur d’entrer le texte de l’instruction SQL comme alternative. Toutefois, l’utilisateur doit connaître non seulement SQL, mais également le schéma de la source de données interrogée. Certaines applications fournissent une interface utilisateur graphique qui permet à l’utilisateur de créer une instruction SQL de base et fournit également une interface de texte avec laquelle l’utilisateur peut la modifier.

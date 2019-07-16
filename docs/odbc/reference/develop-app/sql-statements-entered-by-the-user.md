---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 78a1653df60b21cde772cbe32a688b3fdef80a42
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086074"
---
# <a name="sql-statements-entered-by-the-user"></a>Instructions SQL entrées par l’utilisateur
Les applications qui effectuent des analyses ad hoc également couramment autoriser l’utilisateur à entrer des instructions SQL directement. Exemple :  
  
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
  
 Cette approche simplifie le codage de l’application ; l’application s’appuie sur l’utilisateur pour générer l’instruction SQL et sur la source de données pour vérifier la validité de l’instruction. Comme il est difficile d’écrire une interface utilisateur graphique qui expose de manière adéquate les subtilités de SQL, la simplement l’invitant à entrer le texte de l’instruction SQL peut être une alternative préférable. Toutefois, cela oblige l’utilisateur de connaître non seulement SQL, mais également le schéma de la source de données en cours d’interrogation. Certaines applications fournissent une interface utilisateur graphique par lequel l’utilisateur peut créer une instruction SQL de base et également fournir une interface de texte avec lequel l’utilisateur peut modifier.

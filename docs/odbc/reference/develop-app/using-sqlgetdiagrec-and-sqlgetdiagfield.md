---
description: Utilisation de SQLGetDiagRec et de SQLGetDiagField
title: Utilisation de SQLGetDiagRec et SQLGetDiagField | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], and SQLGetDiagRec
- SQLGetDiagRec function [ODBC], and SQLGetDiagField
- diagnostic information [ODBC], SqlGetDiagRec
- retrieving diagnostic information [ODBC]
ms.assetid: 4f486bb1-fad8-4064-ac9d-61f2de85b68b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 402cb326ac91e13db0d3ab5421bd5ddb097fb3db
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421433"
---
# <a name="using-sqlgetdiagrec-and-sqlgetdiagfield"></a>Utilisation de SQLGetDiagRec et de SQLGetDiagField
Les applications appellent **SQLGetDiagRec** ou **SQLGetDiagField** pour récupérer les informations de diagnostic. Ces fonctions acceptent un handle d’environnement, de connexion, d’instruction ou de descripteur et retournent des diagnostics à partir de la fonction qui a utilisé ce handle pour la dernière fois. Les diagnostics enregistrés sur un handle particulier sont ignorés lorsqu’une nouvelle fonction est appelée à l’aide de ce handle. Si la fonction a retourné plusieurs enregistrements de diagnostic, l’application appelle ces fonctions plusieurs fois. le nombre total d’enregistrements d’État est récupéré en appelant **SQLGetDiagField** pour l’enregistrement d’en-tête (enregistrement 0) avec l’option SQL_DIAG_NUMBER.  
  
 Les applications récupèrent les champs de diagnostics individuels en appelant **SQLGetDiagField** et en spécifiant le champ à récupérer. Certains champs de diagnostic n’ont aucune signification pour certains types de handles. Pour obtenir la liste des champs de diagnostic et leurs significations, consultez la description de la fonction [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) .  
  
 Les applications récupèrent le code d’erreur SQLSTATE, le code d’erreur natif et le message de diagnostic dans un appel unique en appelant **SQLGetDiagRec**. **SQLGetDiagRec** ne peut pas être utilisé pour récupérer des informations à partir de l’enregistrement d’en-tête.  
  
 Par exemple, le code suivant demande à l’utilisateur une instruction SQL et l’exécute. Si des informations de diagnostic ont été retournées, il appelle **SQLGetDiagField** pour connaître le nombre d’enregistrements d’État et de **SQLGetDiagRec** pour recevoir le code d’erreur SQLSTATE, le code d’erreur natif et le message de diagnostic à partir de ces enregistrements.  
  
```  
SQLCHAR       SqlState[6], SQLStmt[100], Msg[SQL_MAX_MESSAGE_LENGTH];  
SQLINTEGER    NativeError;  
SQLSMALLINT   i, MsgLen;  
SQLRETURN     rc1, rc2;  
SQLHSTMT      hstmt;  
  
// Prompt the user for an SQL statement.  
GetSQLStmt(SQLStmt);  
  
// Execute the SQL statement and return any errors or warnings.  
rc1 = SQLExecDirect(hstmt, SQLStmt, SQL_NTS);  
if ((rc1 == SQL_SUCCESS_WITH_INFO) || (rc1 == SQL_ERROR)) {
   SQLLEN numRecs = 0;
   SQLGetDiagField(SQL_HANDLE_STMT, hstmt, 0, SQL_DIAG_NUMBER, &numRecs, 0, 0);
   // Get the status records.
   i = 1;  
   while (i <= numRecs && (rc2 = SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, i, SqlState, &NativeError,  
            Msg, sizeof(Msg), &MsgLen)) != SQL_NO_DATA) {  
      DisplayError(SqlState,NativeError,Msg,MsgLen);  
      i++;  
   }  
}  
  
if ((rc1 == SQL_SUCCESS) || (rc1 == SQL_SUCCESS_WITH_INFO)) {  
   // Process statement results, if any.  
}  
```

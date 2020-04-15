---
title: Utilisation de SQLGetDiagRec et SQLGetDiagField (fr) Microsoft Docs
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
ms.openlocfilehash: 69a17086253b40469b0ed98cb6f870f319f03f52
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306750"
---
# <a name="using-sqlgetdiagrec-and-sqlgetdiagfield"></a>Utilisation de SQLGetDiagRec et de SQLGetDiagField
Les applications appellent **SQLGetDiagRec** ou **SQLGetDiagField** pour récupérer des informations diagnostiques. Ces fonctions acceptent un environnement, une connexion, une déclaration ou un diagnostic de retour de poignée et de retour de la fonction qui a utilisé cette poignée pour la dernière fois. Les diagnostics enregistrés sur une poignée particulière sont jetés lorsqu’une nouvelle fonction est appelée à l’aide de cette poignée. Si la fonction a retourné plusieurs dossiers diagnostiques, l’application appelle ces fonctions plusieurs fois; le nombre total d’enregistrements d’état est récupéré en appelant **SQLGetDiagField** pour le record d’en-tête (enregistrement 0) avec l’option SQL_DIAG_NUMBER.  
  
 Les applications récupèrent les champs de diagnostic individuels en appelant **SQLGetDiagField** et en spécifiant le champ à récupérer. Certains domaines de diagnostic n’ont aucun sens pour certains types de poignées. Pour une liste des champs de diagnostic et de leurs significations, consultez la description de la fonction [SQLGetDiagField.](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
 Les applications récupèrent le SQLSTATE, le code d’erreur natif et le message diagnostique en un seul appel en appelant **SQLGetDiagRec**; **SQLGetDiagRec** ne peut pas être utilisé pour récupérer les informations de l’enregistrement d’en-tête.  
  
 Par exemple, le code suivant invite l’utilisateur à obtenir une déclaration SQL et l’exécute. Si des renseignements diagnostiques ont été retournés, il appelle **SQLGetDiagField** pour obtenir le nombre de dossiers d’état et **SQLGetDiagRec** pour obtenir le SQLSTATE, le code d’erreur natif, et le message diagnostique de ces dossiers.  
  
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

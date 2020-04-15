---
title: Référence de l’ODBC API (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apitype: dllExport
ms.assetid: b7a49774-f458-44ce-9a04-a0457501405b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6065db0ea99efaec11190902ec9268db63a6d255
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298933"
---
# <a name="odbc-api-reference"></a>Informations de référence sur l’API ODBC
Les sujets de cette section décrivent chaque fonction ODBC par ordre alphabétique. Chaque fonction est définie comme une fonction linguistique de programmation C. Les descriptions comprennent ce qui suit:  
  
-   Objectif  
  
-   Version ODBC  
  
-   Niveau standard de conformité CLI  
  
-   Syntaxe  
  
-   Arguments  
  
-   Valeurs retournées  
  
-   Diagnostics  
  
-   Commentaires sur l’utilisation et la mise en œuvre  
  
-   Exemple de code  
  
-   Références aux fonctions connexes  
  
 Le niveau standard de conformité CLI peut être l’un des suivants: ISO 92, Open Group, ODBC, ou Déprémédé. Une fonction étiquetée comme ISO 92-conformant apparaît également dans la version 1 du Groupe Ouvert, parce que Open Group est un superset pur d’ISO 92. Une fonction étiquetée comme conforme au groupe ouvert apparaît également dans ODBC 3. *x*, parce que ODBC 3. *x* est un superset pur de la version 1 open Group. Une fonction étiquetée comme conforme à l’ODBC n’apparaît dans aucune des deux normes. Une fonction étiquetée comme dépréciée a été dépréciée dans ODBC 3. *x*.  
  
 Le traitement de l’information diagnostique est décrit dans la description de fonction [SQLGetDiagField.](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) Le texte associé aux valeurs SQLSTATE est inclus pour fournir une description de la condition, mais n’est pas destiné à prescrire un texte spécifique.  
  
> [!NOTE]  
>  Pour obtenir des renseignements spécifiques au conducteur sur les fonctions de l’ODBC, consultez la section pour le conducteur.  
  
 Cette section contient des sujets pour les fonctions suivantes :  
  
-   [SQLAllocConnect, fonction](../../../odbc/reference/syntax/sqlallocconnect-function.md)  
  
-   [SQLAllocEnv, fonction](../../../odbc/reference/syntax/sqlallocenv-function.md)  
  
-   [SQLAllocHandle, fonction](../../../odbc/reference/syntax/sqlallochandle-function.md)  
  
-   [SQLAllocStmt, fonction](../../../odbc/reference/syntax/sqlallocstmt-function.md)  
  
-   [Fonction SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)  
  
-   [Fonction SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)  
  
-   [Fonction SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)  
  
-   [SQLBulkOperations, fonction](../../../odbc/reference/syntax/sqlbulkoperations-function.md)  
  
-   [SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)  
  
-   [SQLCancelHandle, fonction](../../../odbc/reference/syntax/sqlcancelhandle-function.md)  
  
-   [SQLCloseCursor, fonction](../../../odbc/reference/syntax/sqlclosecursor-function.md)  
  
-   [Fonction SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)  
  
-   [SQLColAttributes, fonction](../../../odbc/reference/syntax/sqlcolattributes-function.md)  
  
-   [Fonction SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)  
  
-   [Fonction SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)  
  
-   [SQLCompleteAsync, fonction](../../../odbc/reference/syntax/sqlcompleteasync-function.md)  
  
-   [Fonction SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)  
  
-   [SQLCopyDesc, fonction](../../../odbc/reference/syntax/sqlcopydesc-function.md)  
  
-   [SQLDataSources, fonction](../../../odbc/reference/syntax/sqldatasources-function.md)  
  
-   [Fonction SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)  
  
-   [Fonction SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)  
  
-   [SQLDisconnect, fonction](../../../odbc/reference/syntax/sqldisconnect-function.md)  
  
-   [Fonction SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)  
  
-   [SQLDrivers, fonction](../../../odbc/reference/syntax/sqldrivers-function.md)  
  
-   [Fonction SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)  
  
-   [SQLError, fonction](../../../odbc/reference/syntax/sqlerror-function.md)  
  
-   [SQLExecDirect, fonction](../../../odbc/reference/syntax/sqlexecdirect-function.md)  
  
-   [SQLExecute, fonction](../../../odbc/reference/syntax/sqlexecute-function.md)  
  
-   [SQLExtendedFetch, fonction](../../../odbc/reference/syntax/sqlextendedfetch-function.md)  
  
-   [SQLFetch, fonction](../../../odbc/reference/syntax/sqlfetch-function.md)  
  
-   [Fonction SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)  
  
-   [Fonction SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)  
  
-   [SQLFreeConnect, fonction](../../../odbc/reference/syntax/sqlfreeconnect-function.md)  
  
-   [SQLFreeEnv, fonction](../../../odbc/reference/syntax/sqlfreeenv-function.md)  
  
-   [Fonction SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)  
  
-   [Fonction SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)  
  
-   [Fonction SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
-   [SQLGetConnectOption, fonction](../../../odbc/reference/syntax/sqlgetconnectoption-function.md)  
  
-   [SQLGetCursorName Function](../../../odbc/reference/syntax/sqlgetcursorname-function.md)  
  
-   [Fonction SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)  
  
-   [Fonction SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)  
  
-   [SQLGetDescRec, fonction](../../../odbc/reference/syntax/sqlgetdescrec-function.md)  
  
-   [Fonction SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
-   [SQLGetDiagRec, fonction](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)  
  
-   [SQLGetEnvAttr, fonction](../../../odbc/reference/syntax/sqlgetenvattr-function.md)  
  
-   [Fonction SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
-   [Fonction SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)  
  
-   [Fonction SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)  
  
-   [SQLGetStmtOption, fonction](../../../odbc/reference/syntax/sqlgetstmtoption-function.md)  
  
-   [Fonction SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)  
  
-   [Fonction SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)  
  
-   [Fonction SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md)  
  
-   [Fonction SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)  
  
-   [Fonction SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)  
  
-   [SQLParamData, fonction](../../../odbc/reference/syntax/sqlparamdata-function.md)  
  
-   [SQLParamOptions, fonction](../../../odbc/reference/syntax/sqlparamoptions-function.md)  
  
-   [Fonction SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)  
  
-   [Fonction SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)  
  
-   [Fonction SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)  
  
-   [Fonction SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)  
  
-   [Fonction SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)  
  
-   [SQLRowCount (fonction)](../../../odbc/reference/syntax/sqlrowcount-function.md)  
  
-   [Fonction SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)  
  
-   [SQLSetConnectOption, fonction](../../../odbc/reference/syntax/sqlsetconnectoption-function.md)  
  
-   [SQLSetCursorName, fonction](../../../odbc/reference/syntax/sqlsetcursorname-function.md)  
  
-   [SQLSetDescField, fonction](../../../odbc/reference/syntax/sqlsetdescfield-function.md)  
  
-   [SQLSetDescRec, fonction](../../../odbc/reference/syntax/sqlsetdescrec-function.md)  
  
-   [Fonction SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)  
  
-   [SQLSetParam, fonction](../../../odbc/reference/syntax/sqlsetparam-function.md)  
  
-   [SQLSetPos, fonction](../../../odbc/reference/syntax/sqlsetpos-function.md)  
  
-   [SQLSetScrollOptions, fonction](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)  
  
-   [Fonction SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)  
  
-   [SQLSetStmtOption, fonction](../../../odbc/reference/syntax/sqlsetstmtoption-function.md)  
  
-   [Fonction SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)  
  
-   [Fonction SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)  
  
-   [Fonction SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)  
  
-   [Fonction SQLTables](../../../odbc/reference/syntax/sqltables-function.md)  
  
-   [SQLTransact, fonction](../../../odbc/reference/syntax/sqltransact-function.md)

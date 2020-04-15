---
title: Rédaction de ODBC 3.x Drivers (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- upgrading drivers [ODBC]
- ODBC drivers [ODBC], upgrading
- backward compatibility [ODBC], drivers
- compatibility [ODBC], drivers
ms.assetid: 9b75f59b-623f-4711-9ca2-e751b3622e00
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 62f2a701fd5ac94c92d41494a4fd1ab023edaf25
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300359"
---
# <a name="writing-odbc-3x-drivers"></a>Écriture de pilotes ODBC 3.x
Le tableau suivant montre le soutien de la fonction dans un ODBC 3. *x* conducteur et une application ODBC, ainsi que la cartographie effectuée par le gestionnaire de conducteur lorsque les fonctions sont appelées contre un ODBC 3. *x* conducteur.  
  
|Fonction|Prise en charge<br /><br /> par un<br /><br /> ODBC 3. *x*<br /><br /> Pilote?|Prise en charge<br /><br /> par un<br /><br /> ODBC 3. *x*<br /><br /> Application?|Cartographié/soutenu<br /><br /> par l’ODBC 3. *x*<br /><br /> Driver Manager à<br /><br /> un ODBC 3. *x* conducteur?|  
|--------------|----------------------------------------------------|---------------------------------------------------------|---------------------------------------------------------------------------------------------|  
|**SQLAllocConnect (SQLAllocConnect)**|Non|Non[1]|Oui|  
|**SQLAllocEnv**|Non|Non[1]|Oui|  
|**SQLAllocHandle**|Oui|Oui|Non|  
|**SQLAllocStmt**|Non|Non[1]|Oui|  
|**SQLBindCol**|Oui|Oui|Non|  
|**SQLBindParam (SQLBindParam)**|Non|Oui[2]|Oui|  
|**SQLBindParameter**|Oui|Oui|Non|  
|**SQLBrowseConnect**|Oui|Oui|Non|  
|**SQLBulkOperations (SQLBulkOperations)**|Oui|Oui|Non|  
|**SQLCancel**|Oui|Oui|Non|  
|**SQLCloseCursor**|Oui|Oui|Non|  
|**SQLColAttribute**|Oui|Oui|Non|  
|**SQLColAttributes**|Non[3]|Non|Oui|  
|**SQLColumnPrivileges**|Oui|Oui|Non|  
|**SQLColumns**|Oui|Oui|Non|  
|**SQLConnect**|Oui|Oui|Non|  
|**SQLCopyDesc (SQLCopyDesc)**|Oui|Oui|Oui[4]|  
|**SQLDataSources**|Non|Oui|Oui|  
|**SQLDescribeCol**|Oui|Oui|Non|  
|**SQLDescribeParam**|Oui|Oui|Non|  
|**SQLDisconnect**|Oui|Oui|Non|  
|**SQLDriverConnect**|Oui|Oui|Non|  
|**SQLDrivers**|Non|Oui|Oui|  
|**SQLEndTran**|Oui|Oui|Non|  
|**Sqlerror**|Non|Non[1]|Oui|  
|**SQLExecDirect**|Oui|Oui|Non|  
|**SQLExecute**|Oui|Oui|Non|  
|**SQLExtendedFetch**|Oui|Non|Non|  
|**SQLFetch**|Oui|Oui|Non|  
|**SQLFetchScroll**|Oui|Oui|Non|  
|**SQLForeignKeys**|Oui|Oui|Non|  
|**SQLFreeConnect (en anglais)**|Non|Oui[1]|Oui|  
|**SQLFreeEnv**|Non|Oui[1]|Oui|  
|**SQLFreeHandle**|Oui|Oui|Non|  
|**SQLFreeStmt**|Oui|Oui|Non|  
|**SQLGetConnectAttr**|Oui|Oui|Non|  
|**SQLGetConnectOption (SQLGetConnectOption)**|Non[5]|Non[1]|Oui|  
|**SQLGetCursorName**|Oui|Oui|Non|  
|**SQLGetData**|Oui|Oui|Non|  
|**SQLGetDescField**|Oui|Oui|Non|  
|**SQLGetDescRec**|Oui|Oui|Non|  
|**SQLGetDiagField**|Oui|Oui|Non|  
|**SQLGetDiagRec**|Oui|Oui|Non|  
|**SQLGetEnvAttr**|Oui|Oui|Non|  
|**SQLGetFunctions**|Non[6]|Oui|Oui|  
|**SQLGetInfo**|Oui|Oui|Non|  
|**SQLGetStmtAttr**|Oui|Oui|Non|  
|**SQLGetStmtOption**|Non[5]|Non[1]|Oui|  
|**SQLGetTypeInfo**|Oui|Oui|Non|  
|**SQLMoreResults**|Oui|Oui|Non|  
|**SQLNativeSql**|Oui|Oui|Non|  
|**SQLNumParams**|Oui|Oui|Non|  
|**SQLNumResultCols**|Oui|Oui|Non|  
|**SQLParamData**|Oui|Oui|Non|  
|**SQLParamOptions**|Non|Non|Oui|  
|**SQLPrepare**|Oui|Oui|Non|  
|**SQLPrimaryKeys**|Oui|Oui|Non|  
|**SQLProcedureColumns**|Oui|Oui|Non|  
|**SQLProcedures**|Oui|Oui|Non|  
|**SQLPutData**|Oui|Oui|Non|  
|**SQLRowCount**|Oui|Oui|Non|  
|**SQLSetConnectAttr**|Oui|Oui|Non|  
|**SQLSetConnectOption**|Non[5]|Non[1]|Oui|  
|**SQLSetCursorName**|Oui|Oui|Non|  
|**SQLSetDescField**|Oui|Oui|Non|  
|**SQLSetDescRec**|Oui|Oui|Non|  
|**SQLSetEnvAttr**|Oui|Oui|Non|  
|**SQLSetPos**|Oui|Oui|Non|  
|**SQLSetParam (SQLSetParam)**|Non|Non|Oui|  
|**SQLSetScrollOption**|Oui|Oui|Non|  
|**SQLSetStmtAttr**|Oui|Oui|Non|  
|**SQLSetStmtOption**|Non[5]|Non[1]|Oui|  
|**SQLSpecialColumns**|Oui|Oui|Non|  
|**SQLStatistics**|Oui|Oui|Non|  
|**SQLTablePrivileges**|Oui|Oui|Non|  
|**SQLTables**|Oui|Oui|Non|  
|**SQLTransacte**|Non|Non[1]|Oui|  
  
 Cette fonction est dépréciée dans ODBC 3. *x*. ODBC 3. *x* applications ne doivent pas utiliser cette fonction. Toutefois, une application conforme à Open Group ou ISO CLI peut appeler cette fonction.  
  
 [2] ODBC 3. *x* les applications doivent utiliser **SQLBindParameter** au lieu de **SQLBindParam**. Toutefois, une application conforme à Open Group ou ISO CLI peut appeler cette fonction.  
  
 [3] Les auteurs de pilotes doivent noter que l’ODBC 2. *x* attributs colonne SQL_COLUMN_PRECISION, SQL_COLUMN_SCALE, et SQL_COLUMN_LENGTH doivent être pris en charge avec **SQLColAttribute**.  
  
 [4] **SQLCopyDesc** est partiellement mis en œuvre par le gestionnaire de conducteur lorsqu’un descripteur est copié entre les connexions qui appartiennent à différents conducteurs. Les conducteurs sont tenus de prendre en charge **SQLCopyDesc** à travers deux de leurs propres connexions. Les fonctions telles que **SQLDrivers**, qui sont mises en œuvre uniquement par le gestionnaire de conducteur, ne figurent pas sur cette liste.  
  
 [5] Dans certaines circonstances, les conducteurs peuvent avoir besoin de soutenir cette fonction. Pour plus d’informations, consultez la page de référence de cette fonction.  
  
 [6] Le conducteur peut choisir de prendre en charge **SQLGetFunctions** si l’ensemble des fonctions que le conducteur prend en charge varie d’une connexion à l’autre.

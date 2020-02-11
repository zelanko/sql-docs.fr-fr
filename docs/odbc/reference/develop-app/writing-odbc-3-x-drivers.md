---
title: Écriture des pilotes ODBC 3. x | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fb403cef47f901cdb43bbb32c669ba68aa34913d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68078903"
---
# <a name="writing-odbc-3x-drivers"></a>Écriture de pilotes ODBC 3.x
Le tableau suivant montre la prise en charge des fonctions dans ODBC 3. *x* et une application ODBC, ainsi que le mappage effectué par le gestionnaire de pilotes quand les fonctions sont appelées sur ODBC 3. pilote *x* .  
  
|Fonction|Prise en charge<br /><br /> par un<br /><br /> ODBC 3. *x*<br /><br /> pilote?|Prise en charge<br /><br /> par un<br /><br /> ODBC 3. *x*<br /><br /> oeuvre?|Mappé/pris en charge<br /><br /> par ODBC 3. *x*<br /><br /> Gestionnaire de pilotes pour<br /><br /> ODBC 3. pilote *x* ?|  
|--------------|----------------------------------------------------|---------------------------------------------------------|---------------------------------------------------------------------------------------------|  
|**SQLAllocConnect**|Non|Non [1]|Oui|  
|**SQLAllocEnv**|Non|Non [1]|Oui|  
|**SQLAllocHandle**|Oui|Oui|Non|  
|**SQLAllocStmt,**|Non|Non [1]|Oui|  
|**SQLBindCol**|Oui|Oui|Non|  
|**SQLBindParam**|Non|Oui [2]|Oui|  
|**SQLBindParameter**|Oui|Oui|Non|  
|**SQLBrowseConnect**|Oui|Oui|Non|  
|**SQLBulkOperations**|Oui|Oui|Non|  
|**SQLCancel**|Oui|Oui|Non|  
|**SQLCloseCursor**|Oui|Oui|Non|  
|**SQLColAttribute**|Oui|Oui|Non|  
|**SQLColAttributes**|Non [3]|Non|Oui|  
|**SQLColumnPrivileges**|Oui|Oui|Non|  
|**SQLColumns**|Oui|Oui|Non|  
|**SQLConnect**|Oui|Oui|Non|  
|**SQLCopyDesc**|Oui|Oui|Oui [4]|  
|**SQLDataSources**|Non|Oui|Oui|  
|**SQLDescribeCol**|Oui|Oui|Non|  
|**SQLDescribeParam**|Oui|Oui|Non|  
|**SQLDisconnect**|Oui|Oui|Non|  
|**SQLDriverConnect**|Oui|Oui|Non|  
|**SQLDrivers**|Non|Oui|Oui|  
|**SQLEndTran**|Oui|Oui|Non|  
|**SQLError**|Non|Non [1]|Oui|  
|**SQLExecDirect**|Oui|Oui|Non|  
|**SQLExecute**|Oui|Oui|Non|  
|**SQLExtendedFetch**|Oui|Non|Non|  
|**SQLFetch**|Oui|Oui|Non|  
|**SQLFetchScroll**|Oui|Oui|Non|  
|**SQLForeignKeys**|Oui|Oui|Non|  
|**Sqlfreeconnect,**|Non|Oui [1]|Oui|  
|**Sqlfreeenv,**|Non|Oui [1]|Oui|  
|**SQLFreeHandle**|Oui|Oui|Non|  
|**SQLFreeStmt**|Oui|Oui|Non|  
|**SQLGetConnectAttr**|Oui|Oui|Non|  
|**Sqlgetconnectoption,**|Non [5]|Non [1]|Oui|  
|**SQLGetCursorName**|Oui|Oui|Non|  
|**SQLGetData**|Oui|Oui|Non|  
|**SQLGetDescField**|Oui|Oui|Non|  
|**SQLGetDescRec**|Oui|Oui|Non|  
|**SQLGetDiagField**|Oui|Oui|Non|  
|**SQLGetDiagRec**|Oui|Oui|Non|  
|**SQLGetEnvAttr**|Oui|Oui|Non|  
|**SQLGetFunctions**|Non [6]|Oui|Oui|  
|**SQLGetInfo**|Oui|Oui|Non|  
|**SQLGetStmtAttr**|Oui|Oui|Non|  
|**SQLGetStmtOption**|Non [5]|Non [1]|Oui|  
|**SQLGetTypeInfo**|Oui|Oui|Non|  
|**SQLMoreResults**|Oui|Oui|Non|  
|**SQLNativeSql**|Oui|Oui|Non|  
|**SQLNumParams**|Oui|Oui|Non|  
|**SQLNumResultCols**|Oui|Oui|Non|  
|**SQLParamData**|Oui|Oui|Non|  
|**SQLParamOptions,**|Non|Non|Oui|  
|**SQLPrepare**|Oui|Oui|Non|  
|**SQLPrimaryKeys**|Oui|Oui|Non|  
|**SQLProcedureColumns**|Oui|Oui|Non|  
|**SQLProcedures**|Oui|Oui|Non|  
|**SQLPutData**|Oui|Oui|Non|  
|**SQLRowCount**|Oui|Oui|Non|  
|**SQLSetConnectAttr**|Oui|Oui|Non|  
|**SQLSetConnectOption**|Non [5]|Non [1]|Oui|  
|**SQLSetCursorName**|Oui|Oui|Non|  
|**SQLSetDescField**|Oui|Oui|Non|  
|**SQLSetDescRec**|Oui|Oui|Non|  
|**SQLSetEnvAttr**|Oui|Oui|Non|  
|**SQLSetPos**|Oui|Oui|Non|  
|**SQLSetParam,**|Non|Non|Oui|  
|**SQLSetScrollOption**|Oui|Oui|Non|  
|**SQLSetStmtAttr**|Oui|Oui|Non|  
|**SQLSetStmtOption**|Non [5]|Non [1]|Oui|  
|**SQLSpecialColumns**|Oui|Oui|Non|  
|**SQLStatistics**|Oui|Oui|Non|  
|**SQLTablePrivileges**|Oui|Oui|Non|  
|**SQLTables**|Oui|Oui|Non|  
|**SQLTransact**|Non|Non [1]|Oui|  
  
 [1] cette fonction est déconseillée dans ODBC 3. *x*. ODBC 3. *x* les applications ne doivent pas utiliser cette fonction. Toutefois, un groupe ouvert ou une application compatible avec la CLI ISO peut appeler cette fonction.  
  
 [2] ODBC 3. *x* les applications doivent utiliser **SQLBindParameter** au lieu de **SQLBindParam**. Toutefois, un groupe ouvert ou une application compatible avec la CLI ISO peut appeler cette fonction.  
  
 [3] les rédacteurs de pilote doivent noter que ODBC 2. les attributs de colonne *x* SQL_COLUMN_PRECISION, SQL_COLUMN_SCALE et SQL_COLUMN_LENGTH doivent être pris en charge avec **SQLColAttribute**.  
  
 [4] **SQLCopyDesc** est partiellement implémenté par le gestionnaire de pilotes lorsqu’un descripteur est copié entre des connexions qui appartiennent à des pilotes différents. Les pilotes sont requis pour prendre en charge les **SQLCopyDesc** sur deux de leurs propres connexions. Les fonctions telles que **SQLDrivers**, qui sont implémentées uniquement par le gestionnaire de pilotes, ne s’affichent pas dans cette liste.  
  
 [5] dans certains cas, il se peut que les pilotes doivent prendre en charge cette fonction. Pour plus d’informations, consultez la page de référence de cette fonction.  
  
 [6] le pilote peut choisir de prendre en charge **SQLGetFunctions** si l’ensemble de fonctions que le pilote prend en charge varie d’une connexion à une connexion.

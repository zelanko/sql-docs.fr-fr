---
title: Écriture de pilotes ODBC 3.x | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 77a94c7505b5ab221fee4896e91f9b26850669df
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47795649"
---
# <a name="writing-odbc-3x-drivers"></a>Écriture de pilotes ODBC 3.x
Le tableau suivant présente la prise en charge de la fonction dans un ODBC 3. *x* pilote et une application ODBC et le mappage effectuée par le Gestionnaire de pilotes lorsque les fonctions sont appelées par rapport à un ODBC 3. *x* pilote.  
  
|Fonction|Pris en charge<br /><br /> par un<br /><br /> ODBC 3. *x*<br /><br /> pilote ?|Pris en charge<br /><br /> par un<br /><br /> ODBC 3. *x*<br /><br /> application ?|Mappé/prise en charge<br /><br /> par le ODBC 3. *x*<br /><br /> Gestionnaire de pilotes à<br /><br /> un ODBC 3. *x* pilote ?|  
|--------------|----------------------------------------------------|---------------------------------------------------------|---------------------------------------------------------------------------------------------|  
|**SQLAllocConnect**|non|Aucun [1]|Oui|  
|**SQLAllocEnv**|non|Aucun [1]|Oui|  
|**SQLAllocHandle**|Oui|Oui|non|  
|**SQLAllocStmt**|non|Aucun [1]|Oui|  
|**SQLBindCol**|Oui|Oui|non|  
|**SQLBindParam**|non|Oui [2]|Oui|  
|**SQLBindParameter**|Oui|Oui|non|  
|**SQLBrowseConnect**|Oui|Oui|non|  
|**SQLBulkOperations**|Oui|Oui|non|  
|**SQLCancel**|Oui|Oui|non|  
|**SQLCloseCursor**|Oui|Oui|non|  
|**SQLColAttribute**|Oui|Oui|non|  
|**SQLColAttributes**|Aucun [3]|non|Oui|  
|**SQLColumnPrivileges**|Oui|Oui|non|  
|**SQLColumns**|Oui|Oui|non|  
|**SQLConnect**|Oui|Oui|non|  
|**SQLCopyDesc**|Oui|Oui|Oui [4]|  
|**SQLDataSources**|non|Oui|Oui|  
|**SQLDescribeCol**|Oui|Oui|non|  
|**SQLDescribeParam**|Oui|Oui|non|  
|**SQLDisconnect**|Oui|Oui|non|  
|**SQLDriverConnect**|Oui|Oui|non|  
|**SQLDrivers**|non|Oui|Oui|  
|**SQLEndTran**|Oui|Oui|non|  
|**SQLError**|non|Aucun [1]|Oui|  
|**SQLExecDirect**|Oui|Oui|non|  
|**SQLExecute**|Oui|Oui|non|  
|**SQLExtendedFetch**|Oui|non|non|  
|**SQLFetch**|Oui|Oui|non|  
|**SQLFetchScroll**|Oui|Oui|non|  
|**SQLForeignKeys**|Oui|Oui|non|  
|**SQLFreeConnect**|non|Oui [1]|Oui|  
|**SQLFreeEnv**|non|Oui [1]|Oui|  
|**SQLFreeHandle**|Oui|Oui|non|  
|**SQLFreeStmt**|Oui|Oui|non|  
|**SQLGetConnectAttr**|Oui|Oui|non|  
|**SQLGetConnectOption**|Aucun [5]|Aucun [1]|Oui|  
|**SQLGetCursorName**|Oui|Oui|non|  
|**SQLGetData**|Oui|Oui|non|  
|**SQLGetDescField**|Oui|Oui|non|  
|**SQLGetDescRec**|Oui|Oui|non|  
|**SQLGetDiagField**|Oui|Oui|non|  
|**SQLGetDiagRec**|Oui|Oui|non|  
|**SQLGetEnvAttr**|Oui|Oui|non|  
|**SQLGetFunctions**|Aucun [6]|Oui|Oui|  
|**SQLGetInfo**|Oui|Oui|non|  
|**SQLGetStmtAttr**|Oui|Oui|non|  
|**SQLGetStmtOption**|Aucun [5]|Aucun [1]|Oui|  
|**SQLGetTypeInfo**|Oui|Oui|non|  
|**SQLMoreResults**|Oui|Oui|non|  
|**SQLNativeSql**|Oui|Oui|non|  
|**SQLNumParams**|Oui|Oui|non|  
|**SQLNumResultCols**|Oui|Oui|non|  
|**SQLParamData**|Oui|Oui|non|  
|**SQLParamOptions**|non|non|Oui|  
|**SQLPrepare**|Oui|Oui|non|  
|**SQLPrimaryKeys**|Oui|Oui|non|  
|**SQLProcedureColumns**|Oui|Oui|non|  
|**SQLProcedures**|Oui|Oui|non|  
|**SQLPutData**|Oui|Oui|non|  
|**SQLRowCount**|Oui|Oui|non|  
|**SQLSetConnectAttr**|Oui|Oui|non|  
|**SQLSetConnectOption**|Aucun [5]|Aucun [1]|Oui|  
|**SQLSetCursorName**|Oui|Oui|non|  
|**SQLSetDescField**|Oui|Oui|non|  
|**SQLSetDescRec**|Oui|Oui|non|  
|**SQLSetEnvAttr**|Oui|Oui|non|  
|**SQLSetPos**|Oui|Oui|non|  
|**SQLSetParam**|non|non|Oui|  
|**SQLSetScrollOption**|Oui|Oui|non|  
|**SQLSetStmtAttr**|Oui|Oui|non|  
|**SQLSetStmtOption**|Aucun [5]|Aucun [1]|Oui|  
|**SQLSpecialColumns**|Oui|Oui|non|  
|**SQLStatistics**|Oui|Oui|non|  
|**SQLTablePrivileges**|Oui|Oui|non|  
|**SQLTables**|Oui|Oui|non|  
|**SQLTransact**|non|Aucun [1]|Oui|  
  
 [1], cette fonction est déconseillée dans ODBC 3. *x*. ODBC 3. *x* applications ne doivent pas utiliser cette fonction. Toutefois, une application compatible avec ISO CLI, ou le Open Group peut appeler cette fonction.  
  
 [2] ODBC 3. *x* les applications doivent utiliser **SQLBindParameter** au lieu de **SQLBindParam**. Toutefois, une application compatible avec ISO CLI, ou le Open Group peut appeler cette fonction.  
  
 [3] les rédacteurs de pilotes sont à noter que ODBC 2. *x* SQL_COLUMN_PRECISION, SQL_COLUMN_SCALE et SQL_COLUMN_LENGTH doivent être pris en charge avec des attributs de colonne **SQLColAttribute**.  
  
 [4] **SQLCopyDesc** est partiellement implémentée par le Gestionnaire de pilotes lorsqu’un descripteur est copié sur les connexions qui appartiennent à différents pilotes. Pilotes sont requis pour prendre en charge **SQLCopyDesc** entre deux de leurs propres connexions. Les fonctions comme **SQLDrivers**, qui est implémenté uniquement par le Gestionnaire de pilotes, ne s’affichent pas dans cette liste.  
  
 [5] dans certaines circonstances, les pilotes peut-être prendre en charge cette fonction. Pour plus d’informations, consultez la page de référence de cette fonction.  
  
 [6] le pilote peut choisir de prendre en charge **SQLGetFunctions** si l’ensemble de fonctions qui prend en charge par le pilote varie à partir d’une connexion à une connexion.

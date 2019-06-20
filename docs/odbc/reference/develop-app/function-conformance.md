---
title: Fonction de la conformité | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- conformance levels [ODBC], function
- function conformance levels [ODBC]
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: bb5d68cf-d238-481e-babc-2e9401b4700e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b6cb2f56113487922866573caf3b5f8b67fff7c4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63061577"
---
# <a name="function-conformance"></a>Conformité des fonctions
Le tableau suivant indique le niveau de conformité de chaque fonction ODBC, où il s’agit bien défini.  
  
|Fonction|Niveau de conformité|  
|--------------|-----------------------|  
|**SQLAllocHandle**|Noyau|  
|**SQLBindCol**|Noyau|  
|**SQLBindParameter**|Core [1]|  
|**SQLBrowseConnect**|Niveau 1|  
|**SQLBulkOperations**|Niveau 1|  
|**SQLCancel**|Core [1]|  
|**SQLCloseCursor**|Noyau|  
|**SQLColAttribute**|Core [1]|  
|**SQLColumnPrivileges**|Niveau 2|  
|**SQLColumns**|Noyau|  
|**SQLConnect**|Noyau|  
|**SQLCopyDesc**|Noyau|  
|**SQLDataSources**|Noyau|  
|**SQLDescribeCol**|Core [1]|  
|**SQLDescribeParam**|Niveau 2|  
|**SQLDisconnect**|Noyau|  
|**SQLDriverConnect**|Noyau|  
|**SQLDrivers**|Noyau|  
|**SQLEndTran**|Core [1]|  
|**SQLExecDirect**|Noyau|  
|**SQLExecute**|Noyau|  
|**SQLFetch**|Noyau|  
|**SQLFetchScroll**|Core [1]|  
|**SQLForeignKeys**|Niveau 2|  
|**SQLFreeHandle**|Noyau|  
|**SQLFreeStmt**|Noyau|  
|**SQLGetConnectAttr**|Noyau|  
|**SQLGetCursorName**|Noyau|  
|**SQLGetData**|Noyau|  
|**SQLGetDescField**|Noyau|  
|**SQLGetDescRec**|Noyau|  
|**SQLGetDiagField**|Noyau|  
|**SQLGetDiagRec**|Noyau|  
|**SQLGetEnvAttr**|Noyau|  
|**SQLGetFunctions**|Noyau|  
|**SQLGetInfo**|Noyau|  
|**SQLGetStmtAttr**|Noyau|  
|**SQLGetTypeInfo**|Noyau|  
|**SQLMoreResults**|Niveau 1|  
|**SQLNativeSql**|Noyau|  
|**SQLNumParams**|Noyau|  
|**SQLNumResultCols**|Noyau|  
|**SQLParamData**|Noyau|  
|**SQLPrepare**|Noyau|  
|**SQLPrimaryKeys**|Niveau 1|  
|**SQLProcedureColumns**|Niveau 1|  
|**SQLProcedures**|Niveau 1|  
|**SQLPutData**|Noyau|  
|**SQLRowCount**|Noyau|  
|**SQLSetConnectAttr**|Core [2]|  
|**SQLSetCursorName**|Noyau|  
|**SQLSetDescField**|Core [1]|  
|**SQLSetDescRec**|Noyau|  
|**SQLSetEnvAttr**|Core [2]|  
|**SQLSetPos**|Niveau 1 [1]|  
|**SQLSetStmtAttr**|Core [2]|  
|**SQLSpecialColumns**|Core [1]|  
|**SQLStatistics**|Noyau|  
|**SQLTablePrivileges**|Niveau 2|  
|**SQLTables**|Noyau|  
  
 [1] étonnante de cette fonction est disponibles uniquement à des niveaux plus élevés de la conformité.  
  
 [2] définissant certains attributs pour les valeurs par défaut varie selon le niveau de conformité. Pour plus d’informations, consultez la section suivante, [conformité des attributs](../../../odbc/reference/develop-app/attribute-conformance.md).

---
title: Conformité des fonctions | Microsoft Docs
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
ms.openlocfilehash: 45eb427b660496430334633b5d43ee8989211c0f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68069753"
---
# <a name="function-conformance"></a>Conformité des fonctions
Le tableau suivant indique le niveau de conformité de chaque fonction ODBC, où elle est bien définie.  
  
|Fonction|Niveau de conformité|  
|--------------|-----------------------|  
|**SQLAllocHandle**|Core|  
|**SQLBindCol**|Core|  
|**SQLBindParameter**|Noyau [1]|  
|**SQLBrowseConnect**|Niveau 1|  
|**SQLBulkOperations**|Niveau 1|  
|**SQLCancel**|Noyau [1]|  
|**SQLCloseCursor**|Core|  
|**SQLColAttribute**|Noyau [1]|  
|**SQLColumnPrivileges**|Level 2|  
|**SQLColumns**|Core|  
|**SQLConnect**|Core|  
|**SQLCopyDesc**|Core|  
|**SQLDataSources**|Core|  
|**SQLDescribeCol**|Noyau [1]|  
|**SQLDescribeParam**|Level 2|  
|**SQLDisconnect**|Core|  
|**SQLDriverConnect**|Core|  
|**SQLDrivers**|Core|  
|**SQLEndTran**|Noyau [1]|  
|**SQLExecDirect**|Core|  
|**SQLExecute**|Core|  
|**SQLFetch**|Core|  
|**SQLFetchScroll**|Noyau [1]|  
|**SQLForeignKeys**|Level 2|  
|**SQLFreeHandle**|Core|  
|**SQLFreeStmt**|Core|  
|**SQLGetConnectAttr**|Core|  
|**SQLGetCursorName**|Core|  
|**SQLGetData**|Core|  
|**SQLGetDescField**|Core|  
|**SQLGetDescRec**|Core|  
|**SQLGetDiagField**|Core|  
|**SQLGetDiagRec**|Core|  
|**SQLGetEnvAttr**|Core|  
|**SQLGetFunctions**|Core|  
|**SQLGetInfo**|Core|  
|**SQLGetStmtAttr**|Core|  
|**SQLGetTypeInfo**|Core|  
|**SQLMoreResults**|Niveau 1|  
|**SQLNativeSql**|Core|  
|**SQLNumParams**|Core|  
|**SQLNumResultCols**|Core|  
|**SQLParamData**|Core|  
|**SQLPrepare**|Core|  
|**SQLPrimaryKeys**|Niveau 1|  
|**SQLProcedureColumns**|Niveau 1|  
|**SQLProcedures**|Niveau 1|  
|**SQLPutData**|Core|  
|**SQLRowCount**|Core|  
|**SQLSetConnectAttr**|Noyau [2]|  
|**SQLSetCursorName**|Core|  
|**SQLSetDescField**|Noyau [1]|  
|**SQLSetDescRec**|Core|  
|**SQLSetEnvAttr**|Noyau [2]|  
|**SQLSetPos**|Niveau 1 [1]|  
|**SQLSetStmtAttr**|Noyau [2]|  
|**SQLSpecialColumns**|Noyau [1]|  
|**SQLStatistics**|Core|  
|**SQLTablePrivileges**|Level 2|  
|**SQLTables**|Core|  
  
 [1] les fonctionnalités significatives de cette fonction ne sont disponibles qu’à des niveaux de conformité plus élevés.  
  
 [2] la définition de certains attributs à des valeurs qui ne sont pas des valeurs par défaut dépend du niveau de conformité. Pour plus d’informations, consultez la section suivante, [conformité aux attributs](../../../odbc/reference/develop-app/attribute-conformance.md).

---
title: "Mappage des fonctions déconseillées | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mapping deprecated functions [ODBC], about mapping deprecated functions
- backward compatibility [ODBC], mapping deprecated functions
- deprecated functions [ODBC]
- compatibility [ODBC], mapping deprecated functions
- functions [ODBC], mapping deprecated functions
- mapping deprecated functions [ODBC]
ms.assetid: ee462617-1d79-4c88-afeb-b129cff34cc6
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fa5f1fb5c50911718adf3aa509dd99fb6e30673c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="mapping-deprecated-functions"></a>Mappage des fonctions déconseillées
Cette section décrit les fonctions déconseillées comment sont mappés par les 3 ODBC*.x* du Gestionnaire de pilotes pour garantir la compatibilité descendante des ODBC 3*.x* pilotes qui sont utilisés avec ODBC 2. *x* applications. Le Gestionnaire de pilotes effectue ce mappage, quelle que soit la version de l’application. Étant donné que chaque ODBC 2. *x* fonctions dans la liste suivante est mappée à la 3 ODBC correspondants*.x* fonction lorsqu’elle est appelée dans un ODBC 3*.x* pilote, la version 3 ODBC*.x* pilote n’a pas d’implémenter ODBC 2. *x* fonctions.  
  
 Le mappage dans la liste est déclenché lorsque le pilote est un ODBC 3*.x* pilote et le pilote ne prend pas en charge la fonction qui est mappée.  
  
 Le tableau suivant répertorie les fonctionnalités tout en double a été introduite dans ODBC 3*.x*.  
  
|ODBC 2. *x* (fonction)|ODBC 3*.x* (fonction)|  
|-------------------------|-------------------------|  
|**SQLAllocConnect**|**SQLAllocHandle**|  
|**SQLAllocEnv**|**SQLAllocHandle**|  
|**SQLAllocStmt**|**SQLAllocHandle**|  
|**SQLBindParam**[1]|**SQLBindParameter**|  
|**SQLColAttributes**|**SQLColAttribute**|  
|**SQLError**|**SQLGetDiagRec**|  
|**SQLFreeConnect**|**SQLFreeHandle**|  
|**SQLFreeEnv**|**SQLFreeHandle**|  
|**SQLFreeStmt** avec un *Option* de SQL_DROP|**SQLFreeHandle**|  
|**SQLGetConnectOption**|**SQLGetConnectAttr**|  
|**SQLGetStmtOption**|**SQLGetStmtAttr**|  
|**SQLParamOptions**|**SQLSetStmtAttr**|  
|**SQLSetConnectOption**|**SQLSetConnectAttr**|  
|**SQLSetParam**[2]|**SQLBindParameter**|  
|**SQLSetScrollOption**|**SQLSetStmtAttr**|  
|**SQLSetStmtOption**|**SQLSetStmtAttr**|  
|**SQLTransact**|**SQLEndTran**|  
  
 [1] même si cette fonction n’existait pas dans ODBC 2*.x*, il se trouve dans les normes Open Group et ISO.  
  
 [2]. il s’agit d’une fonction ODBC version 1.0.  
  
 Cette section contient les rubriques suivantes.  
  
-   [SQLAllocConnect, mappage](../../../odbc/reference/appendixes/sqlallocconnect-mapping.md)  
  
-   [SQLAllocEnv, mappage](../../../odbc/reference/appendixes/sqlallocenv-mapping.md)  
  
-   [SQLAllocStmt, mappage](../../../odbc/reference/appendixes/sqlallocstmt-mapping.md)  
  
-   [SQLBindParam, mappage](../../../odbc/reference/appendixes/sqlbindparam-mapping.md)  
  
-   [SQLColAttributes, mappage](../../../odbc/reference/appendixes/sqlcolattributes-mapping.md)  
  
-   [SQLError, mappage](../../../odbc/reference/appendixes/sqlerror-mapping.md)  
  
-   [SQLFreeConnect, mappage](../../../odbc/reference/appendixes/sqlfreeconnect-mapping.md)  
  
-   [SQLFreeEnv, mappage](../../../odbc/reference/appendixes/sqlfreeenv-mapping.md)  
  
-   [SQLFreeStmt, mappage](../../../odbc/reference/appendixes/sqlfreestmt-mapping.md)  
  
-   [SQLGetConnectOption, mappage](../../../odbc/reference/appendixes/sqlgetconnectoption-mapping.md)  
  
-   [SQLGetStmtOption, mappage](../../../odbc/reference/appendixes/sqlgetstmtoption-mapping.md)  
  
-   [SQLInstallTranslator, mappage](../../../odbc/reference/appendixes/sqlinstalltranslator-mapping.md)  
  
-   [SQLParamOptions, mappage](../../../odbc/reference/appendixes/sqlparamoptions-mapping.md)  
  
-   [SQLSetConnectOption, mappage](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md)  
  
-   [SQLSetParam, mappage](../../../odbc/reference/appendixes/sqlsetparam-mapping.md)  
  
-   [SQLSetScrollOptions, mappage](../../../odbc/reference/appendixes/sqlsetscrolloptions-mapping.md)  
  
-   [SQLSetStmtOption, mappage](../../../odbc/reference/appendixes/sqlsetstmtoption-mapping.md)  
  
-   [SQLTransact, mappage](../../../odbc/reference/appendixes/sqltransact-mapping.md)

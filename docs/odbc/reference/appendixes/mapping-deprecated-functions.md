---
title: Mappage des fonctions dépréciées | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], about mapping deprecated functions
- backward compatibility [ODBC], mapping deprecated functions
- deprecated functions [ODBC]
- compatibility [ODBC], mapping deprecated functions
- functions [ODBC], mapping deprecated functions
- mapping deprecated functions [ODBC]
ms.assetid: ee462617-1d79-4c88-afeb-b129cff34cc6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b59d2604dd9d4b7c3166027c1917dea096b331d9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63181317"
---
# <a name="mapping-deprecated-functions"></a>Mappage des fonctions dépréciées
Cette section décrit les fonctions déconseillées comment sont mappés par le ODBC 3 *.x* Gestionnaire de pilotes afin de garantir la compatibilité descendante de ODBC 3 *.x* pilotes qui sont utilisés avec ODBC 2. *x* applications. Le Gestionnaire de pilotes effectue ce mappage, quel que soit la version de l’application. Étant donné que chacun des ODBC 2. *x* fonctions dans la liste suivante est mappée à le correspondantes ODBC 3 *.x* fonction lorsqu’elle est appelée dans un ODBC 3 *.x* pilote, le 3 ODBC *.x*pilote ne doit pas implémenter d’ODBC 2. *x* fonctions.  
  
 Le mappage dans la liste est déclenché lorsque le pilote est un ODBC 3 *.x* pilote et le pilote ne prend pas en charge la fonction qui est mappée.  
  
 Le tableau suivant répertorie les fonctionnalités tout en double qui a été introduite dans ODBC 3 *.x*.  
  
|ODBC 2. *x* (fonction)|ODBC 3 *.x* (fonction)|  
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
  
 [1] bien que cette fonction n’existait pas dans ODBC 2 *.x*, il se trouve dans les normes Open Group et ISO.  
  
 [2] Il s’agit d’une fonction ODBC 1.0.  
  
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

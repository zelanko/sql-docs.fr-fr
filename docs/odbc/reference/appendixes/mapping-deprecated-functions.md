---
title: "Mappage des fonctions déconseillées | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
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
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 61d05017039673989e1477501feb17b3da6d7220
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

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
  
-   [Mappage de SQLAllocConnect](../../../odbc/reference/appendixes/sqlallocconnect-mapping.md)  
  
-   [Mappage de SQLAllocEnv](../../../odbc/reference/appendixes/sqlallocenv-mapping.md)  
  
-   [Mappage de SQLAllocStmt](../../../odbc/reference/appendixes/sqlallocstmt-mapping.md)  
  
-   [Mappage de SQLBindParam](../../../odbc/reference/appendixes/sqlbindparam-mapping.md)  
  
-   [Mappage de SQLColAttributes](../../../odbc/reference/appendixes/sqlcolattributes-mapping.md)  
  
-   [Mappage de SQLError](../../../odbc/reference/appendixes/sqlerror-mapping.md)  
  
-   [Mappage de SQLFreeConnect](../../../odbc/reference/appendixes/sqlfreeconnect-mapping.md)  
  
-   [Mappage de SQLFreeEnv](../../../odbc/reference/appendixes/sqlfreeenv-mapping.md)  
  
-   [Mappage de SQLFreeStmt](../../../odbc/reference/appendixes/sqlfreestmt-mapping.md)  
  
-   [Mappage de SQLGetConnectOption](../../../odbc/reference/appendixes/sqlgetconnectoption-mapping.md)  
  
-   [Mappage de SQLGetStmtOption](../../../odbc/reference/appendixes/sqlgetstmtoption-mapping.md)  
  
-   [Mappage de SQLInstallTranslator](../../../odbc/reference/appendixes/sqlinstalltranslator-mapping.md)  
  
-   [Mappage de SQLParamOptions](../../../odbc/reference/appendixes/sqlparamoptions-mapping.md)  
  
-   [Mappage de SQLSetConnectOption](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md)  
  
-   [Mappage de SQLSetParam](../../../odbc/reference/appendixes/sqlsetparam-mapping.md)  
  
-   [Mappage de SQLSetScrollOptions](../../../odbc/reference/appendixes/sqlsetscrolloptions-mapping.md)  
  
-   [Mappage de SQLSetStmtOption](../../../odbc/reference/appendixes/sqlsetstmtoption-mapping.md)  
  
-   [Mappage de SQLTransact](../../../odbc/reference/appendixes/sqltransact-mapping.md)


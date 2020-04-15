---
title: Cartographie des fonctions dépréciées (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a4e89cd9281520e70ec5fb289c6050e77ec6194c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299879"
---
# <a name="mapping-deprecated-functions"></a>Mappage des fonctions dépréciées
Cette section décrit comment les fonctions dépréciées sont cartographiées par l’ODBC *3.x* Driver Manager pour garantir la compatibilité rétrograde des pilotes ODBC *3.x* qui sont utilisés avec les applications ODBC *2.x.* Le Driver Manager effectue cette cartographie quelle que soit la version de l’application. Étant donné que chacune des fonctions ODBC *2.x* de la liste suivante est cartographiée pour la fonction ODBC *3.x* correspondante lorsqu’elle est appelée dans un pilote ODBC *3.x,* le pilote ODBC *3.x* n’a pas à implémenter les fonctions ODBC *2.x.*  
  
 La cartographie dans la liste est déclenchée lorsque le conducteur est un pilote ODBC *3.x* et que le conducteur ne prend pas en charge la fonction qui est cartographiée.  
  
 Le tableau suivant répertorie toutes les fonctionnalités dupliquées qui ont été introduites dans ODBC *3.x*.  
  
|Fonction ODBC *2.x*|Fonction ODBC *3.x*|  
|-------------------------|-------------------------|  
|**SQLAllocConnect (SQLAllocConnect)**|**SQLAllocHandle**|  
|**SQLAllocEnv**|**SQLAllocHandle**|  
|**SQLAllocStmt**|**SQLAllocHandle**|  
|**SQLBindParam**[1]|**SQLBindParameter**|  
|**SQLColAttributes**|**SQLColAttribute**|  
|**Sqlerror**|**SQLGetDiagRec**|  
|**SQLFreeConnect (en anglais)**|**SQLFreeHandle**|  
|**SQLFreeEnv**|**SQLFreeHandle**|  
|**SQLFreeStmt** avec une *option* de SQL_DROP|**SQLFreeHandle**|  
|**SQLGetConnectOption (SQLGetConnectOption)**|**SQLGetConnectAttr**|  
|**SQLGetStmtOption**|**SQLGetStmtAttr**|  
|**SQLParamOptions**|**SQLSetStmtAttr**|  
|**SQLSetConnectOption**|**SQLSetConnectAttr**|  
|**SQLSetParam**[2]|**SQLBindParameter**|  
|**SQLSetScrollOption**|**SQLSetStmtAttr**|  
|**SQLSetStmtOption**|**SQLSetStmtAttr**|  
|**SQLTransacte**|**SQLEndTran**|  
  
 [1] Même si cette fonction n’existait pas dans ODBC *2.x*, il est dans le groupe ouvert et les normes ISO.  
  
 [2] Il s’agit d’une fonction ODBC 1.0.  
  
 Cette section contient les rubriques suivantes :  
  
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

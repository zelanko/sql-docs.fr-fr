---
title: Conformité des attributs | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
- conformance levels [ODBC], attribute
- attribute conformance levels [ODBC]
ms.assetid: 34fea100-10f9-46d5-bc50-3aa867b70f24
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b2880a35f4bdc997cc037cdd0d60720267ff4a58
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306400"
---
# <a name="attribute-conformance"></a>Conformité des attributs
Le tableau suivant indique le niveau de conformité de chaque attribut d’environnement ODBC, où ce est bien défini.  
  
|Fonction|Niveau de conformité|  
|--------------|-----------------------|  
|SQL_ATTR_CONNECTION_POOLING|--[1]|  
|SQL_ATTR_CP_MATCH|--[1]|  
|SQL_ATTR_ODBC_VER|Core|  
|SQL_ATTR_OUTPUT_NTS|--[1]|  
  
 [1] il s’agit d’une fonctionnalité facultative qui ne fait pas partie des niveaux de conformité.  
  
 Le tableau suivant indique le niveau de conformité de chaque attribut de connexion ODBC, où ce est bien défini.  
  
|Fonction|Niveau de conformité|  
|--------------|-----------------------|  
|SQL_ATTR_ACCESS_MODE|Core|  
|SQL_ATTR_ASYNC_ENABLE|Niveau 1/niveau 2 [1]|  
|SQL_ATTR_AUTO_IPD|Niveau 2|  
|SQL_ATTR_AUTOCOMMIT|Niveau 1|  
|SQL_ATTR_CONNECTION_DEAD|Niveau 1|  
|SQL_ATTR_CONNECTION_TIMEOUT|Niveau 2|  
|SQL_ATTR_CURRENT_CATALOG|Niveau 2|  
|SQL_ATTR_LOGIN_TIMEOUT|Niveau 2|  
|SQL_ATTR_ODBC_CURSORS|Core|  
|SQL_ATTR_PACKET_SIZE|Niveau 2|  
|SQL_ATTR_QUIET_MODE|Core|  
|SQL_ATTR_TRACE|Core|  
|SQL_ATTR_TRACEFILE|Core|  
|SQL_ATTR_TRANSLATE_LIB|Core|  
|SQL_ATTR_TRANSLATE_OPTION|Core|  
|SQL_ATTR_TXN_ISOLATION|Niveau 1/niveau 2 [2]|  
  
 [1] les applications qui prennent en charge l’asynchronie au niveau de la connexion (requises pour le niveau 1) doivent prendre en charge la définition de cet attribut sur SQL_TRUE en appelant **SQLSetConnectAttr**; l’attribut n’a pas besoin d’être définissable à une valeur autre que sa valeur par défaut jusqu’à **SQLSetStmtAttr**. Les applications qui prennent en charge l’asynchronie au niveau des instructions (requises pour le niveau 2) doivent prendre en charge la définition de cet attribut sur SQL_TRUE à l’aide de l’une des fonctions.  
  
 [2] pour la conformité de l’interface de niveau 1, le pilote doit prendre en charge une valeur en plus de la valeur par défaut définie par le pilote (disponible en appelant **SQLGetInfo** avec l’option SQL_DEFAULT_TXN_ISOLATION). Pour la conformité de l’interface de niveau 2, le pilote doit également prendre en charge SQL_TXN_SERIALIZABLE.  
  
 Le tableau suivant indique le niveau de conformité de chaque attribut d’instruction ODBC, où ce est bien défini.  
  
|Fonction|Niveau de conformité|  
|--------------|-----------------------|  
|SQL_ATTR_APP_PARAM_DESC|Core|  
|SQL_ATTR_APP_ROW_DESC|Core|  
|SQL_ATTR_ASYNC_ENABLE|Niveau 1/niveau 2 [1]|  
|SQL_ATTR_CONCURRENCY|Niveau 1/niveau 2 [2]|  
|SQL_ATTR_CURSOR_SCROLLABLE|Niveau 1|  
|SQL_ATTR_CURSOR_SENSITIVITY|Niveau 2|  
|SQL_ATTR_CURSOR_TYPE|Core/niveau 2 [3]|  
|SQL_ATTR_ENABLE_AUTO_IPD|Niveau 2|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|Niveau 2|  
|SQL_ATTR_IMP_PARAM_DESC|Core|  
|SQL_ATTR_IMP_ROW_DESC|Core|  
|SQL_ATTR_KEYSET_SIZE|Niveau 2|  
|SQL_ATTR_MAX_LENGTH|Niveau 1|  
|SQL_ATTR_MAX_ROWS|Niveau 1|  
|SQL_ATTR_METADATA_ID|Core|  
|SQL_ATTR_NOSCAN|Core|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR|Core|  
|SQL_ATTR_PARAM_BIND_TYPE|Core|  
|SQL_ATTR_PARAM_OPERATION_PTR|Core|  
|SQL_ATTR_PARAM_STATUS_PTR|Core|  
|SQL_ATTR_PARAMS_PROCESSED_PTR|Core|  
|SQL_ATTR_PARAMSET_SIZE|Core|  
|SQL_ATTR_QUERY_TIMEOUT|Niveau 2|  
|SQL_ATTR_RETRIEVE_DATA|Niveau 1|  
|SQL_ATTR_ROW_ARRAY_SIZE|Core|  
|SQL_ATTR_ROW_BIND_OFFSET_PTR|Core|  
|SQL_ATTR_ROW_BIND_TYPE|Core|  
|SQL_ATTR_ROW_NUMBER|Niveau 1|  
|SQL_ATTR_ROW_OPERATION_PTR|Niveau 1|  
|SQL_ATTR_ROW_STATUS_PTR|Core|  
|SQL_ATTR_ROWS_FETCHED_PTR|Core|  
|SQL_ATTR_SIMULATE_CURSOR|Niveau 2|  
|SQL_ATTR_USE_BOOKMARKS|Niveau 2|  
  
 [1] les applications qui prennent en charge l’asynchronie au niveau de la connexion (requises pour le niveau 1) doivent prendre en charge la définition de cet attribut sur SQL_TRUE en appelant **SQLSetConnectAttr**; l’attribut n’a pas besoin d’être définissable à une valeur autre que sa valeur par défaut jusqu’à **SQLSetStmtAttr**. Les applications qui prennent en charge l’asynchronie au niveau des instructions (requises pour le niveau 2) doivent prendre en charge la définition de cet attribut sur SQL_TRUE à l’aide de l’une des fonctions.  
  
 [2] pour la conformité de l’interface de niveau 2, le pilote doit prendre en charge SQL_CONCUR_READ_ONLY et au moins une autre valeur.  
  
 [3] pour la conformité de l’interface de niveau 1, le pilote doit prendre en charge SQL_CURSOR_FORWARD_ONLY et au moins une autre valeur. Pour la conformité de l’interface de niveau 2, le pilote doit prendre en charge toutes les valeurs définies dans ce document.

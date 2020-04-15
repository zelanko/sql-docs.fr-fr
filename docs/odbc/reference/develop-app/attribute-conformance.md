---
title: Conformité d’attributs ( Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306400"
---
# <a name="attribute-conformance"></a>Conformité des attributs
Le tableau suivant indique le niveau de conformité de chaque attribut de l’environnement ODBC, où cela est bien défini.  
  
|Fonction|Niveau de conformité|  
|--------------|-----------------------|  
|SQL_ATTR_CONNECTION_POOLING|--[1]|  
|SQL_ATTR_CP_MATCH|--[1]|  
|SQL_ATTR_ODBC_VER|Core|  
|SQL_ATTR_OUTPUT_NTS|--[1]|  
  
 [1] Il s’agit d’une fonctionnalité facultative et en tant que telle ne fait pas partie des niveaux de conformité.  
  
 Le tableau suivant indique le niveau de conformité de chaque attribut de connexion ODBC, où cela est bien défini.  
  
|Fonction|Niveau de conformité|  
|--------------|-----------------------|  
|SQL_ATTR_ACCESS_MODE|Core|  
|SQL_ATTR_ASYNC_ENABLE|Niveau 1/Niveau 2[1]|  
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
|SQL_ATTR_TXN_ISOLATION|Niveau 1/Niveau 2[2]|  
  
 [1] Les applications qui prennent en charge l’asynchronie de niveau de connexion (requis pour le niveau 1) doivent prendre en charge le réglage de cet attribut à SQL_TRUE en appelant **SQLSetConnectAttr**; l’attribut n’a pas besoin d’être défini à une valeur autre que sa valeur par défaut par **SQLSetStmtAttr**. Les applications qui prennent en charge l’asynchronie au niveau des relevés (requis pour le niveau 2) doivent prendre en charge le réglage de cet attribut à SQL_TRUE l’utilisation de l’une ou l’autre fonction.  
  
 [2] Pour la conformité d’interface de niveau 1, le conducteur doit prendre en charge une valeur en plus de la valeur par défaut définie par le conducteur (disponible en appelant **SQLGetInfo** avec l’option SQL_DEFAULT_TXN_ISOLATION). Pour la conformité à l’interface de niveau 2, le conducteur doit également prendre en charge SQL_TXN_SERIALIZABLE.  
  
 Le tableau suivant indique le niveau de conformité de chaque attribut de relevé ODBC, où cela est bien défini.  
  
|Fonction|Niveau de conformité|  
|--------------|-----------------------|  
|SQL_ATTR_APP_PARAM_DESC|Core|  
|SQL_ATTR_APP_ROW_DESC|Core|  
|SQL_ATTR_ASYNC_ENABLE|Niveau 1/Niveau 2[1]|  
|SQL_ATTR_CONCURRENCY|Niveau 1/Niveau 2[2]|  
|SQL_ATTR_CURSOR_SCROLLABLE|Niveau 1|  
|SQL_ATTR_CURSOR_SENSITIVITY|Niveau 2|  
|SQL_ATTR_CURSOR_TYPE|Noyau/Niveau 2[3]|  
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
  
 [1] Les applications qui prennent en charge l’asynchronie de niveau de connexion (requis pour le niveau 1) doivent prendre en charge le réglage de cet attribut à SQL_TRUE en appelant **SQLSetConnectAttr**; l’attribut n’a pas besoin d’être défini à une valeur autre que sa valeur par défaut par **SQLSetStmtAttr**. Les applications qui prennent en charge l’asynchronie au niveau des relevés (requis pour le niveau 2) doivent prendre en charge le réglage de cet attribut à SQL_TRUE l’utilisation de l’une ou l’autre fonction.  
  
 [2] Pour la conformité d’interface de niveau 2, le conducteur doit prendre en charge SQL_CONCUR_READ_ONLY et au moins une autre valeur.  
  
 [3] Pour la conformité d’interface de niveau 1, le conducteur doit prendre en charge SQL_CURSOR_FORWARD_ONLY et au moins une autre valeur. Pour la conformité à l’interface de niveau 2, le conducteur doit prendre en charge toutes les valeurs définies dans ce document.

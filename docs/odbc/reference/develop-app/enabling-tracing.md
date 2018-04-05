---
title: L’activation du suivi | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tracing options [ODBC], enabling
ms.assetid: 48e318bd-2487-4708-a698-ea01f36a45e9
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 21f9d8b3d96f2860ed532279acc74ac3f7c717dc
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="enabling-tracing"></a>L’activation du traçage
Le suivi peut être activé dans le code suivant trois façons :  
  
-   Définir le **Trace** et **TraceFile** mots clés dans l’entrée de Registre Odbc.ini. Cela active ou désactive le suivi lorsque **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_ENV est appelée. Ces options sont définies dans l’onglet suivi de la boîte de dialogue Administrateur de sources de données ODBC affichée pendant l’installation de source de données. Pour plus d’informations, consultez [les entrées de Registre pour les Sources de données](../../../odbc/reference/install/registry-entries-for-data-sources.md).  
  
-   Appelez **SQLSetConnectAttr** pour définir l’attribut de connexion SQL_ATTR_TRACE à SQL_OPT_TRACE_ON. Cela active ou désactive le suivi pour la durée de la connexion. Pour plus d’informations, consultez la [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) description de fonction.  
  
-   Utilisez **ODBCSharedTraceFlag** pour activer ou désactiver le traçage dynamiquement. (Pour plus d’informations, consultez la rubrique suivante, [suivi dynamique](../../../odbc/reference/develop-app/dynamic-tracing.md).)

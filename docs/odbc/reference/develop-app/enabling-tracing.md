---
title: Activation du suivi | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- tracing options [ODBC], enabling
ms.assetid: 48e318bd-2487-4708-a698-ea01f36a45e9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 80bd4023a0260b67d11d7b4ded1bb810b81e0ab2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81287349"
---
# <a name="enabling-tracing"></a>Activation du traçage
Le suivi peut être activé des trois façons suivantes :  
  
-   Définissez les mots clés **trace** et **tracefile** dans l’entrée de Registre ODBC. ini. Cela active ou désactive le suivi quand **SQLAllocHandle** avec un *comme HandleType* de SQL_HANDLE_ENV est appelé. Ces options sont définies sous l’onglet suivi de la boîte de dialogue administrateur de sources de données ODBC affichée lors de la configuration de la source de données. Pour plus d’informations, consultez [entrées de Registre pour les sources de données](../../../odbc/reference/install/registry-entries-for-data-sources.md).  
  
-   Appelez **SQLSetConnectAttr** pour affecter à l’attribut de connexion SQL_ATTR_TRACE la valeur SQL_OPT_TRACE_ON. Cela active ou désactive le suivi pour la durée de la connexion. Pour plus d’informations, consultez la description de la fonction [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) .  
  
-   Utilisez **ODBCSharedTraceFlag** pour activer ou désactiver le suivi de manière dynamique. (Pour plus d’informations, consultez la rubrique suivante, [traçage dynamique](../../../odbc/reference/develop-app/dynamic-tracing.md).)

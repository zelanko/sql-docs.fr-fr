---
title: Permettre la traçabilité (en anglais) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287349"
---
# <a name="enabling-tracing"></a>Activation du traçage
Le traçage peut être activé de trois façons suivantes :  
  
-   Réglez les mots-clés **Trace** et **TraceFile** dans l’entrée du registre Odbc.ini. Cela permet ou désactive le traçage lorsque **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_ENV est appelé. Ces options sont définies dans l’onglet Tracing de la boîte de dialogue ODBC Data Source Administrator affichée lors de la configuration de la source de données. Pour plus d’informations, voir [Inscriptions de registre pour les sources de données](../../../odbc/reference/install/registry-entries-for-data-sources.md).  
  
-   Appelez **SQLSetConnectAttr** pour définir l’attribut de connexion SQL_ATTR_TRACE à SQL_OPT_TRACE_ON. Cela permet ou désactive le traçage pour la durée de la connexion. Pour plus d’informations, consultez la description de la fonction [SQLSetConnectAttr.](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)  
  
-   Utilisez **ODBCSharedTraceFlag** pour activer ou désactiver le traçage de façon dynamique. (Pour plus d’informations, voir le sujet suivant, [Dynamic Tracing](../../../odbc/reference/develop-app/dynamic-tracing.md).)

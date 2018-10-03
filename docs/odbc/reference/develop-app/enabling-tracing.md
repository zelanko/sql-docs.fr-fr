---
title: L’activation du suivi | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fb6d8eaf4a1f4eaadc4e8e9a7030b81c373d8377
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47819917"
---
# <a name="enabling-tracing"></a>Activation du traçage
Le suivi peut être activé dans le code suivant trois façons :  
  
-   Définir le **Trace** et **TraceFile** mots clés dans l’entrée de Registre du fichier Odbc.ini. Cela active ou désactive le suivi lorsque **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_ENV est appelée. Ces options sont définies dans l’onglet suivi de la boîte de dialogue Administrateur de sources de données ODBC affichée pendant l’installation de source de données. Pour plus d’informations, consultez [les entrées de Registre pour les Sources de données](../../../odbc/reference/install/registry-entries-for-data-sources.md).  
  
-   Appelez **SQLSetConnectAttr** à la valeur de l’attribut de connexion SQL_ATTR_TRACE SQL_OPT_TRACE_ON. Cela active ou désactive le suivi pour la durée de la connexion. Pour plus d’informations, consultez le [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) description de fonction.  
  
-   Utilisez **ODBCSharedTraceFlag** pour activer ou désactiver le suivi de manière dynamique. (Pour plus d’informations, consultez la rubrique suivante, [suivi dynamique](../../../odbc/reference/develop-app/dynamic-tracing.md).)

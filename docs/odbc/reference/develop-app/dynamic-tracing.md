---
title: Suivi dynamique | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- tracing options [ODBC], dynamic
- dynamic tracing [ODBC]
ms.assetid: ebe58a83-a7b0-4747-86c8-2af2940471ef
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d6746566d09d2862275daf508d08e20e2fca8473
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="dynamic-tracing"></a>Suivi dynamique
Le suivi peut être activé ou désactivé à tout moment dans une application de s’exécuter. Cela permet à une application à n’importe quel nombre d’appels de fonction de trace.  
  
 La variable **ODBCSharedTraceFlag** est défini pour activer le traçage de manière dynamique. Cette variable est partagée entre toutes les copies en cours d’exécution du Gestionnaire de pilotes. Si une application affecte à cette variable, le suivi est activé pour toutes les applications ODBC en cours d’exécution. Pour activer le suivi désactivé lorsque le suivi dynamique est activé, une application appelle **SQLSetConnectAttr** à la valeur SQL_ATTR_TRACE SQL_TRACE_OFF. Cet appel activer le suivi pour cette application uniquement. Les applications qui sont liées avec Odbc32.lib peuvent modifier l’utilisation de cette variable. Données de trace peuvent être affichées dans une fenêtre en temps réel, plutôt que le fichier de trace, qui doit être ouvert après la session ODBC. Contrôles peuvent être ajoutés à un écran de l’application pour activer le suivi ou désactiver sur sera.  
  
 La trace de la DLL est livré avec ODBC 3 *.x* n’est pas thread-safe. Il n’est pas garanti que le fichier journal est écrit correctement si le suivi global est activé (la variable **ODBCSharedTraceFlag** est défini) et plus d’une application écrit dans le fichier de trace en même temps. Cette condition ne retourne pas d’erreur.

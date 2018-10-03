---
title: Traçage dynamique | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- tracing options [ODBC], dynamic
- dynamic tracing [ODBC]
ms.assetid: ebe58a83-a7b0-4747-86c8-2af2940471ef
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 63dbfda01d96cad53e5830e598b5812ed79d8f04
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47661742"
---
# <a name="dynamic-tracing"></a>Traçage dynamique
Le suivi peut être activé ou désactivé à tout moment dans une exécution de l’application. Cela permet à une application effectuer le suivi de n’importe quel nombre d’appels de fonction.  
  
 La variable **ODBCSharedTraceFlag** est défini pour activer le traçage de manière dynamique. Cette variable est partagée entre toutes les copies en cours d’exécution du Gestionnaire de pilotes. Si n’importe quelle application affecte à cette variable, le traçage est activé pour toutes les applications ODBC en cours d’exécution. Pour activer le suivi désactivé lorsque le traçage dynamique est activé, une application appelle **SQLSetConnectAttr** à la valeur SQL_ATTR_TRACE SQL_TRACE_OFF. Cet appel désactive le suivi pour cette application uniquement. Les applications qui sont liées avec Odbc32.lib peuvent modifier l’utilisation de cette variable. Les données de trace peuvent être affichées dans une fenêtre en temps réel, au lieu du fichier de trace, qui doit être ouvert après la session ODBC. Contrôles peuvent être ajoutés à un écran de l’application pour activer le suivi activé ou désactivé sur sera.  
  
 La trace de la DLL livré avec ODBC 3 *.x* n’est pas thread-safe. Il n’est pas garanti que le fichier journal est écrit correctement si le suivi global est activé (la variable **ODBCSharedTraceFlag** est défini) et plus d’une application écrit dans le fichier de trace en même temps. Cette condition ne retourne pas d’erreur.

---
description: Traçage dynamique
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a1618d1b2837c5169f03b07900aba3921bc98659
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482992"
---
# <a name="dynamic-tracing"></a>Traçage dynamique
Le suivi peut être activé ou désactivé à tout moment de l’exécution d’une application. Cela permet à une application d’effectuer le suivi de n’importe quel nombre d’appels de fonction.  
  
 La variable **ODBCSharedTraceFlag** est définie pour activer le suivi dynamique. Cette variable est partagée entre toutes les copies en cours d’exécution du gestionnaire de pilotes. Si une application définit cette variable, le suivi est activé pour toutes les applications ODBC en cours d’exécution. Pour désactiver le traçage lorsque le traçage dynamique est activé, une application appelle **SQLSetConnectAttr** pour définir SQL_ATTR_TRACE sur SQL_TRACE_OFF. Cet appel active le suivi pour cette application uniquement. Les applications qui sont liées à Odbc32. lib peuvent modifier l’utilisation de cette variable. Les données de trace peuvent être affichées dans une fenêtre en temps réel, au lieu du fichier de trace, qui doit être ouvert après la session ODBC. Des contrôles peuvent être ajoutés à l’écran d’une application pour activer ou désactiver le suivi à la demande.  
  
 La DLL de trace fournie avec ODBC 3 *. x* n’est pas thread-safe. Il n’est pas garanti que le fichier journal est écrit correctement si le suivi global est activé (la variable **ODBCSharedTraceFlag** est définie) et que plusieurs applications écrivent dans le fichier de trace en même temps. Cette condition ne retourne pas d’erreur.

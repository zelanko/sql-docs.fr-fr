---
title: Traçage dynamique (en anglais) Microsoft Docs
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
ms.openlocfilehash: 8cbd2dbae4f4b437f45845ce2791f4a9b0aa8c8b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305764"
---
# <a name="dynamic-tracing"></a>Traçage dynamique
Le traçage peut être activé ou désactivé à tout moment d’une application. Cela permet à une application de retracer n’importe quel nombre d’appels de fonction.  
  
 La variable **ODBCSharedTraceFlag** est définie pour permettre le traçage dynamique. Cette variable est partagée entre toutes les copies en cours d’exécution du Driver Manager. Si une application définit cette variable, le traçage est activé pour toutes les applications ODBC actuellement en cours d’exécution. Pour désactiver le traçage lorsque le traçage dynamique est activé, une application appelle **SQLSetConnectAttr** pour régler SQL_ATTR_TRACE à SQL_TRACE_OFF. Cet appel désactivera le traçage de cette application uniquement. Les applications qui sont liées à Odbc32.lib peuvent modifier l’utilisation de cette variable. Les données de trace peuvent être affichées dans une fenêtre en temps réel, au lieu du fichier de trace, qui doit être ouvert après la session ODBC. Les contrôles peuvent être ajoutés à l’écran d’une application pour activer ou désactiver le tracé à volonté.  
  
 La trace DLL expédiée avec ODBC 3 *.x* n’est pas sans fil. Il n’est pas garanti que le fichier journal est écrit correctement si le traçage global est activé (la variable **ODBCSharedTraceFlag** est définie) et plus d’une application écrit au fichier de traçage en même temps. Cette condition ne renvoie pas une erreur.

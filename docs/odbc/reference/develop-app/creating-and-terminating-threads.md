---
description: Création et arrêt des threads
title: Création et arrêt des threads | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- terminating threads [ODBC]
- threads [ODBC]
- multithreaded applications [ODBC]
ms.assetid: a2cf98ef-1c71-4742-8ee2-b53fd8e04333
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c0100b85bc596149d809dee7e6c4cb3547dbd081
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465851"
---
# <a name="creating-and-terminating-threads"></a>Création et arrêt des threads
Les applications multithread qui utilisent ODBC doivent appeler les fonctions de la bibliothèque Runtime de Microsoft® Visual C++® **_beginthread** et **_endthread** (ou **_beginthreadex** et **_endthreadex) pour**créer et arrêter des threads qui appellent le gestionnaire de pilotes ODBC. Si les applications appellent Microsoft Windows NT® Functions **CreateThread** et **EndThread** à la place, des fuites de mémoire se produisent car le gestionnaire de pilotes et certains pilotes ODBC appellent des fonctions runtime C qui ne fonctionnent pas sur un thread créé en appelant **CreateThread**. Pour plus d’informations, consultez la documentation de Microsoft Windows®.

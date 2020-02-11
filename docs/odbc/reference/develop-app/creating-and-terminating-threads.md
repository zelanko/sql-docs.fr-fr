---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b97f29ad06c4ed961f3cee571b0ca7b8d9c0b774
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68002083"
---
# <a name="creating-and-terminating-threads"></a>Création et arrêt des threads
Les applications multithread qui utilisent ODBC doivent appeler les fonctions de la bibliothèque Runtime de Microsoft® Visual C++® **_beginthread** et **_endthread** (ou **_beginthreadex** et **_endthreadex) pour**créer et arrêter des threads qui appellent le gestionnaire de pilotes ODBC. Si les applications appellent Microsoft Windows NT® Functions **CreateThread** et **EndThread** à la place, des fuites de mémoire se produisent car le gestionnaire de pilotes et certains pilotes ODBC appellent des fonctions runtime C qui ne fonctionnent pas sur un thread créé en appelant **CreateThread**. Pour plus d’informations, consultez la documentation de Microsoft Windows®.

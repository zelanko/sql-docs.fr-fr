---
title: "Création et arrêter des Threads | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- terminating threads [ODBC]
- threads [ODBC]
- multithreaded applications [ODBC]
ms.assetid: a2cf98ef-1c71-4742-8ee2-b53fd8e04333
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 62950dba2174baac8e3bc34c60f268e07304fa5a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="creating-and-terminating-threads"></a>Création et arrêter des Threads
Les applications multithread qui utilisent ODBC doivent appeler les fonctions de la bibliothèque Runtime de Microsoft® Visual C++® **_beginthread** et **_endthread** (ou **_beginthreadex** et **_endthreadex**) pour créer et terminer des threads qui appellent le Gestionnaire de pilotes ODBC. Si les applications appellent les fonctions Microsoft Windows NT® **CreateThread** et **EndThread** au lieu de cela, mémoire fuites seront produit, car le Gestionnaire de pilotes et certains pilotes ODBC appellent les fonctions runtime C qui ne fonctionnera pas sur un thread créé par l’appel **CreateThread**. Pour plus d’informations, consultez la documentation de Microsoft Windows®.

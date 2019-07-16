---
title: Création et arrêt des Threads | Microsoft Docs
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68002083"
---
# <a name="creating-and-terminating-threads"></a>Création et arrêt des threads
Les applications multithread qui utilisent ODBC doivent appeler le Visual Microsoft® C++® les fonctions de bibliothèque du Run-Time **_beginthread** et **_endthread** (ou **_beginthreadex**et **_endthreadex**) pour créer et terminer des threads qui appellent le Gestionnaire de pilotes ODBC. Si les applications appellent les fonctions Microsoft Windows NT® **CreateThread** et **EndThread** au lieu de cela, les fuites se produira, car le Gestionnaire de pilotes et certains pilotes ODBC appellent Runtime C de mémoire les fonctions ne fonctionnera pas sur un thread créé en appelant **CreateThread**. Pour plus d’informations, consultez la documentation de Microsoft Windows®.

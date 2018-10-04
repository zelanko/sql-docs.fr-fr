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
manager: craigg
ms.openlocfilehash: e9d6d15c449d88043e844addd12ac10a98d5c4a0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47722377"
---
# <a name="creating-and-terminating-threads"></a>Création et arrêt des threads
Les applications multithread qui utilisent ODBC doivent appeler les fonctions de Microsoft® Visual C++® Run-Time Library **_beginthread** et **_endthread** (ou **_beginthreadex** et **_endthreadex**) pour créer et terminer des threads qui appellent le Gestionnaire de pilotes ODBC. Si les applications appellent les fonctions Microsoft Windows NT® **CreateThread** et **EndThread** au lieu de cela, les fuites se produira, car le Gestionnaire de pilotes et certains pilotes ODBC appellent Runtime C de mémoire les fonctions ne fonctionnera pas sur un thread créé en appelant **CreateThread**. Pour plus d’informations, consultez la documentation de Microsoft Windows®.

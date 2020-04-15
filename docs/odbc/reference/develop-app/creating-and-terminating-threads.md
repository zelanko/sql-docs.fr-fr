---
title: Création et Terminating Threads (fr) Microsoft Docs
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
ms.openlocfilehash: 3536deef604d7dbf645903e7d171a58cd9fec96a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301690"
---
# <a name="creating-and-terminating-threads"></a>Création et arrêt des threads
Les applications multitâles qui utilisent ODBC devraient appeler les fonctions Microsoft® Visual C-® Run-Time Library **_beginthread** et **_endthread** (ou **_beginthreadex** et **_endthreadex)** pour créer et mettre fin aux threads qui appellent le gestionnaire de pilote ODBC. Si les applications appellent les fonctions Microsoft Windows NT® **CreateThread** et **EndThread** à la place, des fuites de mémoire se produiront parce que le Driver Manager et certains pilotes ODBC appellent C fonctions de temps d’exécution qui ne fonctionnera pas sur un thread créé en appelant **CreateThread**. Pour plus d’informations, consultez la documentation Microsoft Windows®.

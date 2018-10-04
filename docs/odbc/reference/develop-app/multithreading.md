---
title: Le multithreading | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], thread-safe
- thread-safe drivers [ODBC]
- multithreaded applications [ODBC]
ms.assetid: cdfebdf5-12ff-4e28-8055-41f49b77f664
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a16262d562ca2088f38cd863a6f44e537e65d40
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47622167"
---
# <a name="multithreading"></a>Multithreading
Sur les systèmes d’exploitation multithread, les pilotes doivent être thread-safe. Autrement dit, il doit être possible pour les applications d’utiliser le même handle sur plusieurs threads. Cette opération est spécifique au pilote, et il est probable que les pilotes sérialisera toute tentative d’utiliser simultanément le même handle sur deux threads différents.  
  
 Les applications utilisent souvent plusieurs threads au lieu de traitement asynchrone. L’application crée un thread distinct, appelle une fonction ODBC sur ce dernier, puis continue le traitement sur le thread principal. Plutôt que d’interroger continuellement la fonction asynchrone, comme c’est le cas lorsque l’attribut d’instruction SQL_ATTR_ASYNC_ENABLE est utilisé, l’application peut simplement laissez le thread nouvellement créé.  
  
 Les fonctions qui acceptent un descripteur d’instruction et en cours d’exécution sur un thread peuvent être annulées en appelant **SQLCancel** avec la même instruction gérer à partir d’un autre thread. Bien que les pilotes ne doivent pas sérialiser l’utilisation de **SQLCancel** de cette manière, il n’existe aucune garantie que l’appel **SQLCancel** annule réellement la fonction en cours d’exécution sur l’autre thread.

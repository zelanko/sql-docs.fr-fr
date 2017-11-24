---
title: Multithreading | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC drivers [ODBC], thread-safe
- thread-safe drivers [ODBC]
- multithreaded applications [ODBC]
ms.assetid: cdfebdf5-12ff-4e28-8055-41f49b77f664
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 86ef8e539354dce2d0cd349d75053b05a7ca59ca
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="multithreading"></a>Le multithreading
Sur les systèmes d’exploitation multithread, les pilotes doivent être thread-safe. Autrement dit, il doit être possible pour les applications utiliser le même handle sur plusieurs threads. La procédure est spécifique au pilote, et il est probable que les pilotes sérialisera toute tentative d’utiliser simultanément le même handle sur deux threads différents.  
  
 Applications Azure utilisent habituellement plusieurs threads à la place le traitement asynchrone. L’application crée un thread séparé, il appelle une fonction ODBC, puis continue le traitement sur le thread principal. Au lieu de devoir interroger continuellement la fonction asynchrone, comme c’est le cas lorsque l’attribut d’instruction SQL_ATTR_ASYNC_ENABLE est utilisé, l’application peut simplement laisser le nouveau thread se terminer.  
  
 Les fonctions qui acceptent un descripteur d’instruction et qui sont en cours d’exécution sur un thread peuvent être annulées en appelant **SQLCancel** avec la même instruction gérer à partir d’un autre thread. Bien que les pilotes ne doivent pas sérialiser l’utilisation de **SQLCancel** de cette manière, il n’existe aucune garantie que l’appel **SQLCancel** annule effectivement la fonction en cours d’exécution sur l’autre thread.

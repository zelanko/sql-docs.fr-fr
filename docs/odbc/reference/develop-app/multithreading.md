---
title: Multithreading (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c10d1b401ac780d24184c4c2337199e99973e916
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302413"
---
# <a name="multithreading"></a>Multithreading
Sur les systèmes d’exploitation multimarlits, les pilotes doivent être sans fil. Autrement dit, il doit être possible pour les applications d’utiliser la même poignée sur plus d’un thread. La façon dont cela est réalisé est spécifique au conducteur, et il est probable que les pilotes sérialiser toutes les tentatives d’utiliser simultanément la même poignée sur deux threads différents.  
  
 Les applications utilisent généralement plusieurs threads au lieu d’un traitement asynchrone. L’application crée un thread séparé, appelle une fonction ODBC sur elle, puis continue le traitement sur le thread principal. Plutôt que d’avoir à sonder continuellement la fonction asynchrone, comme c’est le cas lorsque l’attribut de l’SQL_ATTR_ASYNC_ENABLE déclaration est utilisé, l’application peut simplement laisser le fil nouvellement créé terminer.  
  
 Les fonctions qui acceptent une poignée de déclaration et sont en cours d’exécution sur un thread peuvent être annulées en appelant **SQLCancel** avec la même poignée de déclaration à partir d’un autre thread. Bien que les conducteurs ne devraient pas sérialiser l’utilisation de **SQLCancel** de cette manière, il n’y a aucune garantie que l’appel **SQLCancel** sera effectivement annuler la fonction en cours d’exécution sur l’autre thread.

---
description: Multithreading
title: Multithread | Microsoft Docs
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
ms.openlocfilehash: 470a3d3a4d76ae038e3c80b9aa9b93dfd1d0ed79
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429241"
---
# <a name="multithreading"></a>Multithreading
Sur les systèmes d’exploitation multithread, les pilotes doivent être thread-safe. Autrement dit, les applications doivent être en mesure d’utiliser le même handle sur plusieurs threads. Cette opération est spécifique au pilote, et il est probable que les pilotes sérialisent les tentatives d’utilisation simultanée du même handle sur deux threads différents.  
  
 Les applications utilisent généralement plusieurs threads au lieu d’un traitement asynchrone. L’application crée un thread distinct, appelle une fonction ODBC sur celle-ci, puis continue le traitement sur le thread principal. Plutôt que d’avoir à interroger continuellement la fonction asynchrone, comme c’est le cas lorsque l’attribut d’instruction SQL_ATTR_ASYNC_ENABLE est utilisé, l’application peut simplement laisser le thread nouvellement créé se terminer.  
  
 Les fonctions qui acceptent un descripteur d’instruction et qui s’exécutent sur un thread peuvent être annulées en appelant **SQLCancel** avec le même descripteur d’instruction d’un autre thread. Bien que les pilotes ne doivent pas sérialiser l’utilisation de **SQLCancel** de cette manière, il n’est pas garanti que l’appel de **SQLCancel** annulera en fait la fonction en cours d’exécution sur l’autre thread.

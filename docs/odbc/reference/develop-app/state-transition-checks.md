---
title: "Vérifications de la Transition d’état | Documents Microsoft"
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
- diagnostic information [ODBC], driver manager error checking
- state transition checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 0706db7d-e125-4845-a13a-7fe4308f7360
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b3e69167072663f2fa4e2aea0e13611f5cf15cd8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="state-transition-checks"></a>Vérifications de la Transition d’état
Le Gestionnaire de pilotes vérifie que l’état de l’environnement, une connexion ou une instruction est approprié pour la fonction appelée. Par exemple, une connexion doit être dans un alloué état lorsque **SQLConnect** est appelé ; une instruction doit être dans la préparation d’une état lorsque **SQLExecute** est appelée. Le Gestionnaire de pilotes retourne SQL_ERROR pour les erreurs de transition d’état.

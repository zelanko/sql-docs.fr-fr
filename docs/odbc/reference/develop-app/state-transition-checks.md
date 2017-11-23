---
title: "Vérifications de la Transition d’état | Documents Microsoft"
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
- diagnostic information [ODBC], driver manager error checking
- state transition checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 0706db7d-e125-4845-a13a-7fe4308f7360
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0d6c33118d108c4a4c9e541db311710202cabdb3
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="state-transition-checks"></a>Vérifications de la Transition d’état
Le Gestionnaire de pilotes vérifie que l’état de l’environnement, une connexion ou une instruction est approprié pour la fonction appelée. Par exemple, une connexion doit être dans un alloué état lorsque **SQLConnect** est appelé ; une instruction doit être dans la préparation d’une état lorsque **SQLExecute** est appelée. Le Gestionnaire de pilotes retourne SQL_ERROR pour les erreurs de transition d’état.

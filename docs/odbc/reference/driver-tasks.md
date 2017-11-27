---
title: "Tâches de pilote | Documents Microsoft"
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
- ODBC architecture [ODBC], drivers
- drivers [ODBC], tasks
ms.assetid: 184c795a-c2e8-4d20-9902-12e60b2f0e45
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e814f2780baecee5c33edd38f6def2f30abafddd
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="driver-tasks"></a>Tâches de pilote
Les tâches spécifiques effectuées par les pilotes sont les suivantes :  
  
-   Connexion et déconnexion de la source de données.  
  
-   Vérification des erreurs de fonction ne pas vérifiées par le Gestionnaire de pilotes.  
  
-   Transactions de l’initiateur ; Ceci est transparent pour l’application.  
  
-   Envoi de la source de données pour l’exécution d’instructions SQL. Le pilote doit modifier SQL ODBC à propres au SGBD SQL ; Cela est souvent limitée à des clauses d’échappement définis par ODBC avec propres au SGBD SQL de remplacement.  
  
-   Envoie des données et la récupération des données à partir de la source de données, notamment la conversion des types de données comme spécifié par l’application.  
  
-   Mappage des erreurs spécifiques au SGBD sur SQLSTATE de ODBC.

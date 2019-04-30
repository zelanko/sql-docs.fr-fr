---
title: Tâches des pilotes | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], drivers
- drivers [ODBC], tasks
ms.assetid: 184c795a-c2e8-4d20-9902-12e60b2f0e45
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ee695c62fc60b2ebb0ae9bb33ef9008ba617b49a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63254144"
---
# <a name="driver-tasks"></a>Tâches des pilotes
Les tâches spécifiques effectuées par les pilotes sont les suivantes :  
  
-   Connexion et déconnexion à partir de la source de données.  
  
-   Vérification des erreurs de fonction ne pas vérifiées par le Gestionnaire de pilotes.  
  
-   Transactions de l’initiateur ; Cela est transparent pour l’application.  
  
-   Envoi de la source de données pour l’exécution d’instructions SQL. Le pilote doit modifier SQL ODBC à SQL de SGBD spécifiques ; Cela est souvent limité à en remplaçant les clauses d’échappement définis par ODBC avec propres au SGBD SQL.  
  
-   Envoie des données et la récupération des données à partir de la source de données, notamment la conversion en types de données comme spécifié par l’application.  
  
-   Erreurs de mappage de SGBD spécifiques à SQLSTATE de ODBC.

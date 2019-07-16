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
ms.openlocfilehash: 2e2ed50ac3f9e914953abdd64907199a5f978af2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67915459"
---
# <a name="driver-tasks"></a>Tâches des pilotes
Les tâches spécifiques effectuées par les pilotes sont les suivantes :  
  
-   Connexion et déconnexion à partir de la source de données.  
  
-   Vérification des erreurs de fonction ne pas vérifiées par le Gestionnaire de pilotes.  
  
-   Transactions de l’initiateur ; Cela est transparent pour l’application.  
  
-   Envoi de la source de données pour l’exécution d’instructions SQL. Le pilote doit modifier SQL ODBC à SQL de SGBD spécifiques ; Cela est souvent limité à en remplaçant les clauses d’échappement définis par ODBC avec propres au SGBD SQL.  
  
-   Envoie des données et la récupération des données à partir de la source de données, notamment la conversion en types de données comme spécifié par l’application.  
  
-   Erreurs de mappage de SGBD spécifiques à SQLSTATE de ODBC.

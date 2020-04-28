---
title: Tâches du pilote | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1b30df63a3c955d2ed074ab13649ea55c21a6da7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81294199"
---
# <a name="driver-tasks"></a>Tâches des pilotes
Les tâches spécifiques effectuées par les pilotes sont les suivantes :  
  
-   Connexion à la source de données et déconnexion de celle-ci.  
  
-   Recherche des erreurs de fonction non vérifiées par le gestionnaire de pilotes.  
  
-   Lancement des transactions ; Cela est transparent pour l’application.  
  
-   Envoi d’instructions SQL à la source de données pour exécution. Le pilote doit modifier le SQL ODBC en SQL spécifique au SGBD. Cela est souvent limité au remplacement de clauses d’échappement définies par ODBC avec un SQL spécifique au SGBD.  
  
-   Envoi et récupération de données à partir de la source de données, y compris la conversion des types de données tels que spécifiés par l’application.  
  
-   Mappage des erreurs spécifiques au SGBD aux SQLSTATE ODBC.

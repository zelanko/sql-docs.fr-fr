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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2e2ed50ac3f9e914953abdd64907199a5f978af2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67915459"
---
# <a name="driver-tasks"></a>Tâches des pilotes
Les tâches spécifiques effectuées par les pilotes sont les suivantes :  
  
-   Connexion à la source de données et déconnexion de celle-ci.  
  
-   Recherche des erreurs de fonction non vérifiées par le gestionnaire de pilotes.  
  
-   Lancement des transactions ; Cela est transparent pour l’application.  
  
-   Envoi d’instructions SQL à la source de données pour exécution. Le pilote doit modifier le SQL ODBC en SQL spécifique au SGBD. Cela est souvent limité au remplacement de clauses d’échappement définies par ODBC avec un SQL spécifique au SGBD.  
  
-   Envoi et récupération de données à partir de la source de données, y compris la conversion des types de données tels que spécifiés par l’application.  
  
-   Mappage des erreurs spécifiques au SGBD aux SQLSTATE ODBC.

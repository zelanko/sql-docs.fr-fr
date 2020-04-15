---
title: Tâches de conducteur Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294199"
---
# <a name="driver-tasks"></a>Tâches des pilotes
Les tâches spécifiques effectuées par les conducteurs comprennent :  
  
-   Se connecter et se déconnecter de la source de données.  
  
-   Vérification des erreurs de fonction non vérifiées par le gestionnaire de pilote.  
  
-   Lancer des transactions; cela est transparent pour l’application.  
  
-   Soumettre des relevés SQL à la source de données pour exécution. Le conducteur doit modifier ODBC SQL en SQL spécifique à DBMS; cela se limite souvent au remplacement des clauses d’évacuation définies par ODBC par SQL spécifique à DBMS.  
  
-   Envoi de données et récupération de données à partir de la source de données, y compris la conversion des types de données spécifiés par l’application.  
  
-   Cartographier les erreurs spécifiques à DBMS aux SQLSTATes DDBC.

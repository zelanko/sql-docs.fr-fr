---
title: "La récupération des signets | Documents Microsoft"
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
- retrieving bookmarks [ODBC]
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
ms.assetid: a34c8f09-b786-4835-a44b-b7294c970aff
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bb71f5ce4b60a133d600367086cdf73c02a61461
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="retrieving-bookmarks"></a>La récupération des signets
Si l’application utilise des signets, il doit définir l’attribut d’instruction SQL_ATTR_USE_BOOKMARKS à SQL_UB_VARIABLE avant la préparation ou l’exécution de l’instruction. Cela est nécessaire, car les créer et gérer des signets peuvent être une opération coûteuse, signets doivent être activés uniquement lorsqu’une application peut faire une bonne de les utilisent.  
  
 Les signets sont retournés en tant que colonne 0 du jeu de résultats. Il existe trois façons qu'une application peut récupérer les :  
  
-   Lier la colonne 0 du jeu de résultats. **SQLFetch** ou **SQLFetchScroll** renvoie les signets pour chaque ligne dans l’ensemble de lignes, ainsi que les données pour d’autres colonnes.  
  
-   Appelez **SQLSetPos** pour vous positionner sur une ligne dans l’ensemble de lignes, puis appelez **SQLGetData** pour la colonne 0. Si un pilote prend en charge les signets, il doit toujours prendre en charge la possibilité d’appeler **SQLGetData** pour la colonne 0, même si elle n’autorise pas les applications d’appeler **SQLGetData** pour d’autres colonnes avant la dernière colonne dépendante.  
  
-   Appelez **SQLBulkOperations** avec la *opération* SQL_ADD à l’argument et lié à la colonne 0. Le curseur insère la ligne et retourne le signet pour la ligne dans la mémoire tampon liée.

---
title: Signets (ODBC) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
ms.assetid: 1d7cccc5-f847-4321-b240-28570854ee5c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 70b260e422276c4a833f05d4b74c009eddfb5119
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="bookmarks-odbc"></a>Signets (ODBC)
Un signet est une valeur utilisée pour identifier une ligne de données. La signification de la valeur du signet est connue uniquement du pilote ou de la source de données. Par exemple, il peut être aussi simple qu'un numéro de ligne ou aussi complexe qu'une adresse disque. Les signets dans ODBC sont légèrement différentes à partir de signets dans la documentation réelle. Dans un livre réel, le lecteur place un signet dans une page spécifique, puis recherche ce signet revenir à la page. Dans ODBC, l'application demande un signet pour une ligne particulière, le stocke, puis le passe au curseur à retourner à la ligne. Par conséquent, les signets dans ODBC sont similaires à un lecteur de l’écriture vers le bas un numéro de page, rappeler, puis en consultant la page à nouveau.  
  
 Pour déterminer la prise en charge d’un pilote de signets, une application appelle **SQLGetInfo** avec l’option SQL_BOOKMARK_PERSISTENCE. Les bits de cette valeur décrivent ce qui survivent signets d’opérations, telles que si les signets sont toujours valides une fois que le curseur est fermé.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Types de signets](../../../odbc/reference/develop-app/bookmark-types.md)  
  
-   [Récupération des signets](../../../odbc/reference/develop-app/retrieving-bookmarks.md)  
  
-   [Défilement par signet](../../../odbc/reference/develop-app/scrolling-by-bookmark.md)  
  
-   [Mise à jour, suppression ou extraction par signet](../../../odbc/reference/develop-app/updating-deleting-or-fetching-by-bookmark.md)  
  
-   [Comparaison de signets](../../../odbc/reference/develop-app/comparing-bookmarks.md)

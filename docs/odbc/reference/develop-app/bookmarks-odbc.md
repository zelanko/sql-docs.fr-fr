---
title: Bookmarks (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
ms.assetid: 1d7cccc5-f847-4321-b240-28570854ee5c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9eecd202a17a0a08e8607ebec0caaa31b7b3ca9c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199208"
---
# <a name="bookmarks-odbc"></a>Signets (ODBC)
Un signet est une valeur utilisée pour identifier une ligne de données. La signification de la valeur du signet est connue uniquement du pilote ou de la source de données. Par exemple, il peut être aussi simple qu'un numéro de ligne ou aussi complexe qu'une adresse disque. Les signets dans ODBC sont légèrement différentes des signets dans la documentation réelle. Dans un livre réel, le lecteur place un signet à une page spécifique et recherche de signet revenir à la page. Dans ODBC, l'application demande un signet pour une ligne particulière, le stocke, puis le passe au curseur à retourner à la ligne. Par conséquent, les signets dans ODBC sont similaires à un lecteur écrivant un numéro de page, de rappeler, puis en consultant la page à nouveau.  
  
 Pour déterminer la prise en charge d’un pilote de signets, une application appelle **SQLGetInfo** avec l’option SQL_BOOKMARK_PERSISTENCE. Les bits de cette valeur de décrivent ce qui survivent signets d’opérations, telles que si les signets sont toujours valides une fois que le curseur est fermé.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Types de signets](../../../odbc/reference/develop-app/bookmark-types.md)  
  
-   [Récupération des signets](../../../odbc/reference/develop-app/retrieving-bookmarks.md)  
  
-   [Défilement par signet](../../../odbc/reference/develop-app/scrolling-by-bookmark.md)  
  
-   [Mise à jour, suppression ou extraction par signet](../../../odbc/reference/develop-app/updating-deleting-or-fetching-by-bookmark.md)  
  
-   [Comparaison de signets](../../../odbc/reference/develop-app/comparing-bookmarks.md)

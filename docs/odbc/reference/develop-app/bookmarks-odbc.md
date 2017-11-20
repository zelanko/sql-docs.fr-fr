---
title: Signets (ODBC) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
ms.assetid: 1d7cccc5-f847-4321-b240-28570854ee5c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 791350c93e2570ad8615e5b378e9979870e02acf
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="bookmarks-odbc"></a>Signets (ODBC)
Un signet est une valeur utilisée pour identifier une ligne de données. La signification de la valeur du signet est connue uniquement du pilote ou de la source de données. Par exemple, il peut être aussi simple qu'un numéro de ligne ou aussi complexe qu'une adresse disque. Les signets dans ODBC sont légèrement différentes à partir de signets dans la documentation réelle. Dans un livre réel, le lecteur place un signet dans une page spécifique, puis recherche ce signet revenir à la page. Dans ODBC, l'application demande un signet pour une ligne particulière, le stocke, puis le passe au curseur à retourner à la ligne. Par conséquent, les signets dans ODBC sont similaires à un lecteur de l’écriture vers le bas un numéro de page, rappeler, puis en consultant la page à nouveau.  
  
 Pour déterminer la prise en charge d’un pilote de signets, une application appelle **SQLGetInfo** avec l’option SQL_BOOKMARK_PERSISTENCE. Les bits de cette valeur décrivent ce qui survivent signets d’opérations, telles que si les signets sont toujours valides une fois que le curseur est fermé.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Types de signet](../../../odbc/reference/develop-app/bookmark-types.md)  
  
-   [La récupération des signets](../../../odbc/reference/develop-app/retrieving-bookmarks.md)  
  
-   [Le défilement par un signet](../../../odbc/reference/develop-app/scrolling-by-bookmark.md)  
  
-   [Mise à jour, la suppression ou l’extraction par le signet](../../../odbc/reference/develop-app/updating-deleting-or-fetching-by-bookmark.md)  
  
-   [Comparaison des signets](../../../odbc/reference/develop-app/comparing-bookmarks.md)


---
description: Signets (ODBC)
title: Signets (ODBC) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3f162fc317f2651549a1a2e80af03c9942dc64bb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461611"
---
# <a name="bookmarks-odbc"></a>Signets (ODBC)
Un signet est une valeur utilisée pour identifier une ligne de données. La signification de la valeur du signet est connue uniquement du pilote ou de la source de données. Par exemple, il peut être aussi simple qu'un numéro de ligne ou aussi complexe qu'une adresse disque. Dans ODBC, les signets diffèrent légèrement des signets dans les livres réels. Dans un livre réel, le lecteur place un signet sur une page spécifique, puis recherche ce signet pour revenir à la page. Dans ODBC, l'application demande un signet pour une ligne particulière, le stocke, puis le passe au curseur à retourner à la ligne. Ainsi, les signets dans ODBC sont similaires à ceux d’un lecteur qui écrivent un numéro de page, le mémorise, puis rerecherchent la page.  
  
 Pour déterminer la prise en charge des signets par un pilote, une application appelle **SQLGetInfo** avec l’option SQL_BOOKMARK_PERSISTENCE. Les bits de cette valeur décrivent ce que les signets d’opérations survivent, par exemple si les signets sont toujours valides après la fermeture du curseur.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Types de signets](../../../odbc/reference/develop-app/bookmark-types.md)  
  
-   [Récupération des signets](../../../odbc/reference/develop-app/retrieving-bookmarks.md)  
  
-   [Défilement par signet](../../../odbc/reference/develop-app/scrolling-by-bookmark.md)  
  
-   [Mise à jour, suppression ou extraction par signet](../../../odbc/reference/develop-app/updating-deleting-or-fetching-by-bookmark.md)  
  
-   [Comparaison de signets](../../../odbc/reference/develop-app/comparing-bookmarks.md)

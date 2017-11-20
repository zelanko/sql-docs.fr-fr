---
title: "À l’aide de curseurs de bloc | Documents Microsoft"
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
- cursors [ODBC], block
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 2aad7d6b-216e-47e7-b3cb-f95ad096f21a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 51f02b5b243286a650897fecdcac5d8778bd3f40
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="using-block-cursors"></a>À l’aide de curseurs de bloc
Prise en charge pour les curseurs de bloc est intégrée dans ODBC 3. *x*. **SQLFetch** peut être utilisé uniquement pour les extractions multilignes lorsqu’elle est appelée dans ODBC 3. *x*; si une application ODBC 2. *x* application appelle **SQLFetch**, elle s’ouvre uniquement un curseur avant uniquement en ligne unique. Lorsqu’une application ODBC 3. *x* application appelle **SQLFetch** dans une API ODBC 2. *x* pilote, elle retourne une ligne unique, sauf si le pilote prend en charge **SQLExtendedFetch**. Pour plus d’informations, consultez [curseurs de bloc, les curseurs permettant le défilement et la compatibilité descendante](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) dans l’annexe g : pilote recommandations pour la compatibilité descendante.  
  
 Pour utiliser les curseurs de bloc, l’application définit la taille de l’ensemble de lignes, lie les mémoires tampons d’ensemble de lignes (comme décrit dans la section précédente), si vous le souhaitez définit les attributs d’instruction SQL_ATTR_ROWS_FETCHED_PTR et SQL_ATTR_ROW_STATUS_PTR et appels **SQLFetch** ou **SQLFetchScroll** pour extraire un bloc de lignes. L’application peut modifier la taille de l’ensemble de lignes et de lier le nouvel ensemble de lignes tampons (en appelant **SQLBindCol** ou en spécifiant un décalage de liaison) même après que les lignes qui ont été extraites.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Taille de l’ensemble de lignes](../../../odbc/reference/develop-app/rowset-size.md)  
  
-   [Nombre de lignes extraites et l’état](../../../odbc/reference/develop-app/number-of-rows-fetched-and-status.md)  
  
-   [SQLGetData et les curseurs de bloc ; bloc curso](../../../odbc/reference/develop-app/sqlgetdata-and-block-cursors.md)


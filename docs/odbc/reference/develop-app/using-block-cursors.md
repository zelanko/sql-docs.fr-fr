---
title: À l’aide de curseurs de bloc | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], block
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 2aad7d6b-216e-47e7-b3cb-f95ad096f21a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 388995cd5cb8a711d72533685c14088a7e908475
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63313504"
---
# <a name="using-block-cursors"></a>Utilisation de curseurs de bloc
Prise en charge pour les curseurs de bloc est intégrée dans ODBC 3. *x*. **SQLFetch** peut être utilisé uniquement pour les extractions multilignes lorsqu’elle est appelée dans ODBC 3. *x*; si une application ODBC 2. *x* application appelle **SQLFetch**, il s’ouvre uniquement un curseur de ligne unique, avant uniquement. Lorsqu’une application ODBC 3. *x* application appelle **SQLFetch** dans un ODBC 2. *x* pilote, elle retourne une seule ligne, sauf si le pilote prend en charge **SQLExtendedFetch**. Pour plus d’informations, consultez [curseurs de bloc, curseurs avec défilement et compatibilité descendante](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) dans g : annexe Instructions de pilote pour la compatibilité descendante.  
  
 Pour utiliser les curseurs de bloc, l’application définit la taille de l’ensemble de lignes, lie les mémoires tampons d’ensemble de lignes (comme décrit dans la section précédente), si vous le souhaitez définit les attributs d’instruction SQL_ATTR_ROWS_FETCHED_PTR et SQL_ATTR_ROW_STATUS_PTR et les appels **SQLFetch**  ou **SQLFetchScroll** pour extraire un bloc de lignes. L’application peut modifier la taille de l’ensemble de lignes et lier le nouvel ensemble de lignes mémoires tampons (en appelant **SQLBindCol** ou en spécifiant un décalage de liaison) même après les lignes qui ont été extraites.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Taille des ensembles de lignes](../../../odbc/reference/develop-app/rowset-size.md)  
  
-   [Nombre de lignes extraites et état](../../../odbc/reference/develop-app/number-of-rows-fetched-and-status.md)  
  
-   [SQLGetData et curseurs de bloc ; bloc curso](../../../odbc/reference/develop-app/sqlgetdata-and-block-cursors.md)

---
title: "Défilement et extraction de lignes (ODBC) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scrollable cursors [ODBC]
- fetches [ODBC], scrollable cursors
- cursors [ODBC], scrollable
- scrolling rows [ODBC]
ms.assetid: c43764cb-5841-4b89-9dc0-984a7488b3c1
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5b5a9aefccf51cc4b3aac1aeba02c7878c6dceed
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="scrolling-and-fetching-rows-odbc"></a>Défilement et extraction de lignes (ODBC)
Lorsque vous utilisez un curseur de défilement, les applications appellent **SQLFetchScroll** pour positionner les curseur et extraire les lignes. **SQLFetchScroll** prend en charge le défilement relatif (suivant, précédent et relatif * n * lignes), défilement absolu (first, last et de ligne * n *) et la position du signet. Le *FetchOrientation* et *FetchOffset* arguments dans **SQLFetchScroll** spécifier quel ensemble de lignes à extraire, comme indiqué dans les diagrammes suivants.  
  
 ![L’extraction suivante, avant, les premier et dernier ensembles de lignes](../../../odbc/reference/develop-app/media/pr20_2.gif "pr20_2")  
  
 **L’extraction suivante, précédente, première et dernière ensembles de lignes**  
  
 ![L’extraction de lignes absolu, relatif ou avec signet](../../../odbc/reference/develop-app/media/pr20_1.gif "pr20_1")  
  
 **L’extraction des ensembles de lignes absolu, relatif ou avec signet**  
  
 **SQLFetchScroll** place le curseur à la ligne spécifiée et retourne les lignes dans l’ensemble de lignes en commençant par cette ligne. Si l’ensemble de lignes spécifié chevauche la fin du jeu de résultats, un ensemble de lignes partiel est retourné. Si l’ensemble de lignes spécifié chevauche le début du résultat défini, le premier ensemble de lignes dans le résultat de jeu est généralement retourné ; Pour plus d’informations, consultez la [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md) description de fonction.  
  
 Dans certains cas, l’application peut souhaiter de positionner le curseur sans devoir les extraire toutes les données. Par exemple, elle peut avoir besoin tester si une ligne existe ou simplement obtenir le signet pour la ligne sans afficher d’autres données sur le réseau. Pour ce faire, il définit l’attribut d’instruction SQL_ATTR_RETRIEVE_DATA à SQL_RD_OFF. La variable liée à la colonne de signet (le cas échéant) est toujours mise à jour, quelle que soit le paramètre de cet attribut d’instruction.  
  
 Une fois que l’ensemble de lignes a été récupéré, l’application peut appeler **SQLSetPos** pour positionner à une ligne particulière dans les lignes d’ensemble de lignes ou d’actualisation dans l’ensemble de lignes. Pour plus d’informations sur l’utilisation de **SQLSetPos**, consultez [mise à jour des données avec SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md).  
  
> [!NOTE]  
>  Le défilement est pris en charge dans ODBC 2. *x* pilotes **SQLExtendedFetch**. Pour plus d’informations, consultez [curseurs de bloc, les curseurs permettant le défilement et la compatibilité descendante](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)dans l’annexe g : pilote recommandations pour la compatibilité descendante.


---
title: Défilement et extraction de lignes | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- SQLFetchScroll function
- ODBC applications, cursors
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- fetching [ODBC]
- ODBC cursors, scrolling rows
ms.assetid: 9109f10d-326b-4a6d-8c97-831f60da8c4c
author: rothja
ms.author: jroth
ms.openlocfilehash: 08e7f37818ab8a1695e21bae527afc633a2b69c5
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85020394"
---
# <a name="scrolling-and-fetching-rows"></a>Défilement et extraction de lignes
  Pour utiliser un curseur permettant le défilement, une application ODBC doit :  
  
-   Définissez les fonctionnalités de curseur à l’aide de [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md).  
  
-   Ouvrez le curseur à l’aide de **SQLExecute** ou **SQLExecDirect**.  
  
-   Faites défiler et récupérez des lignes à l’aide de **SQLFetch** ou [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md).  
  
 **SQLFetch** et **SQLFetchScroll** peuvent extraire des blocs de lignes à la fois. Le nombre de lignes retournées est spécifié à l’aide de **SQLSetStmtAttr** pour définir le paramètre SQL_ATTR_ROW_ARRAY_SIZE.  
  
 Les applications ODBC peuvent utiliser **SQLFetch** pour effectuer une extraction à l’aide d’un curseur avant uniquement.  
  
 **SQLFetchScroll** est utilisé pour faire défiler un curseur. **SQLFetchScroll** prend en charge l’extraction des ensembles de lignes suivant, précédent, premier et dernier en plus de l’extraction relative (extraction de *l’ensemble de* lignes à partir du début de l’ensemble de lignes actuel) et de l’extraction absolue (extraction de l’ensemble de lignes à partir de la ligne *n*). Si *n* est négatif dans une extraction absolue, les lignes sont comptées à partir de la fin du jeu de résultats. Une extraction absolue de ligne -1 équivaut à l'extraction de l'ensemble de lignes qui démarre à la dernière ligne du jeu de résultats.  
  
 Les applications qui utilisent **SQLFetchScroll** uniquement pour ses fonctionnalités de curseur de bloc, telles que les rapports, sont susceptibles de traverser le jeu de résultats une seule fois, en utilisant uniquement l’option permettant d’extraire l’ensemble de lignes suivant. En revanche, les applications basées sur l’écran peuvent tirer parti de toutes les fonctionnalités de **SQLFetchScroll**. Si l’application définit la taille de l’ensemble de lignes sur le nombre de lignes affichées à l’écran et lie les mémoires tampons d’écran au jeu de résultats, elle peut traduire directement les opérations de barre de défilement en appels à **SQLFetchScroll**.  
  
|Opération de barre de défilement|Option de défilement SQLFetchScroll|  
|--------------------------|-------------------------------------|  
|Page précédente|SQL_FETCH_PRIOR|  
|Page suivante|SQL_FETCH_NEXT|  
|Ligne précédente|SQL_FETCH_RELATIVE avec FetchOffset égal à-1|  
|Ligne suivante|SQL_FETCH_RELATIVE avec FetchOffset égal à 1|  
|Case de défilement vers le haut|SQL_FETCH_FIRST|  
|Case de défilement vers le bas|SQL_FETCH_LAST|  
|Position aléatoire de la case de défilement|SQL_FETCH_ABSOLUTE|  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Création de signets pour des lignes dans ODBC](scrolling-and-fetching-rows-bookmarking-rows-in-odbc.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de curseurs &#40;ODBC&#41;](using-cursors-odbc.md)  
  
  

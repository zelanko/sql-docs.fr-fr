---
title: Faire défiler et aller chercher des rangées (fr) Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0ae9f1079f329951045d4b3f61b39c12efc153fb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302487"
---
# <a name="scrolling-and-fetching-rows"></a>Défilement et extraction de lignes
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Pour utiliser un curseur permettant le défilement, une application ODBC doit :  
  
-   Définissez les capacités de curseur à l’aide [de SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
-   Ouvrez le curseur à l’aide **de SQLExecute** ou **SQLExecDirect**.  
  
-   Faites défiler et aller chercher des rangées à l’aide **de SQLFetch** ou [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md).  
  
 **SQLFetch** et **SQLFetchSroll** peuvent aller chercher des blocs de rangées à la fois. Le nombre de lignes retournées est spécifié en utilisant **SQLSetStmtAttr** pour définir le SQL_ATTR_ROW_ARRAY_SIZE paramètre.  
  
 Les applications ODBC peuvent utiliser **SQLFetch** pour aller chercher par un curseur avant-seulement.  
  
 **SQLFetchScroll** est utilisé pour faire défiler autour d’un curseur. **SQLFetchScroll** prend en charge l’aller chercher les lignes suivantes, avant, première et dernière en plus de la recherche relative (aller chercher les lignes *rowset n* dès le début de la rangée actuelle) et l’aller chercher absolu (aller chercher le rowset à partir de la rangée *n*). Si *n* est négatif dans un aller absolument, les lignes sont comptées à partir de la fin de l’ensemble de résultats. Une extraction absolue de ligne -1 équivaut à l'extraction de l'ensemble de lignes qui démarre à la dernière ligne du jeu de résultats.  
  
 Les applications qui utilisent **SQLFetchScroll** uniquement pour ses capacités de curseur de bloc, telles que les rapports, sont susceptibles de passer par le jeu de résultat une seule fois, en utilisant seulement la possibilité d’aller chercher le jeu de ligne suivant. Les applications basées sur l’écran, d’autre part, peuvent profiter de toutes les capacités de **SQLFetchScroll**. Si l’application définit la taille de la ligne au nombre de lignes affichées sur l’écran et lie les tampons d’écran à l’ensemble de résultat, elle peut traduire les opérations de barre de défilement directement aux appels à **SQLFetchScroll**.  
  
|Opération de barre de défilement|Option de défilement SQLFetchScroll|  
|--------------------------|-------------------------------------|  
|Page précédente|SQL_FETCH_PRIOR|  
|Page vers le bas|SQL_FETCH_NEXT|  
|Ligne précédente|SQL_FETCH_RELATIVE avec FetchOffset égal à -1|  
|Ligne suivante|SQL_FETCH_RELATIVE avec FetchOffset égal à 1|  
|Case de défilement vers le haut|SQL_FETCH_FIRST|  
|Case de défilement vers le bas|SQL_FETCH_LAST|  
|Position aléatoire de la case de défilement|SQL_FETCH_ABSOLUTE|  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Création de signets pour des lignes dans ODBC](../../relational-databases/native-client-odbc-cursors/scrolling-and-fetching-rows-bookmarking-rows-in-odbc.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de cursors &#40;&#41;ODBC](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  

---
title: Le défilement et extraction de lignes (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- fetches [ODBC], scrollable cursors
- cursors [ODBC], scrollable
- scrolling rows [ODBC]
ms.assetid: c43764cb-5841-4b89-9dc0-984a7488b3c1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b326ed0c4e9a196904aa0f5c60b705243ef3bd97
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68061584"
---
# <a name="scrolling-and-fetching-rows-odbc"></a>Défilement et extraction de lignes (ODBC)
Lorsque vous utilisez un curseur de défilement, les applications appellent **SQLFetchScroll** pour positionner les curseur et extraire les lignes. **SQLFetchScroll** prend en charge le défilement relatif (relative suivant et avant *n* lignes), défilement absolu (prénom et de ligne *n*) et le positionnement par signet. Le *FetchOrientation* et *FetchOffset* arguments dans **SQLFetchScroll** spécifier quel ensemble de lignes à extraire, comme indiqué dans les diagrammes suivants.  
  
 ![Extraction des suivante, avant, les premier et dernier ensembles de lignes](../../../odbc/reference/develop-app/media/pr20_2.gif "pr20_2")  
  
 **Extraction des suivante, précédente, première et dernière ensembles de lignes**  
  
 ![Extraction des ensembles de lignes absolu, relatif ou avec signet](../../../odbc/reference/develop-app/media/pr20_1.gif "pr20_1")  
  
 **Extraction des ensembles de lignes absolu, relatif ou avec signet**  
  
 **SQLFetchScroll** positionne le curseur sur la ligne spécifiée et retourne les lignes dans l’ensemble de lignes en commençant par cette ligne. Si l’ensemble de lignes spécifié chevauche la fin du jeu de résultats, un ensemble de lignes partiel est retourné. Si l’ensemble de lignes spécifié chevauche le début du résultat défini, le premier ensemble de lignes dans le résultat de jeu est généralement retourné ; Pour plus d’informations, consultez le [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md) description de fonction.  
  
 Dans certains cas, l’application peut souhaiter positionner le curseur sans récupérer toutes les données. Par exemple, elle peut avoir besoin tester si une ligne existe ou obtenir simplement le signet pour la ligne sans afficher d’autres données sur le réseau. Pour ce faire, il définit l’attribut d’instruction SQL_ATTR_RETRIEVE_DATA sur SQL_RD_OFF. La variable liée à la colonne de signet (le cas échéant) est toujours mis à jour, quel que soit le paramètre de cet attribut d’instruction.  
  
 Une fois que l’ensemble de lignes a été récupérée, l’application peut appeler **SQLSetPos** pour positionner à une ligne particulière dans les lignes d’ensemble de lignes ou de l’actualisation de l’ensemble de lignes. Pour plus d’informations sur l’utilisation de **SQLSetPos**, consultez [la mise à jour des données avec SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md).  
  
> [!NOTE]  
>  Le défilement est pris en charge dans ODBC 2. *x* pilotes par **SQLExtendedFetch**. Pour plus d’informations, consultez [curseurs de bloc, curseurs avec défilement et compatibilité descendante](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)dans g : annexe Instructions de pilote pour la compatibilité descendante.

---
description: Défilement et extraction de lignes (ODBC)
title: Défilement et extraction de lignes (ODBC) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b6fcdd2cd635a7da66a5d81c4beb24088f96382b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476491"
---
# <a name="scrolling-and-fetching-rows-odbc"></a>Défilement et extraction de lignes (ODBC)
Lors de l’utilisation d’un curseur de défilement, les applications appellent **SQLFetchScroll** pour positionner le curseur et extraire des lignes. **SQLFetchScroll** prend en charge le défilement relatif (Next, précédent et relative *n* lignes), le défilement absolu (First, Last et Row *n*) et le positionnement par signet. Les arguments *FetchOrientation* et *FetchOffset* dans **SQLFetchScroll** spécifient l’ensemble de lignes à extraire, comme indiqué dans les diagrammes suivants.  
  
 ![Extraction des ensembles de lignes suivante, précédente, première et dernière](../../../odbc/reference/develop-app/media/pr20_2.gif "pr20_2")  
  
 **Extraction des ensembles de lignes suivante, précédente, première et dernière**  
  
 ![Extraction de l'ensemble de lignes absolu, relatif ou avec signet](../../../odbc/reference/develop-app/media/pr20_1.gif "pr20_1")  
  
 **Extraction d’ensembles de lignes absolus, relatifs et avec signets**  
  
 **SQLFetchScroll** positionne le curseur sur la ligne spécifiée et retourne les lignes de l’ensemble de lignes en commençant par cette ligne. Si l’ensemble de lignes spécifié chevauche la fin du jeu de résultats, un ensemble de lignes partiel est retourné. Si l’ensemble de lignes spécifié chevauche le début du jeu de résultats, le premier ensemble de lignes dans le jeu de résultats est généralement retourné. Pour plus d’informations, consultez la description de la fonction [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md) .  
  
 Dans certains cas, l’application peut souhaiter positionner le curseur sans récupérer de données. Par exemple, il peut être utile de tester si une ligne existe ou simplement d’obtenir le signet de la ligne sans placer d’autres données sur le réseau. Pour ce faire, il définit l’attribut d’instruction SQL_ATTR_RETRIEVE_DATA sur SQL_RD_OFF. La variable liée à la colonne de signets (le cas échéant) est toujours mise à jour, quel que soit le paramètre de cet attribut d’instruction.  
  
 Une fois l’ensemble de lignes récupéré, l’application peut appeler **SQLSetPos** pour la positionner sur une ligne particulière de l’ensemble de lignes ou actualiser les lignes de l’ensemble de lignes. Pour plus d’informations sur l’utilisation de **SQLSetPos**, consultez [mise à jour des données avec SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md).  
  
> [!NOTE]  
>  Le défilement est pris en charge dans ODBC 2. *x* pilotes par **SQLExtendedFetch**. Pour plus d’informations, consultez [curseurs de bloc, curseurs avec défilement et compatibilité descendante](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)dans l’annexe G : instructions relatives aux pilotes pour la compatibilité descendante.

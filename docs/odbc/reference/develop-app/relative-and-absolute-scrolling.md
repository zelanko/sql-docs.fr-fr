---
title: Défilement relatif et absolu | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- absolute scrolling [ODBC]
- relative scrolling [ODBC]
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
ms.assetid: 3d0ff48d-fef5-4c01-bb1d-a583e6269b66
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e2034a3922dcd3db77113e08a6c48fe7ac39457f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138059"
---
# <a name="relative-and-absolute-scrolling"></a>Défilement relatif et absolu
La plupart des options de défilement dans **SQLFetchScroll** déplacent le curseur par rapport à la position actuelle ou à une position absolue. **SQLFetchScroll** prend en charge l’extraction des ensembles de lignes suivant, précédent, premier et dernier, ainsi que l’extraction relative (extraction de *l’ensemble de* lignes à partir du début de l’ensemble de lignes actuel) et l’extraction absolue (extraction de l’ensemble de lignes à partir de la ligne *n*). Si *n* est négatif dans une extraction absolue, les lignes sont comptées à partir de la fin du jeu de résultats. Ainsi, une extraction absolue de Row-1 signifie extraire l’ensemble de lignes qui commence par la dernière ligne du jeu de résultats.  
  
 Les curseurs dynamiques détectent les lignes insérées et supprimées dans le jeu de résultats. il n’existe donc aucun moyen simple pour les curseurs dynamiques de récupérer la ligne à un nombre particulier, à l’exception de la lecture à partir du début du jeu de résultats, ce qui est susceptible d’être lent. En outre, l’extraction absolue n’est pas très utile dans les curseurs dynamiques, car les numéros de ligne changent à mesure que des lignes sont insérées et supprimées. par conséquent, l’extraction successive du même numéro de ligne peut produire des lignes différentes.  
  
 Les applications qui utilisent **SQLFetchScroll** uniquement pour ses fonctionnalités de curseur de bloc, telles que les rapports, sont susceptibles de traverser le jeu de résultats une seule fois, en utilisant uniquement l’option permettant d’extraire l’ensemble de lignes suivant. En revanche, les applications basées sur l’écran peuvent tirer parti de toutes les fonctionnalités de **SQLFetchScroll**. Si l’application définit la taille de l’ensemble de lignes sur le nombre de lignes affichées à l’écran et lie les mémoires tampons d’écran au jeu de résultats, elle peut traduire directement les opérations de barre de défilement en appels à **SQLFetchScroll**.  
  
|Opération de barre de défilement|Option de défilement SQLFetchScroll|  
|--------------------------|-------------------------------------|  
|Page précédente|SQL_FETCH_PRIOR|  
|Page suivante|SQL_FETCH_NEXT|  
|Ligne précédente|SQL_FETCH_RELATIVE avec *FetchOffset* égal à-1|  
|Ligne suivante|SQL_FETCH_RELATIVE avec *FetchOffset* égal à 1|  
|Case de défilement en haut|SQL_FETCH_FIRST|  
|Case de défilement en bas|SQL_FETCH_LAST|  
|Position aléatoire de la case de défilement|SQL_FETCH_ABSOLUTE|  
  
 De telles applications doivent également positionner la case de défilement après une opération de défilement, ce qui nécessite le numéro de ligne actuel et le nombre de lignes. Pour le numéro de ligne actuel, les applications peuvent soit suivre le numéro de ligne actuel, soit appeler **SQLGetStmtAttr** avec l’attribut SQL_ATTR_ROW_NUMBER pour les récupérer.  
  
 Le nombre de lignes dans le curseur, qui est la taille du jeu de résultats, est disponible en tant que SQL_DIAG_CURSOR_ROW_COUNT champ de l’en-tête de diagnostic. La valeur de ce champ est définie uniquement après l’appel de **SQLExecute**, **SQLExecDirect**ou **SQLMoreResult** . Ce nombre peut être un nombre approximatif ou un nombre exact, en fonction des capacités du pilote. La prise en charge du pilote peut être déterminée en appelant **SQLGetInfo** avec les types d’informations d’attributs de curseur et en vérifiant si le bit SQL_CA2_CRC_APPROXIMATE ou SQL_CA2_CRC_EXACT est retourné pour le type de curseur.  
  
 Un nombre exact de lignes n’est jamais pris en charge pour un curseur dynamique. Pour les autres types de curseurs, le pilote peut prendre en charge des nombres de lignes exacts ou approximatifs, mais pas les deux. Si le pilote ne prend pas en charge les nombres de lignes exacts et approximatifs pour un type de curseur spécifique, le champ SQL_DIAG_CURSOR_ROW_COUNT contient le nombre de lignes extraites jusqu’à présent. Indépendamment de ce que le pilote prend en charge, **SQLFetchScroll** avec une *opération* de SQL_FETCH_LAST, le champ SQL_DIAG_CURSOR_ROW_COUNT peut contenir le nombre de lignes exact.

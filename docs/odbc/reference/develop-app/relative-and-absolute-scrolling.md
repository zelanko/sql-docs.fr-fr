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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138059"
---
# <a name="relative-and-absolute-scrolling"></a>Défilement relatif et absolu
La plupart des options de défilement dans **SQLFetchScroll** positionner le curseur par rapport à la position actuelle ou à une position absolue. **SQLFetchScroll** prend en charge l’extraction de la suivante, précédente, première et dernière ensembles de lignes, comme l’extraction bien comme étant relatif (extraire l’ensemble de lignes *n* lignes à partir du début de l’ensemble de lignes actuel) et absolu extraction (fetch le démarrage de l’ensemble de lignes à la ligne *n*). Si *n* est négatif dans une extraction absolue, les lignes sont comptées à partir de la fin du jeu de résultats. Par conséquent, une extraction absolue de ligne -1 équivaut à l’extraction de l’ensemble de lignes qui commence par la dernière ligne du jeu de résultats.  
  
 Les curseurs dynamiques détectent les lignes insérées et supprimées du jeu de résultats, donc il n’existe aucun moyen facile pour les curseurs dynamiques récupérer la ligne à un nombre autre que lecture à partir du début du jeu de résultats, qui est susceptible d’être lente. En outre, l’extraction absolue n’est pas très utile dans les curseurs dynamiques, car les numéros de ligne modifié lorsque des lignes sont insérées et supprimées ; Par conséquent, l’extraction successivement le même nombre de lignes peut produire des différentes lignes.  
  
 Les applications qui utilisent **SQLFetchScroll** uniquement pour son bloc fonctionnalités du curseur, tels que des rapports, sont susceptibles de passer par le jeu de résultats une seule fois, à l’aide de l’option uniquement pour extraire l’ensemble de lignes suivant. Applications basées sur l’écran, quant à eux, peuvent tirer parti de toutes les fonctionnalités de **SQLFetchScroll**. Si l’application définit la taille de l’ensemble de lignes sur le nombre de lignes affichées sur l’écran et lie les mémoires tampons d’écran au jeu de résultats, il peut traduire directement aux appels à des opérations de barre de défilement **SQLFetchScroll**.  
  
|Opération de barre de défilement|Option de défilement SQLFetchScroll|  
|--------------------------|-------------------------------------|  
|Page précédente|SQL_FETCH_PRIOR|  
|Pg. suiv|SQL_FETCH_NEXT|  
|Ligne précédente|SQL_FETCH_RELATIVE avec *FetchOffset* égal à -1|  
|Ligne suivante|SQL_FETCH_RELATIVE avec *FetchOffset* égal à 1|  
|Case de défilement en haut|SQL_FETCH_FIRST|  
|Case de défilement en bas|SQL_FETCH_LAST|  
|Position aléatoire de la case de défilement|SQL_FETCH_ABSOLUTE|  
  
 Ces applications doivent également positionner le curseur de défilement après une opération de défilement, ce qui nécessite le numéro de ligne actuel et le nombre de lignes. Pour le numéro de ligne actuelle, les applications peuvent soit effectuer le suivi du nombre de lignes actuel ou d’un appel **SQLGetStmtAttr** avec l’attribut SQL_ATTR_ROW_NUMBER pour la récupérer.  
  
 Le nombre de lignes du curseur, ce qui est la taille du résultat défini, il est disponible en tant que le champ SQL_DIAG_CURSOR_ROW_COUNT de l’en-tête de diagnostic. La valeur dans ce champ est définie uniquement après avoir **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResult** a été appelée. Ce nombre peut être un nombre approximatif ou un nombre exact, selon les capacités du pilote. Prise en charge du pilote peut être déterminé en appelant **SQLGetInfo** avec les types d’informations de curseur attributs et en vérifiant si le bit SQL_CA2_CRC_APPROXIMATE ou SQL_CA2_CRC_EXACT est retourné pour le type de curseur.  
  
 Un nombre de lignes exacte n’est jamais pris en charge pour un curseur dynamique. Pour les autres types de curseurs, le pilote peut prendre en charge des nombres de lignes exact ou approximatif, mais pas les deux. Si le pilote prend en charge ni exacte ni approximative du nombre de lignes pour un type de curseur spécifique, le champ SQL_DIAG_CURSOR_ROW_COUNT contient le nombre de lignes qui ont été extraites jusqu'à présent. Quel que soit le quel pilote prend en charge, **SQLFetchScroll** avec un *opération* de SQL_FETCH_LAST entraîne le champ SQL_DIAG_CURSOR_ROW_COUNT contenir le nombre exact de lignes.

---
title: Défilement relatif et absolu (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae0ed5af8d116a3038b55b1e3d68231154c2a35c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300099"
---
# <a name="relative-and-absolute-scrolling"></a>Défilement relatif et absolu
La plupart des options de défilement dans **SQLFetchScroll** positionnent le curseur par rapport à la position actuelle ou à une position absolue. **SQLFetchScroll** prend en charge l’aller chercher les lignes suivantes, avant, première et dernière, ainsi que les aller chercher relatifs (aller chercher les lignes en rangée *n* dès le début de la rangée actuelle) et l’aller chercher absolu (aller chercher le rowset à partir de la rangée *n*). Si *n* est négatif dans un aller absolument, les lignes sont comptées à partir de la fin de l’ensemble de résultats. Ainsi, un coup de grâce absolu de la ligne -1 signifie aller chercher le rowset qui commence avec la dernière rangée dans l’ensemble de résultat.  
  
 Les curseurs dynamiques détectent les lignes insérées et supprimées de l’ensemble de résultats, de sorte qu’il n’y a pas de moyen facile pour les curseurs dynamiques de récupérer la ligne à un nombre particulier autre que la lecture dès le début de l’ensemble de résultats, qui est susceptible d’être lent. En outre, l’aller chercher absolu n’est pas très utile dans les curseurs dynamiques parce que les nombres de rangées changent au fur et à mesure que les rangées sont insérées et supprimées; par conséquent, successivement aller chercher le même numéro de rangée peut donner des lignes différentes.  
  
 Les applications qui utilisent **SQLFetchScroll** uniquement pour ses capacités de curseur de bloc, telles que les rapports, sont susceptibles de passer par le jeu de résultat une seule fois, en utilisant seulement la possibilité d’aller chercher le jeu de ligne suivant. Les applications basées sur l’écran, d’autre part, peuvent profiter de toutes les capacités de **SQLFetchScroll**. Si l’application définit la taille de la ligne au nombre de lignes affichées sur l’écran et lie les tampons d’écran à l’ensemble de résultat, elle peut traduire les opérations de barre de défilement directement aux appels à **SQLFetchScroll**.  
  
|Opération de barre de défilement|Option de défilement SQLFetchScroll|  
|--------------------------|-------------------------------------|  
|Page précédente|SQL_FETCH_PRIOR|  
|Page vers le bas|SQL_FETCH_NEXT|  
|Ligne précédente|SQL_FETCH_RELATIVE avec *FetchOffset* égal à -1|  
|Ligne suivante|SQL_FETCH_RELATIVE avec *FetchOffset* égal à 1|  
|Boîte de défilement en haut|SQL_FETCH_FIRST|  
|Boîte de défilement en bas|SQL_FETCH_LAST|  
|Position aléatoire de la case de défilement|SQL_FETCH_ABSOLUTE|  
  
 Ces applications doivent également positionner la boîte de défilement après une opération de défilement, ce qui nécessite le numéro de ligne actuel et le nombre de lignes. Pour le numéro de rangée actuel, les applications peuvent soit garder une trace du numéro de ligne actuel, soit appeler **SQLGetStmtAttr** avec l’attribut SQL_ATTR_ROW_NUMBER pour le récupérer.  
  
 Le nombre de lignes dans le curseur, qui est la taille de l’ensemble de résultat, est disponible comme le champ SQL_DIAG_CURSOR_ROW_COUNT de l’en-tête diagnostique. La valeur dans ce domaine n’est définie qu’après **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResult** a été appelé. Ce nombre peut être soit un nombre approximatif ou un décompte exact, selon les capacités du conducteur. Le support du conducteur peut être déterminé en appelant **SQLGetInfo** avec le curseur attribue les types d’information et en vérifiant si le SQL_CA2_CRC_APPROXIMATE ou SQL_CA2_CRC_EXACT bit est retourné pour le type de curseur.  
  
 Un nombre exact de lignes n’est jamais pris en charge pour un curseur dynamique. Pour d’autres types de curseurs, le conducteur peut prendre en charge les nombres de rangées exacts ou approximatifs, mais pas les deux. Si le conducteur ne prend en charge ni le nombre de rangées exactes ni approximatives pour un type de curseur spécifique, le champ SQL_DIAG_CURSOR_ROW_COUNT contient le nombre de rangées qui ont été récupérées jusqu’à présent. Peu importe ce que le conducteur prend en charge, **SQLFetchScroll** avec une *opération* de SQL_FETCH_LAST fera en sorte que le champ SQL_DIAG_CURSOR_ROW_COUNT contiendra le nombre exact de rangées.

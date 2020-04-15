---
title: Taille Rowset (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- rowset size [ODBC]
- cursors [ODBC], block
- result sets [ODBC], rowset size
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 60366ae8-175c-456a-ae5e-bdd860786911
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 11b95768934f96e1587b3c570b2510f3c2849239
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304240"
---
# <a name="rowset-size"></a>Taille des ensembles de lignes
La taille de l’acart à utiliser dépend de l’application. Les applications basées sur l’écran suivent généralement l’une des deux stratégies. La première consiste à définir la taille de l’aviron au nombre de lignes affichées à l’écran; si l’utilisateur resize l’écran, l’application modifie la taille de l’ensemble en conséquence. La deuxième consiste à définir la taille de l’acart à un plus grand nombre, comme 100, ce qui réduit le nombre d’appels vers la source de données. L’application défile localement dans le ligne lorsque c’est possible et ne récupère de nouvelles lignes que lorsqu’elle défile à l’extérieur de la ligne.  
  
 D’autres applications, telles que les rapports, ont tendance à définir la taille de la ligne au plus grand nombre de lignes que l’application peut raisonnablement gérer - avec un plus grand jeu de ligne, le réseau au-dessus par rangée est parfois réduit. Exactement la taille d’un ramage peut être dépend de la taille de chaque rangée et la quantité de mémoire disponible.  
  
 La taille de Rowset est réglée par un appel à **SQLSetStmtAttr** avec un argument *d’attribut* de SQL_ATTR_ROW_ARRAY_SIZE. L’application peut modifier la taille de l’aviron, lier de nouveaux tampons encastrés (en appelant **SQLBindCol** ou en spécifiant un décalage de liaison) même après que les lignes ont été récupérées, ou les deux. Les implications de la modification de la taille de l’aviron dépendent de la fonction :  
  
-   **SQLFetch** et **SQLFetchScroll** utilisent la taille de l’aviron au moment de l’appel pour déterminer le nombre de rangées à aller chercher. Cependant, **SQLFetchScroll** avec une *fetchOrientation* de SQL_FETCH_NEXT incréments le curseur basé sur le ramage de l’aller chercher précédent, puis récupère un rowset en fonction de la taille actuelle rowset.  
  
-   **SQLSetPos** utilise la taille de la ligne qui est en vigueur à partir de l’appel précédent à **SQLFetch** ou **SQLFetchScroll**, parce que **SQLSetPos** fonctionne sur un rowset qui a déjà été fixé. **SQLSetPos** reprendra également la nouvelle taille de la rangée si **SQLBulkOperations** a été appelé après que la taille du rowset a été changée.  
  
-   **SQLBulkOperations** utilise la taille de l’aviron en vigueur au moment de l’appel, parce qu’il effectue des opérations sur une table indépendamment de tout ramset récupéré.

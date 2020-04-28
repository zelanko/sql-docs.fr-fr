---
title: Taille de l’ensemble de lignes | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304240"
---
# <a name="rowset-size"></a>Taille des ensembles de lignes
La taille de l’ensemble de lignes à utiliser dépend de l’application. Les applications basées sur l’écran suivent généralement l’une des deux stratégies. La première consiste à définir la taille de l’ensemble de lignes sur le nombre de lignes affichées à l’écran. Si l’utilisateur redimensionne l’écran, l’application modifie la taille de l’ensemble de lignes en conséquence. La seconde consiste à définir la taille de l’ensemble de lignes sur un nombre plus élevé, tel que 100, ce qui réduit le nombre d’appels à la source de données. L’application fait défiler localement l’ensemble de lignes dans la mesure du possible et récupère les nouvelles lignes uniquement lorsqu’il fait défiler l’ensemble de lignes.  
  
 D’autres applications, telles que les rapports, ont tendance à définir la taille de l’ensemble de lignes sur le plus grand nombre de lignes que l’application peut raisonnablement gérer-avec un plus grand ensemble de lignes, la charge réseau par ligne est parfois réduite. La taille exacte d’un ensemble de lignes dépend de la taille de chaque ligne et de la quantité de mémoire disponible.  
  
 La taille de l’ensemble de lignes est définie par un appel à **SQLSetStmtAttr** avec un argument d' *attribut* de SQL_ATTR_ROW_ARRAY_SIZE. L’application peut modifier la taille de l’ensemble de lignes, lier de nouvelles mémoires tampons d’ensemble de lignes (en appelant **SQLBindCol** ou en spécifiant un décalage de liaison) même après l’extraction des lignes, ou les deux à la fois. Les implications de la modification de la taille de l’ensemble de lignes dépendent de la fonction :  
  
-   **SQLFetch** et **SQLFetchScroll** utilisent la taille de l’ensemble de lignes au moment de l’appel pour déterminer le nombre de lignes à extraire. Toutefois, **SQLFetchScroll** avec un *FetchOrientation* de SQL_FETCH_NEXT incrémente le curseur en fonction de l’ensemble de lignes de l’extraction précédente, puis extrait un ensemble de lignes en fonction de la taille de l’ensemble de lignes actuel.  
  
-   **SQLSetPos** utilise la taille de l’ensemble de lignes en vigueur au cours de l’appel précédent à **SQLFetch** ou **SQLFetchScroll**, car **SQLSetPos** opère sur un ensemble de lignes qui a déjà été défini. **SQLSetPos** prend également en compte la nouvelle taille de l’ensemble de lignes si **SQLBulkOperations** a été appelé après la modification de la taille de l’ensemble de lignes.  
  
-   **SQLBulkOperations** utilise la taille de l’ensemble de lignes en vigueur au moment de l’appel, car il effectue des opérations sur une table indépendante de tout ensemble de lignes extrait.

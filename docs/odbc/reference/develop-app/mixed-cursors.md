---
title: Curseurs mixtes | Microsoft Docs
ms.custom: ''
ms.date: 01/20/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mixed cursors [ODBC]
- cursors [ODBC], dynamic
- keyset-driven cursors [ODBC]
- dynamic cursors [ODBC]
- cursors [ODBC], key-set driven
- cursors [ODBC], mixed
ms.assetid: 9beb2db9-0b6d-491d-9529-d64e64e59014
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a91dacf8ea9c0ed0db2c3b64634ddd53b854a534
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307434"
---
# <a name="mixed-cursors"></a>Curseurs mixtes

Un curseur mixte est une combinaison d’un curseur de jeu de clés et d’un curseur dynamique. Elle est utilisée lorsque le jeu de résultats est trop grand pour enregistrer des clés pour l’ensemble du jeu de résultats. Les curseurs mixtes sont implémentés en créant un jeu de clés qui est plus petit que l’ensemble du jeu de résultats, mais plus grand que l’ensemble de lignes.  
  
 Tant que l’application fait défiler le jeu de clés, le comportement est piloté par jeu de clés. Lorsque l’application fait défiler en dehors du jeu de clés, le comportement est dynamique : le curseur extrait les lignes demandées et crée un nouveau jeu de clés. Une fois le nouveau jeu de clés créé, le comportement revient à la valeur keyset dans ce jeu de clés.  
  
 Par exemple, supposons qu’un jeu de résultats contient 1 000 lignes et utilise un curseur mixte avec une taille de jeu de clés de 100 et une taille d’ensemble de lignes de 10. Lorsque le premier ensemble de lignes est extrait, le curseur crée un jeu de clés composé des clés pour les 100 premières lignes. Elle retourne ensuite les 10 premières lignes, comme demandé.  
  
 Supposons à présent qu’une autre application supprime les lignes 11 et 101. Si le curseur tente d’extraire la ligne 11, il rencontre un intervalle parce qu’il a une clé pour cette ligne, mais qu’il n’existe pas de ligne ; Il s’agit d’un comportement piloté par jeu de clés. Si le curseur tente d’extraire la ligne 101, le curseur ne détecte pas que la ligne est manquante, car il n’a pas de clé pour la ligne. Au lieu de cela, il récupère ce qui était précédemment la ligne 102. Il s’agit du comportement de curseur dynamique.  
  
 Un curseur mixte est équivalent à un curseur de jeu de clés lorsque la taille du keyset est égale à la taille du jeu de résultats. Un curseur mixte est équivalent à un curseur dynamique lorsque la taille du keyset est égale à 1.

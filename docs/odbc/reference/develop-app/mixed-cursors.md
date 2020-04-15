---
title: Curseurs mixtes (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307434"
---
# <a name="mixed-cursors"></a>Curseurs mixtes

Un curseur mixte est une combinaison d’un curseur à clé et d’un curseur dynamique. Il est utilisé lorsque l’ensemble de résultat est trop grand pour enregistrer raisonnablement les clés pour l’ensemble du résultat. Les curseurs mixtes sont mis en œuvre en créant un jeu-clé plus petit que l’ensemble de résultats, mais plus grand que le jeu de ligne.  
  
 Tant que l’application défile dans le jeu de clés, le comportement est keyset-driven. Lorsque l’application défile en dehors du jeu de clés, le comportement est dynamique : le curseur récupère les lignes demandées et crée un nouvel ensemble de clés. Après la création du nouveau jeu de clés, le comportement revient à keyset-driven dans ce jeu de clés.  
  
 Supposons, par exemple, qu’un ensemble de résultats comporte 1 000 lignes et qu’il utilise un curseur mixte d’une taille de 100 et une taille de 10 rames. Lorsque le premier jeu de ligne est récupéré, le curseur crée un jeu de clés composé des touches pour les 100 premières rangées. Il renvoie ensuite les 10 premières rangées, comme demandé.  
  
 Supposons maintenant qu’une autre application supprime les lignes 11 et 101. Si le curseur tente de récupérer la rangée 11, il rencontrera un écart parce qu’il a une clé pour cette rangée, mais aucune rangée n’existe; il s’agit d’un comportement axé sur les clés. Si le curseur tente de récupérer la rangée 101, le curseur ne détectera pas que la ligne est manquante parce qu’elle n’a pas de clé pour la ligne. Au lieu de cela, il va récupérer ce qui était auparavant rangée 102. Il s’agit d’un comportement de curseur dynamique.  
  
 Un curseur mixte est équivalent à un curseur à clé lorsque la taille du jeu de clés est égale à la taille de l’ensemble de résultats. Un curseur mixte est équivalent à un curseur dynamique lorsque la taille du jeu à clé est égale à 1.

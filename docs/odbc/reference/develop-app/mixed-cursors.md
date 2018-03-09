---
title: Mixte curseurs | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mixed cursors [ODBC]
- cursors [ODBC], dynamic
- keyset-driven cursors [ODBC]
- dynamic cursors [ODBC]
- cursors [ODBC], key-set driven
- cursors [ODBC], mixed
ms.assetid: 9beb2db9-0b6d-491d-9529-d64e64e59014
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3ca9ad7c2c1f085cf3a74ab8b824ef7c4d6df2e6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="mixed-cursors"></a>Curseurs mixtes
Un curseur mixte est une combinaison d’un curseur keyset et curseur dynamique. Il est utilisé lorsque le jeu de résultats est trop volumineux pour être raisonnablement enregistré clés pour le jeu de résultats entier. Mixte de curseurs est implémenté en créant un jeu de clés qui est plus petit que le jeu de résultats complet mais supérieure à l’ensemble de lignes.  
  
 Tant que l’application fait défiler dans le jeu de clés, le comportement est piloté par jeu de clés. Lorsque l’application fait défiler le jeu de clés à l’extérieur, le comportement est dynamique : le curseur, extrait les lignes demandées et crée un nouveau jeu de clés. Une fois le nouveau jeu de clés est créé, le comportement revient à keyset dans ce jeu de clés.  
  
 Par exemple, un jeu de résultats est de 1 000 lignes et utilise un curseur mixte avec une taille de jeu de clés de 100 et une taille d’ensemble de lignes de 10. Lorsque le premier ensemble de lignes est atteinte, le curseur crée un jeu de clés comprenant des clés pour les 100 premières lignes. Il retourne ensuite les 10 premières lignes, comme le demande.  
  
 Supposons à présent qu’une autre application supprime les lignes 11 et 101. Si le curseur tente de récupérer la ligne 11, il se produit un trou, car il a une clé pour cette ligne, mais la ligne n’existe pas ; Il s’agit de curseurs pilotés par un comportement. Si le curseur tente de récupérer la ligne 101, le curseur ne détecte pas que la ligne est manquante, car il n’a pas de clé pour la ligne. Il récupère à la place, ce qui a été précédemment ligne 102. Il s’agit du comportement des curseurs dynamiques.  
  
 Un curseur mixte est équivalent à un curseur keyset lorsque la taille du jeu de clés est égale à la taille du jeu de résultats. Un curseur mixte est équivalent à un curseur dynamique lorsque la taille du jeu de clés est égale à 1.

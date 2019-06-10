---
title: Mixte curseurs | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ef8d5142397b4169513cf262ba4126ccba1fc1c3
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66785835"
---
# <a name="mixed-cursors"></a>Curseurs mixtes

Un curseur mixte est une combinaison d’un curseur keyset et un curseur dynamique. Il est utilisé lorsque le jeu de résultats est trop volumineux pour être raisonnablement enregistré clés pour le jeu de résultats entier. Curseurs mixtes sont implémentées en créant un jeu de clés est plus petit que le jeu de résultats complet mais supérieure à l’ensemble de lignes.  
  
 Tant que l’application utilise le défilement dans le jeu de clés, le comportement est commandé par keyset. Lorsque l’application fait défiler le jeu de clés à l’extérieur, le comportement est dynamique : Le curseur extrait les lignes demandées et crée un nouveau jeu de clés. Une fois le nouveau jeu de clés est créé, le comportement revient à keyset dans ce jeu de clés.  
  
 Par exemple, un jeu de résultats a 1 000 lignes et utilise un curseur mixte avec une taille de jeu de clés de 100 et une taille d’ensemble de lignes de 10. Lorsque le premier ensemble de lignes est atteinte, le curseur crée un jeu de clés constituée des clés pour les 100 premières lignes. Elle retourne ensuite les 10 premières lignes, comme demandé.  
  
 Maintenant, supposons qu’une autre application supprime les lignes 11 et 101. Si le curseur tente de récupérer la ligne 11, qu’il rencontrera un écart, car il a une clé pour cette ligne, mais la ligne n’existe pas ; Il s’agit de curseurs pilotés par un comportement. Si le curseur tente de récupérer la ligne 101, le curseur ne détecte pas que la ligne est manquante, car il n’a pas de clé pour la ligne. Au lieu de cela, elle récupère ce qui a été précédemment ligne 102. Il s’agit de comportement du curseur dynamique.  
  
 Un curseur mixte est équivalent à un curseur keyset lorsque la taille du jeu de clés est égale à la taille du jeu de résultats. Un curseur mixte est équivalent à un curseur dynamique lorsque la taille du jeu de clés est égale à 1.

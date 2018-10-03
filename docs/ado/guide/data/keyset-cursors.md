---
title: Les curseurs keyset | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Keyset cursors [ADO]
- cursors [ADO], Keyset
ms.assetid: 14b51b17-6fd9-4146-af45-ca4b0fe6d48a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a2ff246d01254ceb2b526b5118553d72cc499046
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47726147"
---
# <a name="keyset-cursors"></a>Curseurs de jeu de clés
Le curseur de jeu de clés fournit des fonctionnalités entre un statique et un curseur dynamique dans sa capacité à détecter les modifications. À un curseur statique, il ne détecte pas toujours les modifications apportées à l’appartenance et l’ordre du jeu de résultats. Comme un curseur dynamique, il détecte les modifications apportées aux valeurs de lignes dans le jeu de résultats.  
  
 Curseurs sont contrôlées par un ensemble d’identificateurs uniques (clés) appelé jeu de clés. Les clés sont créées à partir d'un ensemble de colonnes qui identifient uniquement les lignes de l'ensemble de résultats. Le jeu de clés est l’ensemble de valeurs de clés à partir de toutes les lignes retournées par l’instruction de requête.  
  
 Avec les curseurs, une clé est générée et enregistrée pour chaque ligne du curseur et stockée sur la station de travail cliente ou sur le serveur. Lorsque vous accédez à chaque ligne, la clé stockée est utilisée pour extraire les valeurs de données actuelles de la source de données. Dans un curseur keyset, l’appartenance au jeu de résultats est figée lorsque le jeu de clés est pleine. Par la suite, ajouts ou mises à jour affectant l’appartenance ne sont pas une partie du résultat défini jusqu'à ce qu’il est rouvert.  
  
 Modifications apportées aux valeurs de données (effectuées par le propriétaire du jeu de clés ou d’autres processus) sont visibles lorsque l’utilisateur fait défiler le jeu de résultats. Les insertions effectuées en dehors du curseur (par d’autres processus) sont visibles uniquement si le curseur est fermé et rouvert. Les insertions effectuées à l’intérieur du curseur sont visibles à la fin du jeu de résultats.  
  
 Lorsqu’un curseur keyset tente de récupérer une ligne qui a été supprimée, la ligne apparaît comme un « trou » dans le jeu de résultats. La clé pour la ligne existe dans le jeu de clés, mais la ligne n’existe plus dans le jeu de résultats. Si les valeurs de clé dans une ligne sont mis à jour, la ligne est considérée comme supprimée, puis inséré, par conséquent, ces lignes apparaissent également sous forme de trous dans le jeu de résultats. Pendant un curseur keyset peut toujours détecter les lignes supprimées par d’autres processus, il peut éventuellement supprimer les clés des lignes, qu'il se supprime lui-même. Curseurs que cela ne peut pas détecter leurs propres suppressions car la preuve a été supprimée.  
  
 Une mise à jour à une colonne clé équivaut à la suppression de l’ancienne clé suivie par une insertion de la nouvelle clé. La nouvelle valeur de clé n’est pas visible si la mise à jour n’a été pas effectuée via le curseur. Si la mise à jour a été effectuée via le curseur, la nouvelle valeur de clé est visible à la fin du jeu de résultats.  
  
 Il existe une variante des curseurs appelés curseurs standards. Dans un curseur standard par keyset, l’appartenance des lignes du jeu de résultats et l’ordre des lignes sont fixés à l’heure d’ouverture de curseur, mais les modifications apportées aux valeurs qui sont effectuées par le propriétaire du curseur et les modifications effectuées par d’autres processus sont visibles. Si une modification ne permet pas d’une ligne pour l’appartenance ou affecte l’ordre d’une ligne, la ligne ne disparaissent ni déplacé, sauf si le curseur est fermé et rouvert. Données insérées n’apparaissant pas, mais les modifications apportées aux données existantes s’affichent que les lignes sont extraites.  
  
 Le curseur keyset est difficile à utiliser correctement car la sensibilité aux modifications de données dépend des circonstances différentes, comme décrit ci-dessus. Toutefois, si votre application n’est pas concernée avec les mises à jour simultanées permettre gérer par programmation les mauvaises clés et devez accéder directement à certaines lignes dotées de clés, le curseur keyset peut fonctionner pour vous. Utiliser le **adOpenKeyset CursorTypeEnum** pour indiquer que vous souhaitez utiliser un curseur de jeu de clés dans ADO.  
  
## <a name="see-also"></a>Voir aussi  
 [Curseurs avant uniquement](../../../ado/guide/data/forward-only-cursors.md)   
 [Curseurs statiques](../../../ado/guide/data/static-cursors.md)   
 [Curseurs dynamiques](../../../ado/guide/data/dynamic-cursors.md)

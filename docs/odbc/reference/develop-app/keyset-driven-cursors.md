---
title: Curseurs | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- keyset-driven cursors [ODBC]
- cursors [ODBC], key-set driven
ms.assetid: 01769f43-1d9c-4685-84fa-15a6465335e9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0c40fe8c823115c3131a1719185bce8f1506df81
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138843"
---
# <a name="keyset-driven-cursors"></a>Curseurs de jeu de clés
Un curseur keyset se situe entre un statique et un curseur dynamique dans sa capacité à détecter les modifications. Comme un curseur statique, il ne détecte pas toujours les modifications apportées à l’appartenance et à l’ordre du jeu de résultats. Comme un curseur dynamique, il détecte les modifications apportées aux valeurs de lignes du jeu de résultats (selon le niveau d’isolation de la transaction, tel que défini par l’attribut de connexion SQL_ATTR_TXN_ISOLATION).  
  
 Lorsqu’un curseur est ouvert, il enregistre les clés pour le jeu de résultats entier ; Cela permet de corriger l’appartenance apparent et l’ordre du jeu de résultats. Lorsque le curseur fait défiler le jeu de résultats, il utilise les clés dans ce *keyset* pour récupérer les valeurs de données actuelle pour chaque ligne. Par exemple, un curseur keyset extrait une ligne et une autre application, puis met à jour de cette ligne. Si le curseur réextrait la ligne, les valeurs sont nouveaux, car il à nouveau extraites de la ligne à l’aide de sa clé. Pour cette raison, les curseurs de toujours détectent les modifications apportées par eux-mêmes et d’autres.  
  
 Lorsque le curseur tente de récupérer une ligne qui a été supprimée, cette ligne apparaît comme un « trou » dans le jeu de résultats : La clé pour la ligne existe dans le jeu de clés, mais la ligne n’existe plus dans le jeu de résultats. Si les valeurs de clé dans une ligne sont mis à jour, la ligne est considérée comme supprimée, puis inséré, par conséquent, ces lignes apparaissent également sous forme de trous dans le jeu de résultats. Pendant un curseur keyset peut toujours détecter les lignes supprimées par d’autres, il peut éventuellement supprimer les clés pour les lignes sont supprimées lui-même le jeu de clés. Curseurs que cela ne peut pas détecter leurs propres suppressions. Indique si un curseur keyset particulier détecte ses propres suppressions est signalé via l’option SQL_STATIC_SENSITIVITY dans **SQLGetInfo**.  
  
 Lignes insérées par d’autres ne sont jamais visibles par un curseur keyset, car aucune clé pour ces lignes n’existe dans le jeu de clés. Toutefois, un curseur keyset permettre éventuellement ajouter les clés pour les lignes qu’il s’insère pour le jeu de clés. Curseurs que cela peuvent détecter leurs propres insertions. Indique si un curseur keyset particulier détecte ses propres insertions est signalé via l’option SQL_STATIC_SENSITIVITY dans **SQLGetInfo**.  
  
 Le tableau d’état de ligne spécifié par l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR peut contenir SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO ou SQL_ROW_ERROR pour n’importe quelle ligne. Elle retourne SQL_ROW_UPDATED, SQL_ROW_DELETED, SQL_ROW_ADDED pour les lignes qu’il détecte une mise à jour, supprimées ou insérées.  
  
 Curseurs sont généralement implémentées en créant une table temporaire qui contient les clés pour chaque ligne du jeu de résultats. Étant donné que le curseur doit également déterminer si les lignes ont été mis à jour, cette table contient généralement une colonne avec des informations de versioning de ligne.  
  
 Pour faire défiler sur le jeu de résultats d’origine, le curseur keyset ouvre un curseur statique sur la table temporaire. Pour récupérer une ligne dans le jeu de résultats d’origine, le curseur récupère d’abord la clé appropriée à partir de la table temporaire, puis récupère les valeurs actuelles de la ligne. Si vous utilisez des curseurs de bloc, le curseur doit récupérer plusieurs lignes et les clés.

---
title: Curseurs de jeu de clés | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 814fca7d48f50aab51b6b4f7e34835be8c412e9c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306204"
---
# <a name="keyset-driven-cursors"></a>Curseurs de jeu de clés
Un curseur de jeu de clés se trouve entre un curseur statique et un curseur dynamique dans sa capacité à détecter des modifications. Comme un curseur statique, il ne détecte pas toujours les modifications apportées à l’appartenance et à l’ordre du jeu de résultats. À l’instar d’un curseur dynamique, il détecte les modifications apportées aux valeurs des lignes du jeu de résultats (selon le niveau d’isolation de la transaction, tel qu’il est défini par l’attribut de connexion SQL_ATTR_TXN_ISOLATION).  
  
 Lorsqu’un curseur de jeu de clés est ouvert, il enregistre les clés pour l’ensemble du jeu de résultats ; Cela résout l’appartenance et l’ordre évidents du jeu de résultats. Au fur et à mesure que le curseur fait défiler le jeu de résultats, il utilise les clés de ce *jeu* de clés pour récupérer les valeurs de données actuelles de chaque ligne. Par exemple, supposons qu’un curseur de jeu de clés extrait une ligne et qu’une autre application met à jour cette ligne. Si le curseur récupère à nouveau la ligne, les valeurs qu’elle voit sont les nouvelles, car elle a récupéré la ligne à l’aide de sa clé. Pour cette raison, les curseurs de jeu de clés détectent toujours les modifications effectuées par eux-mêmes, ainsi que d’autres.  
  
 Lorsque le curseur tente d’extraire une ligne qui a été supprimée, cette ligne apparaît sous la forme d’un « trou » dans le jeu de résultats : la clé de la ligne existe dans le jeu de clés, mais la ligne n’existe plus dans le jeu de résultats. Si les valeurs de clé d’une ligne sont mises à jour, la ligne est considérée comme supprimée puis insérée, de sorte que ces lignes apparaissent également sous forme de trous dans le jeu de résultats. Bien qu’un curseur piloté par jeu de clés puisse toujours détecter les lignes supprimées par d’autres, il peut éventuellement supprimer les clés pour les lignes qu’il supprime du jeu de clés. Les curseurs de jeu de clés qui effectuent cette opération ne peuvent pas détecter leurs propres suppressions. Le fait qu’un curseur de jeu de clés particulier détecte ses propres suppressions est signalé par l’option SQL_STATIC_SENSITIVITY dans **SQLGetInfo**.  
  
 Les lignes insérées par d’autres ne sont jamais visibles par un curseur de jeu de clés, car il n’existe aucune clé pour ces lignes dans le jeu de clés. Toutefois, un curseur piloté par jeu de clés peut éventuellement ajouter les clés pour les lignes qu’il insère lui-même dans le jeu de clés. Les curseurs de jeu de clés qui le permettent peuvent détecter leurs propres insertions. Le fait qu’un curseur de jeu de clés particulier détecte ses propres insertions est signalé par l’option SQL_STATIC_SENSITIVITY dans **SQLGetInfo**.  
  
 Le tableau d’état de ligne spécifié par l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR peut contenir SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO ou SQL_ROW_ERROR pour n’importe quelle ligne. Il retourne SQL_ROW_UPDATED, SQL_ROW_DELETED ou SQL_ROW_ADDED pour les lignes qu’il détecte comme mis à jour, supprimé ou inséré.  
  
 Les curseurs de jeu de clés sont généralement implémentés en créant une table temporaire qui contient les clés pour chaque ligne du jeu de résultats. Étant donné que le curseur doit également déterminer si des lignes ont été mises à jour, cette table contient également une colonne avec des informations sur le contrôle de version de ligne.  
  
 Pour faire défiler le jeu de résultats d’origine, le curseur de jeu de clés ouvre un curseur statique sur la table temporaire. Pour récupérer une ligne dans le jeu de résultats d’origine, le curseur récupère d’abord la clé appropriée de la table temporaire, puis récupère les valeurs actuelles de la ligne. Si des curseurs de bloc sont utilisés, le curseur doit récupérer plusieurs clés et lignes.

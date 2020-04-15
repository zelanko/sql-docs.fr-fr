---
title: Keyset-Driven Cursors (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306204"
---
# <a name="keyset-driven-cursors"></a>Curseurs de jeu de clés
Un curseur à clé se trouve entre un curseur statique et un curseur dynamique dans sa capacité à détecter les changements. Comme un curseur statique, il ne détecte pas toujours les modifications apportées à l’appartenance et à l’ordre du jeu de résultats. Comme un curseur dynamique, il détecte des changements dans les valeurs des lignes dans l’ensemble de résultats (sous réserve du niveau d’isolement de la transaction, tel qu’établi par l’attribut de connexion SQL_ATTR_TXN_ISOLATION).  
  
 Lorsqu’un curseur à clé est ouvert, il enregistre les clés pour l’ensemble du résultat; cela corrige l’adhésion apparente et l’ordre de l’ensemble de résultats. Comme le curseur défile à travers l’ensemble de résultat, il utilise les touches de ce *jeu de clés* pour récupérer les valeurs de données actuelles pour chaque ligne. Supposons, par exemple, qu’un curseur à clé récupère une ligne et qu’une autre application met à jour cette ligne. Si le curseur refaçonner la ligne, les valeurs qu’il voit sont les nouvelles parce qu’il a recadré la ligne à l’aide de sa clé. Pour cette raison, les curseurs à clé détectent toujours les changements apportés par eux-mêmes et les autres.  
  
 Lorsque le curseur tente de récupérer une ligne qui a été supprimée, cette ligne apparaît comme un «trou» dans l’ensemble de résultat: La clé pour la ligne existe dans le jeu de clés, mais la ligne n’existe plus dans l’ensemble de résultats. Si les valeurs clés d’une rangée sont mises à jour, la ligne est considérée comme ayant été supprimée puis insérée, de sorte que ces lignes apparaissent également comme des trous dans l’ensemble de résultats. Bien qu’un curseur piloté par keyset puisse toujours détecter les lignes supprimées par d’autres, il peut en option supprimer les touches pour les lignes qu’il se supprime de l’ensemble de clés. Les curseurs pilotés par Keyset qui le font ne peuvent pas détecter leurs propres suppressions. La question de savoir si un curseur à clé particulière détecte ses propres suppressions est signalée par l’option SQL_STATIC_SENSITIVITY dans **SQLGetInfo**.  
  
 Les lignes insérées par d’autres ne sont jamais visibles par un curseur à clé parce qu’aucune clé pour ces lignes n’existe dans le jeu de clés. Cependant, un curseur à jeu de clés peut en option ajouter les touches pour les lignes qu’il s’insère à l’ensemble de touches. Les curseurs pilotés par Keyset qui font cela peuvent détecter leurs propres inserts. La question de savoir si un curseur à clé particulière détecte ses propres inserts est signalée par l’option SQL_STATIC_SENSITIVITY dans **SQLGetInfo**.  
  
 Le tableau d’état de la ligne spécifié par l’attribut de l’instruction SQL_ATTR_ROW_STATUS_PTR peut contenir SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO ou SQL_ROW_ERROR pour n’importe quelle rangée. Il renvoie SQL_ROW_UPDATED, SQL_ROW_DELETED ou SQL_ROW_ADDED pour les lignes qu’il détecte comme mises à jour, supprimées ou insérées.  
  
 Les curseurs pilotés par Keyset sont généralement mis en œuvre en créant une table temporaire qui contient les clés de chaque rangée dans l’ensemble de résultats. Étant donné que le curseur doit également déterminer si les lignes ont été mises à jour, ce tableau contient également généralement une colonne avec des informations de version de ligne.  
  
 Pour faire défiler l’ensemble de résultats d’origine, le curseur à clé ouvre un curseur statique sur la table temporaire. Pour récupérer une ligne dans l’ensemble de résultat d’origine, le curseur récupère d’abord la clé appropriée de la table temporaire, puis récupère les valeurs actuelles pour la ligne. Si des curseurs de blocs sont utilisés, le curseur doit récupérer plusieurs clés et lignes.

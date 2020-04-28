---
title: Mise à jour, suppression ou extraction par signet | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating by bookmarks [ODBC]
- result sets [ODBC], bookmarks
- fetches [ODBC], by bookmarks [ODBC]
- deleting by bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: e2ee58d7-c28f-435f-b537-06207215dd2f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5e94a98bb577ef906afbb04539761fd07d15f772
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81286149"
---
# <a name="updating-deleting-or-fetching-by-bookmark"></a>Mise à jour, suppression ou extraction par signet
Les signets peuvent être utilisés pour identifier les données à mettre à jour dans le jeu de résultats, supprimées du jeu de résultats ou extraites du jeu de résultats vers les tampons de l’ensemble de lignes. Ces opérations sont effectuées par un appel à **SQLBulkOperations** avec un argument *option* de SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK ou SQL_FETCH_BY_BOOKMARK. Les signets utilisés dans ces opérations sont stockés dans la colonne 0 des mémoires tampons de l’ensemble de lignes. Lors de la mise à jour par signet, les données auxquelles les colonnes du jeu de résultats sont mises à jour sont récupérées à partir des mémoires tampons de l’ensemble de lignes. Pour plus d’informations, consultez [mise à jour des données avec SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md).

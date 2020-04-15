---
title: Mise à jour, suppression ou fetching par Bookmark ( Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286149"
---
# <a name="updating-deleting-or-fetching-by-bookmark"></a>Mise à jour, suppression ou extraction par signet
Les signets peuvent être utilisés pour identifier les données à mettre à jour dans l’ensemble de résultats, supprimés de l’ensemble de résultats ou récupérés à partir du résultat réglé sur les tampons encastrés. Ces opérations sont effectuées par un appel à **SQLBulkOperations** avec un argument *Option* de SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK, ou SQL_FETCH_BY_BOOKMARK. Les signets utilisés dans ces opérations sont stockés dans la colonne 0 des tampons encastrés. Lors de la mise à jour par signet, les données dont les colonnes de l’ensemble de résultats sont mises à jour sont extraites des tampons encastrés. Pour plus d’informations, voir [Mise à jour des données avec SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md).

---
title: Mise à jour, la suppression ou l’extraction par le signet | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- updating by bookmarks [ODBC]
- result sets [ODBC], bookmarks
- fetches [ODBC], by bookmarks [ODBC]
- deleting by bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: e2ee58d7-c28f-435f-b537-06207215dd2f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 905278d3bb7100f1db05a2dea99ced009d21deb3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="updating-deleting-or-fetching-by-bookmark"></a>Mise à jour, la suppression ou l’extraction par le signet
Signets peuvent être utilisés pour identifier les données à jour dans le jeu de résultats, supprimé à partir du résultat définie ou récupérée depuis le jeu de résultats pour les tampons de l’ensemble de lignes. Ces opérations sont effectuées par un appel à **SQLBulkOperations** avec un *Option* argument de SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK ou SQL_FETCH_BY_BOOKMARK. Les signets utilisées dans ces opérations sont stockés dans des tampons de lignes de la colonne 0. Lors de la mise à jour par un signet, qui résultent des colonnes du jeu de données sont mises à jour est récupérée à partir de mémoires tampons de l’ensemble de lignes. Pour plus d’informations, consultez [mise à jour des données avec SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md).

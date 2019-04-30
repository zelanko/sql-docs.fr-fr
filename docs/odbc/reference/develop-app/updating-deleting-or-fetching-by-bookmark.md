---
title: La mise à jour, suppression ou extraction par signet | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c5af3cad39739c3b85a0c6298d682d8e75a5918d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63151221"
---
# <a name="updating-deleting-or-fetching-by-bookmark"></a>Mise à jour, suppression ou extraction par signet
Signets peuvent être utilisés pour identifier les données à mettre à jour du jeu de résultats, supprimé à partir du résultat de définir ou extraire le jeu de résultats dans les mémoires tampons d’ensemble de lignes. Ces opérations sont effectuées par un appel à **SQLBulkOperations** avec un *Option* argument de SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK ou SQL_FETCH_BY_BOOKMARK. Les signets utilisées dans ces opérations sont stockées dans la colonne 0 de mémoires tampons de l’ensemble de lignes. Lors de la mise à jour par signet, les données des colonnes de jeu de résultats sont mis à jour est récupérée à partir de mémoires tampons de l’ensemble de lignes. Pour plus d’informations, consultez [la mise à jour des données avec SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md).

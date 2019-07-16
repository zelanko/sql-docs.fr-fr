---
title: Ajouter des signets aux lignes dans ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- ODBC cursors, scrolling rows
- bookmarks [ODBC]
ms.assetid: 9cfcd243-c9d4-4c2a-abc4-399dbabe5f6b
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 40180e8f2fe9b4f77546dd95da1813eec6ce1f96
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68078824"
---
# <a name="scrolling-and-fetching-rows---bookmarking-rows-in-odbc"></a>Défilement et récupération (fetch) de lignes - Ajout de signets aux lignes dans ODBC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Un signet est une valeur utilisée pour identifier une ligne de données. La signification de la valeur du signet est connue uniquement du pilote ou de la source de données. Par exemple, il peut être aussi simple qu'un numéro de ligne ou aussi complexe qu'une adresse disque. Dans ODBC, l'application demande un signet pour une ligne particulière, le stocke, puis le passe au curseur à retourner à la ligne.  
  
 Lors de l’extraction des lignes avec [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md), une application peut utiliser un signet comme base pour la sélection de la ligne de départ. Il s'agit d'une forme d'adressage absolu qui ne dépend pas de la position actuelle du curseur. Pour accéder à une ligne marquée par un signet, l’application appelle **SQLFetchScroll** avec un *FetchOrientation* de SQL_FETCH_BOOKMARK. Cette opération utilise le signet vers lequel pointe l'attribut d'option SQL_ATTR_FETCH_BOOKMARK_PTR. Elle retourne l'ensemble de lignes démarrant à la ligne identifiée par ce signet. Une application peut spécifier un décalage pour cette opération dans le *FetchOffset* argument de l’appel à **SQLFetchScroll**. Lorsqu'un décalage est spécifié, la première ligne de l'ensemble de lignes retourné est déterminée par l'ajout du nombre présent dans l'argument FetchOffset au numéro de la ligne identifiée par le signet. Le pilote ODBC de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend en charge uniquement les signets sur les curseurs statiques et les curseurs de jeu de clés. Si un curseur dynamique est demandé lorsque les signets sont définis, un curseur de jeu de clés est ouvert à la place.  
  
 Signets peuvent également être utilisés avec la **SQLBulkOperations** (fonction) pour effectuer des opérations sur un ensemble de lignes démarrant au signet.  
  
## <a name="see-also"></a>Voir aussi  
 [Défilement et récupération (fetch) de lignes](../../relational-databases/native-client-odbc-cursors/scrolling-and-fetching-rows.md)  
  
  

---
title: Faire défiler par Bookmark Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
- scrolling rows [ODBC]
ms.assetid: 4862f098-41a4-4bd2-894e-f71bb97f9bc0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 454e29abdf848fdf4f4eaae090e7cc326f0048df
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304190"
---
# <a name="scrolling-by-bookmark"></a>Défilement par signet
Lorsque vous allez chercher des rangées avec **SQLFetchScroll**, une application peut utiliser un signet comme base pour sélectionner la ligne de départ. Il s'agit d'une forme d'adressage absolu qui ne dépend pas de la position actuelle du curseur. Pour faire défiler vers une rangée de signets, l’application appelle **SQLFetchScroll** avec une *fetchOrientation* de SQL_FETCH_BOOKMARK. Cette opération utilise le signet indiqué par l’attribut de l’SQL_ATTR_FETCH_BOOKMARK_PTR déclaration. Elle retourne l'ensemble de lignes démarrant à la ligne identifiée par ce signet. Une demande peut spécifier une compensation pour cette opération dans l’argument *FetchOffset* de l’appel à **SQLFetchScroll**. Lorsqu’un décalage est spécifié, la première rangée de l’ensemble de rangée retournées est déterminée en ajoutant le nombre dans l’argument *FetchOffset* au nombre de la ligne identifiée par le signet. Cette utilisation de l’argument *FetchOffset* n’est pas étayée lorsqu’elle est utilisée avec ODBC 2. *x* conducteurs; lorsqu’une application appelle **SQLFetchScroll** dans un ODBC 2. *x* pilote avec *FetchOrientation* mis à SQL_FETCH_BOOKMARK, l’argument *FetchOffset* doit être réglé à 0.

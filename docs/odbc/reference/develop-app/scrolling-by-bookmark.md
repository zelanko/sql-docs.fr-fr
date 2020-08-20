---
description: Défilement par signet
title: Défilement par signet | Microsoft Docs
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
ms.openlocfilehash: 52ef0813f3f9fd3f2d139a2549000c629943109e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476471"
---
# <a name="scrolling-by-bookmark"></a>Défilement par signet
Lors de l’extraction de lignes avec **SQLFetchScroll**, une application peut utiliser un signet comme base pour la sélection de la ligne de départ. Il s'agit d'une forme d'adressage absolu qui ne dépend pas de la position actuelle du curseur. Pour faire défiler jusqu’à une ligne avec signet, l’application appelle **SQLFetchScroll** avec un *FetchOrientation* de SQL_FETCH_BOOKMARK. Cette opération utilise le signet désigné par l’attribut d’instruction SQL_ATTR_FETCH_BOOKMARK_PTR. Elle retourne l'ensemble de lignes démarrant à la ligne identifiée par ce signet. Une application peut spécifier un décalage pour cette opération dans l’argument *FetchOffset* de l’appel à **SQLFetchScroll**. Lorsqu’un offset est spécifié, la première ligne de l’ensemble de lignes retourné est déterminée en ajoutant le nombre de l’argument *FetchOffset* au numéro de la ligne identifiée par le signet. Cette utilisation de l’argument *FetchOffset* n’est pas prise en charge lorsqu’elle est utilisée avec ODBC 2. *x* pilotes ; Quand une application appelle **SQLFetchScroll** dans ODBC 2. *x* avec *FetchOrientation* défini sur SQL_FETCH_BOOKMARK, l’argument *FetchOffset* doit avoir la valeur 0.

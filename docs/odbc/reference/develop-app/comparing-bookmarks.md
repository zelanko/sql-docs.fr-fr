---
description: Comparaison de signets
title: Comparaison des signets | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- comparing bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: ea347635-fbe3-41c1-b537-4048b7c0f7da
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 939c3780fc9c6738a307e9a969a346951cfac5e7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476781"
---
# <a name="comparing-bookmarks"></a>Comparaison de signets
Comme les signets sont comparables en octets, ils peuvent être comparés à des fins d’égalité ou d’inégalité. Pour ce faire, une application traite chaque signet comme un tableau d’octets et compare deux signets octet par octet. Étant donné que les signets sont garantis comme étant distincts uniquement dans un jeu de résultats, il n’est pas judicieux de comparer les signets obtenus à partir de différents jeux de résultats.

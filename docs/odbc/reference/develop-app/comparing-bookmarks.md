---
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
ms.openlocfilehash: c28392c0d48984b4aaf8a8df442b6a4054a7eced
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307474"
---
# <a name="comparing-bookmarks"></a>Comparaison de signets
Comme les signets sont comparables en octets, ils peuvent être comparés à des fins d’égalité ou d’inégalité. Pour ce faire, une application traite chaque signet comme un tableau d’octets et compare deux signets octet par octet. Étant donné que les signets sont garantis comme étant distincts uniquement dans un jeu de résultats, il n’est pas judicieux de comparer les signets obtenus à partir de différents jeux de résultats.

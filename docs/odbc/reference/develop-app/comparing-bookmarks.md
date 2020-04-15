---
title: Comparaison des signets Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307474"
---
# <a name="comparing-bookmarks"></a>Comparaison de signets
Parce que les signets sont parte-comparables, ils peuvent être comparés pour l’égalité ou l’inégalité. Pour ce faire, une application traite chaque signets comme un tableau d’octets et compare deux signets byte-by-byte. Étant donné que les signets sont garantis d’être distincts uniquement dans un ensemble de résultats, il n’est pas logique de comparer les signets qui ont été obtenus à partir de différents ensembles de résultats.

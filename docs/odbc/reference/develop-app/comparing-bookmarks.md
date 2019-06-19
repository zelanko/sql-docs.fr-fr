---
title: Comparaison de signets | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 690acf80bfabdc04d5f70b780e41943337c18cb9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63026613"
---
# <a name="comparing-bookmarks"></a>Comparaison de signets
Étant donné que les signets sont comparables à l’octet, ils peuvent être comparées pour l’égalité ou d’inégalité. Pour ce faire, une application traite chaque signet comme un tableau d’octets et compare les deux signets octet par octet. Étant donné que les signets sont assurées d’être distinctes uniquement au sein d’un jeu de résultats, il n’a aucun sens pour comparer des signets qui ont été obtenues à partir de jeux de résultats.

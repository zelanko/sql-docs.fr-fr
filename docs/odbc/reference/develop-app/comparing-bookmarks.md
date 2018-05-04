---
title: Comparaison des signets | Documents Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- comparing bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: ea347635-fbe3-41c1-b537-4048b7c0f7da
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 05d1d66c7eec8f1e02d4195a6bf09d35c3d28203
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="comparing-bookmarks"></a>Comparaison des signets
Étant donné que les signets sont comparables en termes d’octets, elles pouvant être comparés en égalité ou d’inégalité. Pour ce faire, une application traite chaque signet sous forme de tableau d’octets et compare les deux signets octet par octet. Étant donné que les signets sont assurées d’être distinctes uniquement dans un jeu de résultats, il n’est pas justifiée pour comparer des signets qui ont été obtenues à partir de jeux de résultats.

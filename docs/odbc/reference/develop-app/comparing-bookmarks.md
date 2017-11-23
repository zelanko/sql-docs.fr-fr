---
title: Comparaison des signets | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- result sets [ODBC], bookmarks
- comparing bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: ea347635-fbe3-41c1-b537-4048b7c0f7da
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c3d26095cf879859e6ea74784fcf87694ba5eb5d
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="comparing-bookmarks"></a>Comparaison des signets
Étant donné que les signets sont comparables en termes d’octets, elles pouvant être comparés en égalité ou d’inégalité. Pour ce faire, une application traite chaque signet sous forme de tableau d’octets et compare les deux signets octet par octet. Étant donné que les signets sont assurées d’être distinctes uniquement dans un jeu de résultats, il n’est pas justifiée pour comparer des signets qui ont été obtenues à partir de jeux de résultats.

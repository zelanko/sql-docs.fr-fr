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
ms.topic: article
helpviewer_keywords:
- result sets [ODBC], bookmarks
- comparing bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: ea347635-fbe3-41c1-b537-4048b7c0f7da
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 44561e4386353ef1efaf3dd41e5a24b93941963d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="comparing-bookmarks"></a>Comparaison des signets
Étant donné que les signets sont comparables en termes d’octets, elles pouvant être comparés en égalité ou d’inégalité. Pour ce faire, une application traite chaque signet sous forme de tableau d’octets et compare les deux signets octet par octet. Étant donné que les signets sont assurées d’être distinctes uniquement dans un jeu de résultats, il n’est pas justifiée pour comparer des signets qui ont été obtenues à partir de jeux de résultats.

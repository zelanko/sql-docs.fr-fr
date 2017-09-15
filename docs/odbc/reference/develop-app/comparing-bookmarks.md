---
title: Comparaison des signets | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- result sets [ODBC], bookmarks
- comparing bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: ea347635-fbe3-41c1-b537-4048b7c0f7da
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7ebcf375311af498dbb4c777707b7febcddb05a3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="comparing-bookmarks"></a>Comparaison des signets
Étant donné que les signets sont comparables en termes d’octets, elles pouvant être comparés en égalité ou d’inégalité. Pour ce faire, une application traite chaque signet sous forme de tableau d’octets et compare les deux signets octet par octet. Étant donné que les signets sont assurées d’être distinctes uniquement dans un jeu de résultats, il n’est pas justifiée pour comparer des signets qui ont été obtenues à partir de jeux de résultats.

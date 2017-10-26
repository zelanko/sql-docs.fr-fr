---
title: Identificateur cas | Documents Microsoft
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
- SQL statements [ODBC], interoperability
- identifiers [ODBC], case
- interoperability of SQL statements [ODBC], identifier case
ms.assetid: ee8a31aa-389d-4dd1-bfa9-547f6b50bc70
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c55118fa47337425e715a8b3d6409525668e383f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="identifier-case"></a>Cas d’identificateur
Dans les instructions SQL et les arguments de fonction de catalogue, les identificateurs et les identificateurs entre guillemets peuvent être sensible à la casse ou pas, une application peut déterminer en appelant **SQLGetInfo** avec les options SQL_IDENTIFIER_CASE et SQL_QUOTED_IDENTIFIER_CASE.  
  
 Chacune de ces options a quatre valeurs de retour possibles : un indiquant que l’identificateur ou la casse de l’identificateur entre guillemets est sensible et trois indiquant qu’il n’est pas sensible. Les trois valeurs qui ne respectent pas la casse décrivent plus précisément le cas dans lequel les identificateurs sont stockés dans le catalogue système. Comment les identificateurs sont stockés dans le catalogue système ne s’applique uniquement à des fins d’affichage, telles que lorsqu’une application affiche les résultats d’une fonction de catalogue ; Il ne modifie pas le respect de la casse des identificateurs.


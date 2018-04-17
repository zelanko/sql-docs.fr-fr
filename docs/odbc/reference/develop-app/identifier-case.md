---
title: Identificateur cas | Documents Microsoft
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
- SQL statements [ODBC], interoperability
- identifiers [ODBC], case
- interoperability of SQL statements [ODBC], identifier case
ms.assetid: ee8a31aa-389d-4dd1-bfa9-547f6b50bc70
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 122f4dfdfab25f246858b36f7753413d25f2eea4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="identifier-case"></a>Cas d’identificateur
Dans les instructions SQL et les arguments de fonction de catalogue, les identificateurs et les identificateurs entre guillemets peuvent être sensible à la casse ou pas, une application peut déterminer en appelant **SQLGetInfo** avec les options SQL_IDENTIFIER_CASE et SQL_QUOTED_IDENTIFIER_CASE.  
  
 Chacune de ces options a quatre valeurs de retour possibles : un indiquant que l’identificateur ou la casse de l’identificateur entre guillemets est sensible et trois indiquant qu’il n’est pas sensible. Les trois valeurs qui ne respectent pas la casse décrivent plus précisément le cas dans lequel les identificateurs sont stockés dans le catalogue système. Comment les identificateurs sont stockés dans le catalogue système ne s’applique uniquement à des fins d’affichage, telles que lorsqu’une application affiche les résultats d’une fonction de catalogue ; Il ne modifie pas le respect de la casse des identificateurs.

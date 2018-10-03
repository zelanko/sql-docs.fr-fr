---
title: Casse de l’identificateur | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- identifiers [ODBC], case
- interoperability of SQL statements [ODBC], identifier case
ms.assetid: ee8a31aa-389d-4dd1-bfa9-547f6b50bc70
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6445cffd5faa8b825c81ec729d7b28c90e14a7b3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47678349"
---
# <a name="identifier-case"></a>Casse des identificateurs
Dans les instructions SQL et les arguments de fonction de catalogue, identificateurs et les identificateurs entre guillemets peuvent être respect de la casse ou non, pour laquelle une application peut déterminer en appelant **SQLGetInfo** avec le SQL_IDENTIFIER_CASE et SQL_QUOTED_ Options de IDENTIFIER_CASE.  
  
 Chacune de ces options a quatre valeurs de retour possibles : un indiquant que l’identificateur ou la casse de l’identificateur entre guillemets est sensible et trois indiquant qu’il n’est pas sensible. Les trois valeurs qui ne respectent pas la casse mieux décrivent le cas dans lequel les identificateurs sont stockés dans le catalogue système. Comment les identificateurs sont stockées dans le catalogue système s’applique uniquement à des fins d’affichage, par exemple quand une application affiche les résultats d’une fonction de catalogue ; Il ne modifie pas le respect de la casse des identificateurs.

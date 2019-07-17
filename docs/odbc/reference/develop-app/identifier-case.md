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
ms.openlocfilehash: 70728908f081ab89e08cad1265f04394f29b66ef
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138972"
---
# <a name="identifier-case"></a>Casse des identificateurs
Dans les instructions SQL et les arguments de fonction de catalogue, identificateurs et les identificateurs entre guillemets peuvent être respect de la casse ou non, pour laquelle une application peut déterminer en appelant **SQLGetInfo** avec le SQL_IDENTIFIER_CASE et SQL_QUOTED_ Options de IDENTIFIER_CASE.  
  
 Chacune de ces options a quatre valeurs de retour possibles : un indiquant que l’identificateur ou la casse de l’identificateur entre guillemets est sensible et trois indiquant qu’il n’est pas sensible. Les trois valeurs qui ne respectent pas la casse mieux décrivent le cas dans lequel les identificateurs sont stockés dans le catalogue système. Comment les identificateurs sont stockées dans le catalogue système s’applique uniquement à des fins d’affichage, par exemple quand une application affiche les résultats d’une fonction de catalogue ; Il ne modifie pas le respect de la casse des identificateurs.

---
title: Cas de l’identificateur | Microsoft Docs
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138972"
---
# <a name="identifier-case"></a>Casse des identificateurs
Dans les instructions SQL et les arguments de fonction de catalogue, les identificateurs et les identificateurs entre guillemets peuvent être sensibles à la casse ou non, qu’une application peut déterminer en appelant **SQLGetInfo** avec les options SQL_IDENTIFIER_CASE et SQL_QUOTED_IDENTIFIER_CASE.  
  
 Chacune de ces options a quatre valeurs de retour possibles : l’une indiquant que la casse de l’identificateur ou de l’identificateur entre guillemets est sensible et trois indique qu’elle n’est pas sensible. Les trois valeurs qui ne respectent pas la casse décrivent plus en détail le cas dans lequel les identificateurs sont stockés dans le catalogue système. Le mode de stockage des identificateurs dans le catalogue système s’applique uniquement à des fins d’affichage, par exemple lorsqu’une application affiche les résultats d’une fonction de catalogue ; elle ne modifie pas le respect de la casse des identificateurs.

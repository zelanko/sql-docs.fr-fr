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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 940d96ece6b2c344fa02e0daadd6248270f4d19e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300149"
---
# <a name="identifier-case"></a>Casse des identificateurs
Dans les instructions SQL et les arguments de fonction de catalogue, les identificateurs et les identificateurs entre guillemets peuvent être sensibles à la casse ou non, qu’une application peut déterminer en appelant **SQLGetInfo** avec les options SQL_IDENTIFIER_CASE et SQL_QUOTED_IDENTIFIER_CASE.  
  
 Chacune de ces options a quatre valeurs de retour possibles : l’une indiquant que la casse de l’identificateur ou de l’identificateur entre guillemets est sensible et trois indique qu’elle n’est pas sensible. Les trois valeurs qui ne respectent pas la casse décrivent plus en détail le cas dans lequel les identificateurs sont stockés dans le catalogue système. Le mode de stockage des identificateurs dans le catalogue système s’applique uniquement à des fins d’affichage, par exemple lorsqu’une application affiche les résultats d’une fonction de catalogue ; elle ne modifie pas le respect de la casse des identificateurs.

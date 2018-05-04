---
title: Types de signet | Documents Microsoft
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
- variable-length bookmarks [ODBC]
- bookmarks [ODBC]
- fixed-length bookmarks [ODBC]
ms.assetid: cb2e7443-0260-4d1a-930f-0154db447979
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a9a8f6fb698e55e2a5de623bfa4252468ba655ee
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="bookmark-types"></a>Types de signet
Tous les signets dans ODBC 3 *.x* sont des signets de longueur variable. Cela permet une clé primaire ou un index unique associé à une table à utiliser comme un signet. Le signet peut également être une valeur 32 bits, que celui utilisé dans ODBC 2. *x*. Pour spécifier qu’un signet est utilisé avec un curseur, une ODBC 3 *.x* application définit l’attribut d’instruction SQL_ATTR_USE_BOOKMARK à SQL_UB_VARIABLE. Un signet de longueur variable est automatiquement utilisé.  
  
 Une application peut appeler **SQLColAttribute** avec la *FieldIdentifier* argument valeur SQL_DESC_OCTET_LENGTH pour obtenir la longueur du signet. Un signet de longueur variable pouvant être une valeur de type long, une application doit lier la colonne 0, sauf si elle utilise le signet pour un grand nombre de lignes dans l’ensemble de lignes.  
  
 Les signets de longueur fixe sont pris en charge uniquement pour la compatibilité descendante. If un ODBC 2. *x* application utilisant une ODBC 3 *.x* pilote appelle **SQLSetStmtOption** pour définir SQL_USE_BOOKMARKS SQL_UB_ON, il est mappé à SQL_UB_VARIABLE dans le Gestionnaire de pilotes. Un signet de longueur variable est utilisé, même si uniquement 32 bits de celui-ci sont remplies. Si un pilote prend en charge les signets de longueur fixe, il prendra en charge des signets de longueur variable. Si un ODBC 3 *.x* application utilisant une API ODBC 2. *x* pilote appelle **SQLSetStmtAttr** pour définir SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE, il est mappé dans le Gestionnaire de pilotes à SQL_UB_ON et un signet de longueur fixe de 32 bits est utilisé. L’attribut d’instruction SQL_ATTR_FETCH_BOOKMARK_PTR doit ensuite pointer vers un signet 32 bits. Si les signets utilisés sont plus de 32 bits, notamment lorsque les clés primaires sont utilisées en tant que signets, le curseur doit mapper les valeurs réelles aux valeurs de 32 bits. Il pourrait, par exemple, créer une table de hachage d’eux. Lorsqu’un ODBC 3 *.x* application utilisant une API ODBC 2. *x* pilote lie un signet, la longueur de la mémoire tampon doit être de 4.

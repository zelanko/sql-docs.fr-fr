---
title: Types de signet | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- result sets [ODBC], bookmarks
- variable-length bookmarks [ODBC]
- bookmarks [ODBC]
- fixed-length bookmarks [ODBC]
ms.assetid: cb2e7443-0260-4d1a-930f-0154db447979
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8ae130125c99e6ff87fd3b2d6fa8563c75f7e6ba
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="bookmark-types"></a>Types de signet
Tous les signets dans ODBC 3*.x* sont des signets de longueur variable. Cela permet une clé primaire ou un index unique associé à une table à utiliser comme un signet. Le signet peut également être une valeur 32 bits, que celui utilisé dans ODBC 2. *x*. Pour spécifier qu’un signet est utilisé avec un curseur, une ODBC 3*.x* application définit l’attribut d’instruction SQL_ATTR_USE_BOOKMARK à SQL_UB_VARIABLE. Un signet de longueur variable est automatiquement utilisé.  
  
 Une application peut appeler **SQLColAttribute** avec la *FieldIdentifier* argument valeur SQL_DESC_OCTET_LENGTH pour obtenir la longueur du signet. Un signet de longueur variable pouvant être une valeur de type long, une application doit lier la colonne 0, sauf si elle utilise le signet pour un grand nombre de lignes dans l’ensemble de lignes.  
  
 Les signets de longueur fixe sont pris en charge uniquement pour la compatibilité descendante. If un ODBC 2. *x* application utilisant une ODBC 3*.x* pilote appelle **SQLSetStmtOption** pour définir SQL_USE_BOOKMARKS SQL_UB_ON, il est mappé à SQL_UB_VARIABLE dans le Gestionnaire de pilotes. Un signet de longueur variable est utilisé, même si uniquement 32 bits de celui-ci sont remplies. Si un pilote prend en charge les signets de longueur fixe, il prendra en charge des signets de longueur variable. Si un ODBC 3*.x* application utilisant une API ODBC 2. *x* pilote appelle **SQLSetStmtAttr** pour définir SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE, il est mappé dans le Gestionnaire de pilotes à SQL_UB_ON et un signet de longueur fixe de 32 bits est utilisé. L’attribut d’instruction SQL_ATTR_FETCH_BOOKMARK_PTR doit ensuite pointer vers un signet 32 bits. Si les signets utilisés sont plus de 32 bits, notamment lorsque les clés primaires sont utilisées en tant que signets, le curseur doit mapper les valeurs réelles aux valeurs de 32 bits. Il pourrait, par exemple, créer une table de hachage d’eux. Lorsqu’un ODBC 3*.x* application utilisant une API ODBC 2. *x* pilote lie un signet, la longueur de la mémoire tampon doit être de 4.

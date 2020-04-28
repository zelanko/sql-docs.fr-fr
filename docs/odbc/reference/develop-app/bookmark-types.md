---
title: Types de signets | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- variable-length bookmarks [ODBC]
- bookmarks [ODBC]
- fixed-length bookmarks [ODBC]
ms.assetid: cb2e7443-0260-4d1a-930f-0154db447979
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 26d0297cd9dc57e9f30945a9248b235ae469da3e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306330"
---
# <a name="bookmark-types"></a>Types de signets
Tous les signets dans ODBC *3. x* sont des signets de longueur variable. Cela permet d’utiliser une clé primaire ou un index unique associé à une table en tant que signet. Le signet peut également être une valeur 32 bits, telle qu’elle a été utilisée dans ODBC *2. x*. Pour spécifier qu’un signet est utilisé avec un curseur, une application ODBC *3. x* définit l’attribut d’instruction SQL_ATTR_USE_BOOKMARK sur SQL_UB_VARIABLE. Un signet de longueur variable est automatiquement utilisé.  
  
 Une application peut appeler **SQLColAttribute** avec l’argument *FieldIdentifier* défini sur SQL_DESC_OCTET_LENGTH pour obtenir la longueur du signet. Comme un signet de longueur variable peut être une valeur longue, une application ne doit pas être liée à la colonne 0, sauf si elle utilise le signet pour la plupart des lignes de l’ensemble de lignes.  
  
 Les signets de longueur fixe ne sont pris en charge que pour la compatibilité descendante. Si une application ODBC *2. x* qui utilise un pilote ODBC *3. x* appelle **SQLSetStmtOption** pour définir SQL_USE_BOOKMARKS sur SQL_UB_ON, elle est mappée dans le gestionnaire de pilotes pour SQL_UB_VARIABLE. Un signet de longueur variable est utilisé, même si seuls 32 bits sont remplis. Si un pilote prend en charge les signets de longueur fixe, il prend en charge les signets de longueur variable. Si une application ODBC *3. x* qui utilise un pilote ODBC *2. x* appelle **SQLSetStmtAttr** pour définir SQL_ATTR_USE_BOOKMARKS sur SQL_UB_VARIABLE, elle est mappée dans le gestionnaire de pilotes à SQL_UB_ON et un signet de longueur fixe 32 bits est utilisé. L’attribut d’instruction SQL_ATTR_FETCH_BOOKMARK_PTR doit ensuite pointer vers un signet 32 bits. Si les signets utilisés sont plus longs que 32 bits, par exemple lorsque les clés primaires sont utilisées en tant que signets, le curseur doit mapper les valeurs réelles aux valeurs 32 bits. Il peut, par exemple, créer une table de hachage. Lorsqu’une application ODBC *3. x* qui utilise un pilote ODBC *2. x* lie un signet, la longueur de la mémoire tampon doit être 4.

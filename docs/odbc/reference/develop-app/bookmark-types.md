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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8f5c5a126ea220f055349ad00dc950281606ed4c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199244"
---
# <a name="bookmark-types"></a>Types de signets
Tous les signets dans ODBC 3 *.x* sont des signets de longueur variable. Cela permet une clé primaire ou un index unique associé à une table pour être utilisée comme signet. Le signet peut également être une valeur 32 bits, que celui utilisé dans ODBC 2. *x*. Pour spécifier qu’un signet est utilisé avec un curseur, une ODBC 3 *.x* application définit l’attribut d’instruction SQL_ATTR_USE_BOOKMARK à SQL_UB_VARIABLE. Un signet de longueur variable est automatiquement utilisé.  
  
 Une application peut appeler **SQLColAttribute** avec la *FieldIdentifier* argument valeur SQL_DESC_OCTET_LENGTH pour obtenir la longueur du signet. Un signet de longueur variable pouvant être une valeur de type long, une application doit lier la colonne 0, sauf si elle utilisera le signet pour la plupart des lignes dans l’ensemble de lignes.  
  
 Signets de longueur fixe sont pris en charge uniquement pour la compatibilité descendante. If un ODBC 2. *x* application fonctionne avec un ODBC 3 *.x* pilote appelle **SQLSetStmtOption** pour définir SQL_USE_BOOKMARKS SQL_UB_ON, elle est mappée dans le Gestionnaire de pilotes à SQL_UB_VARIABLE . Un signet de longueur variable est utilisé, même si seulement 32 bits de celui-ci sont remplies. Si un pilote prend en charge les signets de longueur fixe, il prendra en charge les signets de longueur variable. Si un ODBC 3 *.x* application fonctionne avec une API ODBC 2. *x* pilote appelle **SQLSetStmtAttr** pour définir SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE, elle est mappée dans le Gestionnaire de pilotes à SQL_UB_ON et un signet de longueur fixe de 32 bits est utilisé. L’attribut d’instruction SQL_ATTR_FETCH_BOOKMARK_PTR doit ensuite pointer vers un signet de 32 bits. Si les signets utilisés sont plus de 32 bits, par exemple lorsque les clés primaires sont utilisées en tant que signets, le curseur doit mapper les valeurs réelles aux valeurs de 32 bits. Il peut, par exemple, créer une table de hachage d'entre eux. Quand un ODBC 3 *.x* application fonctionne avec une API ODBC 2. *x* pilote lie un signet, la longueur de la mémoire tampon doit être de 4.

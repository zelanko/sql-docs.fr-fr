---
title: Types de signets (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306330"
---
# <a name="bookmark-types"></a>Types de signets
Tous les signets dans ODBC *3.x* sont des signets à longueur variable. Cela permet d’utiliser une clé principale ou un index unique associé à une table comme signet. Le signet peut également être une valeur 32 bits, comme cela a été utilisé dans ODBC *2.x*. Pour spécifier qu’un signet est utilisé avec un curseur, une application ODBC *3.x* définit l’attribut de relevé SQL_ATTR_USE_BOOKMARK à SQL_UB_VARIABLE. Un signet à longueur variable est automatiquement utilisé.  
  
 Une application peut appeler **SQLColAttribute** avec *l’argument FieldIdentifier* mis à SQL_DESC_OCTET_LENGTH pour obtenir la longueur du signet. Étant donné qu’un signet à longueur variable peut être une valeur longue, une application ne doit pas se lier à la colonne 0 à moins qu’elle n’utilise le signet pour la plupart des lignes dans le ramset.  
  
 Les signets à longueur fixe ne sont pris en charge que pour la compatibilité vers l’arrière. Si une application ODBC *2.x* travaillant avec un conducteur ODBC *3.x* appelle **SQLSetStmtOption** pour régler SQL_USE_BOOKMARKS à SQL_UB_ON, il est cartographié dans le gestionnaire de conducteur pour SQL_UB_VARIABLE. Un signet à longueur variable est utilisé, même si seulement 32 bits de celui-ci sont peuplés. Si un conducteur prend en charge les signets à longueur fixe, il prendra en charge les signets à longueur variable. Si une application ODBC *3.x* travaillant avec un conducteur ODBC *2.x* appelle **SQLSetStmtAttr** pour régler SQL_ATTR_USE_BOOKMARKS à SQL_UB_VARIABLE, il est cartographié dans le Gestionnaire de conducteur pour SQL_UB_ON et un signet fixe de 32 bits est utilisé. L’attribut de l’SQL_ATTR_FETCH_BOOKMARK_PTR déclaration doit alors indiquer un signet 32 bits. Si les signets utilisés sont plus longs que 32 bits, comme lorsque les touches primaires sont utilisées comme signets, le curseur doit cartographier les valeurs réelles en valeurs 32 bits. Il pourrait, par exemple, construire une table de hachage d’entre eux. Lorsqu’une application ODBC *3.x* travaillant avec un pilote ODBC *2.x* lie un signet, la longueur du tampon doit être de 4.

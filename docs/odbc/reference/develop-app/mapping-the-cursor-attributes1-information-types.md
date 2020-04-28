---
title: Mappage des types d’informations du curseur Attributes1 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], mapping cursor attributes1 information types
- application upgrades [ODBC], mapping cursor attributes1 information types
- mapping cursor attributes1 information types [ODBC]
- backward compatibility [ODBC], mapping cursor attributes1 information types
- upgrading applications [ODBC], mapping cursor attributes1 information types
ms.assetid: 9f112449-ca86-45ac-a865-e6174d67f91b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d70cf0a93a6c6160faeb0afe991b2adfff11b8f1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301042"
---
# <a name="mapping-the-cursor-attributes1-information-types"></a>Mappage des types d’informations Attributes1 du curseur
Quand ODBC 3. *x* l’application appelle **SQLGetInfo** dans un pilote ODBC 2 *. x* avec le type d’informations SQL_XXXX_CURSOR_ATTRIBUTES1 (pour les curseurs dynamiques, avant uniquement, avec pilote de jeu de clés ou statiques), le paramètre des bits retournés par le gestionnaire de pilotes dépend de ce que fait ODBC 2. *x* retourne le pilote ODBC 2 correspondant. *x* types d’informations. Les bits sont définis comme indiqué dans le tableau suivant.  
  
|Bit dans<br /><br /> SQL_XXXX_CURSOR_ATTRIBUTES1|Type de curseur|ODBC 2. informations sur *x*<br /><br /> type|  
|-----------------------------------------------|-----------------|-------------------------------------|  
|SQL_CA1_NEXT|Tous|SQL_FETCH_DIRECTION|  
|SQL_CA1_ABSOLUTE SQL_CA1_RELATIVE SQL_CA1_BOOKMARK|Dynamic, keyset-Driver, static|SQL_FETCH_DIRECTION|  
|SQL_CA1_LOCK_NO_CHANGE SQL_CA1_LOCK_UNLOCK SQL_CA1_LOCK_EXCLUSIVE|Dynamic, keyset-Driver, static|SQL_LOCK_TYPES|  
|SQL_CA1_POSITIONED_UPDATE SQL_CA1_POSITIONED_DELETE SQL_CA1_SELECT_FOR_UPDATE|Tous|SQL_POSITIONED_STATEMENTS|  
|SQL_CA1_POS_POSITION SQL_CA1_POS_DELETE SQL_CA1_POS_REFRESH SQL_CA1_POS_BULK_ADD|Dynamic, keyset-Driver, static|SQL_POS_OPERATIONS|

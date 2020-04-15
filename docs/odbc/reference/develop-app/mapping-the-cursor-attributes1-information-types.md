---
title: Cartographier les types d’information Attributs1 du curseur1 Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301042"
---
# <a name="mapping-the-cursor-attributes1-information-types"></a>Mappage des types d’informations Attributes1 du curseur
Quand un ODBC 3. *x* application appelle **SQLGetInfo** dans un pilote ODBC 2 *.x* avec le type d’information SQL_XXXX_CURSOR_ATTRIBUTES1 (pour dynamique, avant-seulement, keyset-driver, ou curseurs statiques), le réglage des bits retournés par Driver Manager dépend de ce que l’ODBC 2. *x* le pilote revient pour l’ODBC 2 correspondant. *x* types d’informations. Les bits sont réglés comme indiqué dans le tableau suivant.  
  
|Bit dans<br /><br /> SQL_XXXX_CURSOR_ATTRIBUTES1|Type de curseur|ODBC 2. *x* informations<br /><br /> type|  
|-----------------------------------------------|-----------------|-------------------------------------|  
|SQL_CA1_NEXT|Tous|SQL_FETCH_DIRECTION|  
|SQL_CA1_ABSOLUTE SQL_CA1_RELATIVE SQL_CA1_BOOKMARK|Dynamique, keyset-driver, statique|SQL_FETCH_DIRECTION|  
|SQL_CA1_LOCK_NO_CHANGE SQL_CA1_LOCK_UNLOCK SQL_CA1_LOCK_EXCLUSIVE|Dynamique, keyset-driver, statique|SQL_LOCK_TYPES|  
|SQL_CA1_POSITIONED_UPDATE SQL_CA1_POSITIONED_DELETE SQL_CA1_SELECT_FOR_UPDATE|Tous|SQL_POSITIONED_STATEMENTS|  
|SQL_CA1_POS_POSITION SQL_CA1_POS_DELETE SQL_CA1_POS_REFRESH SQL_CA1_POS_BULK_ADD|Dynamique, keyset-driver, statique|SQL_POS_OPERATIONS|

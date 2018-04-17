---
title: Mapper les Types d’informations de Attributes1 curseur | Documents Microsoft
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
ms.topic: article
helpviewer_keywords:
- compatibility [ODBC], mapping cursor attributes1 information types
- application upgrades [ODBC], mapping cursor attributes1 information types
- mapping cursor attributes1 information types [ODBC]
- backward compatibility [ODBC], mapping cursor attributes1 information types
- upgrading applications [ODBC], mapping cursor attributes1 information types
ms.assetid: 9f112449-ca86-45ac-a865-e6174d67f91b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2d40ff95acc4011e7cc3dc12785ea6cef7340e35
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="mapping-the-cursor-attributes1-information-types"></a>Mapper les Types d’informations de Attributes1 curseur
Lorsqu’une application ODBC 3. *x* application appelle **SQLGetInfo** dans une API ODBC 2*.x* pilote avec les informations de type (pour pilotés dynamique et en avant uniquement, ou les curseurs statiques), le paramètre des bits retournés par le Gestionnaire de pilotes de SQL_XXXX_CURSOR_ATTRIBUTES1 dépend de quelles ODBC 2. *x* pilote retourne pour correspondant ODBC 2. *x* types d’informations. Les bits sont définis comme indiqué dans le tableau suivant.  
  
|Bit dans<br /><br /> SQL_XXXX_CURSOR_ATTRIBUTES1|Type de curseur|ODBC 2. *x* informations<br /><br /> Type|  
|-----------------------------------------------|-----------------|-------------------------------------|  
|SQL_CA1_NEXT|Tous|SQL_FETCH_DIRECTION|  
|SQL_CA1_ABSOLUTE SQL_CA1_RELATIVE SQL_CA1_BOOKMARK|Dynamiques, pilotés, statiques|SQL_FETCH_DIRECTION|  
|SQL_CA1_LOCK_NO_CHANGE SQL_CA1_LOCK_UNLOCK SQL_CA1_LOCK_EXCLUSIVE|Dynamiques, pilotés, statiques|SQL_LOCK_TYPES|  
|SQL_CA1_POSITIONED_UPDATE SQL_CA1_POSITIONED_DELETE SQL_CA1_SELECT_FOR_UPDATE|Tous|SQL_POSITIONED_STATEMENTS|  
|SQL_CA1_POS_POSITION SQL_CA1_POS_DELETE SQL_CA1_POS_REFRESH SQL_CA1_POS_BULK_ADD|Dynamiques, pilotés, statiques|SQL_POS_OPERATIONS|

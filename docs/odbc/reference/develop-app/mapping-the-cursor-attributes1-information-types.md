---
title: Mappage des Types d’informations Attributes1 curseur | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9e9549c442e301f3a6ed8d3da9c73d52177adf01
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62628901"
---
# <a name="mapping-the-cursor-attributes1-information-types"></a>Mappage des types d’informations Attributes1 du curseur
Lorsqu’une application ODBC 3. *x* application appelle **SQLGetInfo** dans un ODBC 2 *.x* pilote avec le type d’information SQL_XXXX_CURSOR_ATTRIBUTES1 (pour dynamique, avant uniquement, les curseurs pilotés, ou les curseurs statiques), le paramètre des bits retournés par le Gestionnaire de pilotes dépend de ce que les 2 d’ODBC. *x* pilote retourne pour le correspondantes ODBC 2. *x* types d’informations. Les bits sont définis comme indiqué dans le tableau suivant.  
  
|Bit dans<br /><br /> SQL_XXXX_CURSOR_ATTRIBUTES1|Type de curseur|ODBC 2. *x* informations<br /><br /> type|  
|-----------------------------------------------|-----------------|-------------------------------------|  
|SQL_CA1_NEXT|All|SQL_FETCH_DIRECTION|  
|SQL_CA1_ABSOLUTE SQL_CA1_RELATIVE SQL_CA1_BOOKMARK|Dynamiques, curseurs pilotés, statiques|SQL_FETCH_DIRECTION|  
|SQL_CA1_LOCK_NO_CHANGE SQL_CA1_LOCK_UNLOCK SQL_CA1_LOCK_EXCLUSIVE|Dynamiques, curseurs pilotés, statiques|SQL_LOCK_TYPES|  
|SQL_CA1_POSITIONED_UPDATE SQL_CA1_POSITIONED_DELETE SQL_CA1_SELECT_FOR_UPDATE|All|SQL_POSITIONED_STATEMENTS|  
|SQL_CA1_POS_POSITION SQL_CA1_POS_DELETE SQL_CA1_POS_REFRESH SQL_CA1_POS_BULK_ADD|Dynamiques, curseurs pilotés, statiques|SQL_POS_OPERATIONS|

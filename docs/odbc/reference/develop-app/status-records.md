---
title: Enregistrements d’état | Documents Microsoft
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
- diagnostic information [ODBC], diagnostic records
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 4a987f69-158f-4cc4-a31b-2b7dd8dcbb87
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e748612bf8293a0c7fca29b0baa21c9278e44d15
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="status-records"></a>Enregistrements d’état
Les champs dans les enregistrements d’état contiennent des informations sur les erreurs spécifiques ou des avertissements retournés par la source du Gestionnaire de pilotes, pilotes ou des données, y compris le SQLSTATE numéro d’erreur natif, message de diagnostic, numéro de colonne et numéro de ligne. Enregistrements d’état peuvent être créés uniquement si la fonction retourne SQL_ERROR, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_NEED_DATA ou SQL_STILL_EXECUTING. Pour obtenir une liste complète des champs dans les enregistrements d’état, consultez le [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) description de fonction.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Séquence d’enregistrements d’état](../../../odbc/reference/develop-app/sequence-of-status-records.md)  
  
-   [Codes SQLSTATE](../../../odbc/reference/develop-app/sqlstates.md)  
  
-   [Messages de diagnostic](../../../odbc/reference/develop-app/diagnostic-messages.md)

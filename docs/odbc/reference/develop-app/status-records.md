---
title: "Enregistrements d’état | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 4a987f69-158f-4cc4-a31b-2b7dd8dcbb87
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ab82d285a57c147a27cb248e1e28b1bd9c6d0241
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="status-records"></a>Enregistrements d’état
Les champs dans les enregistrements d’état contiennent des informations sur les erreurs spécifiques ou des avertissements retournés par la source du Gestionnaire de pilotes, pilotes ou des données, y compris le SQLSTATE numéro d’erreur natif, message de diagnostic, numéro de colonne et numéro de ligne. Enregistrements d’état peuvent être créés uniquement si la fonction retourne SQL_ERROR, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_NEED_DATA ou SQL_STILL_EXECUTING. Pour obtenir une liste complète des champs dans les enregistrements d’état, consultez le [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) description de fonction.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Séquence d’enregistrements d’état](../../../odbc/reference/develop-app/sequence-of-status-records.md)  
  
-   [SQLSTATE](../../../odbc/reference/develop-app/sqlstates.md)  
  
-   [Messages de diagnostic](../../../odbc/reference/develop-app/diagnostic-messages.md)


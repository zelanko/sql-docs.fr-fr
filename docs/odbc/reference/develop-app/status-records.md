---
title: Dossiers d’état Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 4a987f69-158f-4cc4-a31b-2b7dd8dcbb87
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4afef16137404fcdfd3e1d328642f1d314829538
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301370"
---
# <a name="status-records"></a>Enregistrements d’état
Les champs dans les registres d’état contiennent des renseignements sur des erreurs ou des avertissements spécifiques retournés par le gestionnaire de conducteur, le conducteur ou la source de données, y compris le SQLSTATE, le numéro d’erreur natif, le message diagnostique, le numéro de colonne et le numéro de rangée. Les enregistrements d’état ne peuvent être créés que si la fonction renvoie SQL_ERROR, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_NEED_DATA ou SQL_STILL_EXECUTING. Pour une liste complète des champs dans les registres d’état, consultez la description de la fonction [SQLGetDiagField.](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
 Cette section contient les rubriques suivantes :  
  
-   [Séquence d’enregistrements d’état](../../../odbc/reference/develop-app/sequence-of-status-records.md)  
  
-   [Codes SQLSTATE](../../../odbc/reference/develop-app/sqlstates.md)  
  
-   [Messages de diagnostic](../../../odbc/reference/develop-app/diagnostic-messages.md)

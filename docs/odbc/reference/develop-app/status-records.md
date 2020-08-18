---
description: Enregistrements d’état
title: Enregistrements d’État | Microsoft Docs
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
ms.openlocfilehash: 96d871814ac22e52eece4d6db7fff68fa2dacd48
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482901"
---
# <a name="status-records"></a>Enregistrements d’état
Les champs des enregistrements d’État contiennent des informations sur des erreurs ou des avertissements spécifiques retournés par le gestionnaire de pilotes, le pilote ou la source de données, y compris le SQLSTATE, le numéro d’erreur natif, le message de diagnostic, le numéro de colonne et le numéro de ligne. Les enregistrements d’État ne peuvent être créés que si la fonction retourne SQL_ERROR, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_NEED_DATA ou SQL_STILL_EXECUTING. Pour obtenir la liste complète des champs dans les enregistrements d’État, consultez la description de la fonction [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) .  
  
 Cette section contient les rubriques suivantes :  
  
-   [Séquence d’enregistrements d’état](../../../odbc/reference/develop-app/sequence-of-status-records.md)  
  
-   [Codes SQLSTATE](../../../odbc/reference/develop-app/sqlstates.md)  
  
-   [Messages de diagnostic](../../../odbc/reference/develop-app/diagnostic-messages.md)

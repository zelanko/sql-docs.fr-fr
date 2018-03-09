---
title: "Déterminer le nombre de lignes affectées | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- updating data [ODBC], number of rows affected
- number of rows affected by update [ODBC]
- data updates [ODBC], number of rows affected
ms.assetid: 1e56297d-a786-415e-b66d-b42d1b2a8d45
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ac4b30fc9bbbb2e289ca53094d5050f0808b3ec1
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="determining-the-number-of-affected-rows"></a>Déterminer le nombre de lignes affectées
Une fois une application met à jour, supprime ou insère des lignes, elle peut appeler **SQLRowCount** pour déterminer le nombre de lignes affecté. **SQLRowCount** renvoie cette valeur si les lignes ont été mis à jour, supprimées ou insérées en exécutant un **mettre à jour**, **supprimer**, ou **insérer** instruction, en exécutant une mise à jour positionnée ou une instruction delete, ou en appelant **SQLSetPos**.  
  
 Si un lot d’instructions SQL est exécuté, le nombre de lignes affectées peut être un nombre total de toutes les instructions dans le lot ou des nombres individuels pour chaque instruction du lot. Pour plus d’informations, consultez [Batches of SQL Statements](../../../odbc/reference/develop-app/batches-of-sql-statements.md) et [plusieurs résultats](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Le nombre de lignes affectées est également retourné dans le champ d’en-tête diagnostic SQL_DIAG_ROW_COUNT dans la zone de diagnostic associé au handle d’instruction. Cependant, les données de ce champ sont réinitialisées après chaque fonction est appelé sur le même descripteur d’instruction, tandis que la valeur retournée par **SQLRowCount** reste le même qu’un appel à **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPrepare**, ou **SQLSetPos**.

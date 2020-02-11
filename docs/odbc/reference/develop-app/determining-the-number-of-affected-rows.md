---
title: Détermination du nombre de lignes affectées | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], number of rows affected
- number of rows affected by update [ODBC]
- data updates [ODBC], number of rows affected
ms.assetid: 1e56297d-a786-415e-b66d-b42d1b2a8d45
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a6a1bebf7d5cfb85e49fb0e382dacc4f4464054e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68039983"
---
# <a name="determining-the-number-of-affected-rows"></a>Détermination du nombre de lignes affectées
Lorsqu’une application met à jour, supprime ou insère des lignes, elle peut appeler **SQLRowCount** pour déterminer le nombre de lignes affectées. **SQLRowCount** retourne cette valeur que les lignes aient été mises à jour, supprimées ou insérées en exécutant une instruction **Update**, **Delete**ou **Insert** , en exécutant une instruction UPDATE ou DELETE positionnée, ou en appelant **SQLSetPos**.  
  
 Si un lot d’instructions SQL est exécuté, le nombre de lignes affectées peut être un nombre total de toutes les instructions du lot ou des comptes individuels pour chaque instruction du lot. Pour plus d’informations, consultez [lots d’instructions SQL](../../../odbc/reference/develop-app/batches-of-sql-statements.md) et [résultats multiples](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Le nombre de lignes affectées est également retourné dans le champ d’en-tête de diagnostic SQL_DIAG_ROW_COUNT dans la zone de diagnostic associée au descripteur d’instruction. Toutefois, les données de ce champ sont réinitialisées après chaque appel de fonction sur le même descripteur d’instruction, alors que la valeur retournée par **SQLRowCount** reste la même jusqu’à un appel à **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPrepare**ou **SQLSetPos**.

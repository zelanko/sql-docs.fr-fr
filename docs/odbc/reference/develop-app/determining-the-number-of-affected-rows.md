---
title: Déterminer le nombre de rangées touchées (en anglais seulement) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 156a5fe41d2c9b57a33bbc2bdb4540d1f5b00340
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305890"
---
# <a name="determining-the-number-of-affected-rows"></a>Détermination du nombre de lignes affectées
Après une application met à jour, supprime ou insère des lignes, elle peut appeler **SQLRowCount** pour déterminer combien de lignes ont été touchées. **SQLRowCount** retourne cette valeur, que les lignes aient été mises à jour, supprimées ou insérées en exécutant une **mise À JOUR**, **SUPPRIMER**, ou **insert** statement, en exécutant une mise à jour ou une déclaration de suppression positionnée, ou en appelant **SQLSetPos**.  
  
 Si un lot de relevés SQL est exécuté, le nombre de lignes touchées peut être un décompte total pour toutes les déclarations dans le lot ou les dénombrements individuels pour chaque relevé dans le lot. Pour plus d’informations, voir [Lots of SQL Statements](../../../odbc/reference/develop-app/batches-of-sql-statements.md) and Multiple [Results](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Le nombre de lignes touchées est également retourné dans le champ d’en-tête diagnostique SQL_DIAG_ROW_COUNT dans le domaine diagnostique associé à la poignée de déclaration. Cependant, les données dans ce domaine sont réinitialisées après chaque appel de fonction sur la même poignée de déclaration, tandis que la valeur retournée par **SQLRowCount** reste la même jusqu’à ce qu’un appel à **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPrepare**, ou **SQLSetPos**.

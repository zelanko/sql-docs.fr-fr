---
title: Erreurs et lots | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- batches [ODBC], errors
- sql_success_with_info [ODBC]
- sql_success [ODBC]
- SQL statements [ODBC], batches
- sql_error [ODBC]
ms.assetid: 6debd41d-9f4c-4f4c-a44b-2993da5306f0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 97179574407dca56026f9d5216e4978069cffc1e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62942982"
---
# <a name="errors-and-batches"></a>Erreurs et lots
Lorsqu’une erreur se produit lors de l’exécution d’un lot d’instructions SQL, un des quatre résultats suivants sont possibles. (Chaque résultat possible est spécifique à la source de données et peut même dépend les instructions incluses dans le lot.)  
  
-   Aucune instruction du lot est exécutée.  
  
-   Aucune instruction du lot est exécutée et la transaction est restaurée.  
  
-   Toutes les instructions avant l’instruction d’erreur sont exécutées.  
  
-   Toutes les instructions à l’exception de l’instruction d’erreur sont exécutées.  
  
 Dans les deux premiers cas, **SQLExecute** et **SQLExecDirect** retourne SQL_ERROR. Dans les deux derniers cas, ils peuvent retourner SQL_SUCCESS_WITH_INFO ou SQL_SUCCESS, selon l’implémentation. Dans tous les cas, plus des informations d’erreur peuvent être récupérées avec **SQLGetDiagField**, **SQLGetDiagRec**, ou **SQLError**. Toutefois, la nature et la profondeur de ces informations est spécifique à la source de données. En outre, ces informations sont peu de chances d’identifier exactement l’instruction dans l’erreur.

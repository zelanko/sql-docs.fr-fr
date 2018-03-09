---
title: Erreurs et des traitements | Documents Microsoft
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
- batches [ODBC], errors
- sql_success_with_info [ODBC]
- sql_success [ODBC]
- SQL statements [ODBC], batches
- sql_error [ODBC]
ms.assetid: 6debd41d-9f4c-4f4c-a44b-2993da5306f0
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6bdb04f60a6f7a981fd5869f7c74c4741df05f3a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="errors-and-batches"></a>Erreurs et des traitements
Lorsqu’une erreur se produit lors de l’exécution d’un lot d’instructions SQL, un des quatre résultats suivants sont possibles. (Chaque résultat possible est spécifique à la source de données et peut même dépend les instructions incluses dans le lot.)  
  
-   Aucune instruction du lot n’est exécutées.  
  
-   Aucune instruction du lot n’est exécutées et la transaction est restaurée.  
  
-   Toutes les instructions avant l’instruction d’erreur sont exécutées.  
  
-   Toutes les instructions à l’exception de l’instruction d’erreur sont exécutées.  
  
 Dans les deux premiers cas, **SQLExecute** et **SQLExecDirect** retourne SQL_ERROR. Dans les deux derniers cas, elles peuvent retourner SQL_SUCCESS_WITH_INFO ou SQL_SUCCESS, selon l’implémentation. Dans tous les cas, obtenir des informations d’erreur pouvant être récupérées avec **SQLGetDiagField**, **SQLGetDiagRec**, ou **SQLError**. Toutefois, la nature et la profondeur de ces informations est spécifique à la source de données. En outre, cette information est peu probable qu’exactement l’instruction dans l’erreur.

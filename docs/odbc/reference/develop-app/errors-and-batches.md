---
title: Erreurs et des traitements | Documents Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- batches [ODBC], errors
- sql_success_with_info [ODBC]
- sql_success [ODBC]
- SQL statements [ODBC], batches
- sql_error [ODBC]
ms.assetid: 6debd41d-9f4c-4f4c-a44b-2993da5306f0
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9f9ad11a7f9f0f89e2aa1320b221ce43ac04573e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="errors-and-batches"></a>Erreurs et des traitements
Lorsqu’une erreur se produit lors de l’exécution d’un lot d’instructions SQL, un des quatre résultats suivants sont possibles. (Chaque résultat possible est spécifique à la source de données et peut même dépend les instructions incluses dans le lot.)  
  
-   Aucune instruction du lot n’est exécutées.  
  
-   Aucune instruction du lot n’est exécutées et la transaction est restaurée.  
  
-   Toutes les instructions avant l’instruction d’erreur sont exécutées.  
  
-   Toutes les instructions à l’exception de l’instruction d’erreur sont exécutées.  
  
 Dans les deux premiers cas, **SQLExecute** et **SQLExecDirect** retourne SQL_ERROR. Dans les deux derniers cas, elles peuvent retourner SQL_SUCCESS_WITH_INFO ou SQL_SUCCESS, selon l’implémentation. Dans tous les cas, obtenir des informations d’erreur pouvant être récupérées avec **SQLGetDiagField**, **SQLGetDiagRec**, ou **SQLError**. Toutefois, la nature et la profondeur de ces informations est spécifique à la source de données. En outre, cette information est peu probable qu’exactement l’instruction dans l’erreur.

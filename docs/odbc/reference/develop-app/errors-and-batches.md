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
ms.openlocfilehash: 61effe29811cc7a8f6e23cbea127b2f757cc7b0c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47645937"
---
# <a name="errors-and-batches"></a>Erreurs et lots
Lorsqu’une erreur se produit lors de l’exécution d’un lot d’instructions SQL, un des quatre résultats suivants sont possibles. (Chaque résultat possible est spécifique à la source de données et peut même dépend les instructions incluses dans le lot.)  
  
-   Aucune instruction du lot est exécutée.  
  
-   Aucune instruction du lot est exécutée et la transaction est restaurée.  
  
-   Toutes les instructions avant l’instruction d’erreur sont exécutées.  
  
-   Toutes les instructions à l’exception de l’instruction d’erreur sont exécutées.  
  
 Dans les deux premiers cas, **SQLExecute** et **SQLExecDirect** retourne SQL_ERROR. Dans les deux derniers cas, ils peuvent retourner SQL_SUCCESS_WITH_INFO ou SQL_SUCCESS, selon l’implémentation. Dans tous les cas, plus des informations d’erreur peuvent être récupérées avec **SQLGetDiagField**, **SQLGetDiagRec**, ou **SQLError**. Toutefois, la nature et la profondeur de ces informations est spécifique à la source de données. En outre, ces informations sont peu de chances d’identifier exactement l’instruction dans l’erreur.

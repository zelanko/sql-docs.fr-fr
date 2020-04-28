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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 36a402686a695a08748df24a7b40a228d7a2ca7f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300429"
---
# <a name="errors-and-batches"></a>Erreurs et lots
Lorsqu’une erreur se produit lors de l’exécution d’un lot d’instructions SQL, l’un des quatre résultats suivants est possible. (Chaque résultat possible est spécifique à la source de données et peut même dépendre des instructions incluses dans le lot).  
  
-   Aucune instruction du traitement n’est exécutée.  
  
-   Aucune instruction du traitement n’est exécutée et la transaction est restaurée.  
  
-   Toutes les instructions avant l’instruction Error sont exécutées.  
  
-   Toutes les instructions, à l’exception de l’instruction Error, sont exécutées.  
  
 Dans les deux premiers cas, **SQLExecute** et **SQLExecDirect** retournent SQL_ERROR. Dans les deux derniers cas, ils peuvent retourner des SQL_SUCCESS_WITH_INFO ou des SQL_SUCCESS, en fonction de l’implémentation. Dans tous les cas, des informations supplémentaires sur l’erreur peuvent être récupérées avec **SQLGetDiagField**, **SQLGetDiagRec**ou **SQLError**. Toutefois, la nature et la profondeur de ces informations sont spécifiques à la source de données. En outre, il est peu probable que ces informations identifient exactement l’instruction erronée.

---
description: Erreurs et lots
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
ms.openlocfilehash: 1e5cdf4d394ffa1c17173aedc4485b6979cf371e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461491"
---
# <a name="errors-and-batches"></a>Erreurs et lots
Lorsqu’une erreur se produit lors de l’exécution d’un lot d’instructions SQL, l’un des quatre résultats suivants est possible. (Chaque résultat possible est spécifique à la source de données et peut même dépendre des instructions incluses dans le lot).  
  
-   Aucune instruction du traitement n’est exécutée.  
  
-   Aucune instruction du traitement n’est exécutée et la transaction est restaurée.  
  
-   Toutes les instructions avant l’instruction Error sont exécutées.  
  
-   Toutes les instructions, à l’exception de l’instruction Error, sont exécutées.  
  
 Dans les deux premiers cas, **SQLExecute** et **SQLExecDirect** retournent SQL_ERROR. Dans les deux derniers cas, ils peuvent retourner des SQL_SUCCESS_WITH_INFO ou des SQL_SUCCESS, en fonction de l’implémentation. Dans tous les cas, des informations supplémentaires sur l’erreur peuvent être récupérées avec **SQLGetDiagField**, **SQLGetDiagRec**ou **SQLError**. Toutefois, la nature et la profondeur de ces informations sont spécifiques à la source de données. En outre, il est peu probable que ces informations identifient exactement l’instruction erronée.

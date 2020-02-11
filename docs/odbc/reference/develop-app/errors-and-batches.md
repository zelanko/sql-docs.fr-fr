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
ms.openlocfilehash: 6902b82c74e953d6009d7e5352608477d92122d6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68051132"
---
# <a name="errors-and-batches"></a>Erreurs et lots
Lorsqu’une erreur se produit lors de l’exécution d’un lot d’instructions SQL, l’un des quatre résultats suivants est possible. (Chaque résultat possible est spécifique à la source de données et peut même dépendre des instructions incluses dans le lot).  
  
-   Aucune instruction du traitement n’est exécutée.  
  
-   Aucune instruction du traitement n’est exécutée et la transaction est restaurée.  
  
-   Toutes les instructions avant l’instruction Error sont exécutées.  
  
-   Toutes les instructions, à l’exception de l’instruction Error, sont exécutées.  
  
 Dans les deux premiers cas, **SQLExecute** et **SQLExecDirect** retournent SQL_ERROR. Dans les deux derniers cas, ils peuvent retourner des SQL_SUCCESS_WITH_INFO ou des SQL_SUCCESS, en fonction de l’implémentation. Dans tous les cas, des informations supplémentaires sur l’erreur peuvent être récupérées avec **SQLGetDiagField**, **SQLGetDiagRec**ou **SQLError**. Toutefois, la nature et la profondeur de ces informations sont spécifiques à la source de données. En outre, il est peu probable que ces informations identifient exactement l’instruction erronée.

---
title: Erreurs et lots Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300429"
---
# <a name="errors-and-batches"></a>Erreurs et lots
Lorsqu’une erreur se produit lors de l’exécution d’un lot de relevés SQL, l’un des quatre résultats suivants est possible. (Chaque résultat possible est spécifique à la source de données et peut même dépendre des énoncés inclus dans le lot.)  
  
-   Aucune déclaration dans le lot n’est exécutée.  
  
-   Aucune déclaration dans le lot n’est exécutée et la transaction est annulée.  
  
-   Toutes les déclarations avant l’exécution de la déclaration d’erreur.  
  
-   Toutes les déclarations, sauf la déclaration d’erreur, sont exécutées.  
  
 Dans les deux premiers cas, **SQLExecute** et **SQLExecDirect** retournent SQL_ERROR. Dans les deux derniers cas, ils peuvent retourner SQL_SUCCESS_WITH_INFO ou SQL_SUCCESS, selon la mise en œuvre. Dans tous les cas, d’autres informations d’erreur peuvent être récupérées avec **SQLGetDiagField**, **SQLGetDiagRec**, ou **SQLError**. Cependant, la nature et la profondeur de ces informations sont spécifiques aux données. En outre, il est peu probable que ces informations identifient exactement l’instruction par erreur.

---
title: Exécution des lots (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- batches [ODBC], executing
- SQL statements [ODBC], batches
ms.assetid: f082c717-4f82-4820-a2fa-ba607d8fd872
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0ce0c043fcfad41a624ad129a757a047d2c87fb6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305730"
---
# <a name="executing-batches"></a>Exécution de lots
Avant qu’une application exécute un lot d’instructions, elle doit d’abord vérifier si elles sont prises en charge. Pour ce faire, l’application appelle **SQLGetInfo** avec les options SQL_BATCH_SUPPORT, SQL_PARAM_ARRAY_ROW_COUNTS et SQL_PARAM_ARRAY_SELECTS. La première option renvoie si les énoncés générateurs de comptage et de résultats sont pris en charge dans des lots et des procédures explicites, tandis que les deux dernières options renvoient des informations sur la disponibilité des nombres de lignes et donnent lieu à des ensembles d’exécutions paramétrées.  
  
 Des lots de déclarations sont exécutés par **SQLExecute** ou **SQLExecDirect**. Par exemple, l’appel suivant exécute un lot explicite d’instructions pour ouvrir un nouvel ordre de vente.  
  
```  
SQLCHAR *BatchStmt =  
   "INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)"  
      "VALUES (2002, 1001, {fn CURDATE()}, 'Garcia', 'OPEN');"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 1, 1234, 10);"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 2, 987, 8);"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 3, 566, 17);"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 4, 412, 500)";  
  
SQLExecDirect(hstmt, BatchStmt, SQL_NTS);  
```  
  
 Lorsqu’un lot d’instructions génératrices de résultats est exécuté, il renvoie un ou plusieurs nombres de lignes ou ensembles de résultats. Pour plus d’informations sur la façon de les récupérer, voir [résultats multiples](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Si un lot d’instructions comprend des marqueurs de paramètres, ceux-ci sont numérotés dans l’ordre de paramètres croissant comme ils le sont dans toute autre déclaration. Par exemple, le lot suivant d’énoncés a des paramètres numérotés de 1 à 21; ceux de la première instruction **INSERT** sont numérotés 1 à 5 et ceux de la dernière instruction **INSERT** sont numérotés 18 à 21.  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
```  
  
 Pour plus d’informations sur les paramètres, voir [Paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md), plus tard dans cette section.

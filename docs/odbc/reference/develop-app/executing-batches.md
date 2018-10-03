---
title: L’exécution de lots | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 46b224e8167587c4e4860f171b132d23539143e8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47695030"
---
# <a name="executing-batches"></a>Exécution de lots
Avant qu’une application exécute un lot d’instructions, elle doit tout d’abord vérifier si elles sont prises en charge. Pour ce faire, l’application appelle **SQLGetInfo** avec les options SQL_BATCH_SUPPORT, SQL_PARAM_ARRAY_ROW_COUNTS et SQL_PARAM_ARRAY_SELECTS. La première option retourne si le nombre de ligne – génération et le résultat : génération de l’ensemble des instructions sont pris en charge dans les lots explicites et de procédures, pendant les deux dernières options de retour d’informations sur la disponibilité des nombres de lignes et résultat définit dans paramétrable exécution.  
  
 Lots d’instructions sont exécutées via **SQLExecute** ou **SQLExecDirect**. Par exemple, l’appel suivant exécute un lot explicit d’instructions pour ouvrir une nouvelle commande.  
  
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
  
 Lorsqu’un lot de génération de résultats instructions est exécutée, elle retourne l’une ou plusieurs nombres de lignes ou résultat définit. Pour plus d’informations sur la façon de les récupérer, consultez [plusieurs résultats](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Si un lot d’instructions inclut des marqueurs de paramètres, ceux-ci sont numérotées en augmentant l’ordre des paramètres comme elles se trouvent dans une autre instruction. Par exemple, le lot suivant d’instructions ayant des paramètres numérotées de 1 à 21. ceux de la première **insérer** instruction sont numérotés 1 à 5 et celles de la dernière **insérer** instruction sont numérotées 18 et 21.  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
```  
  
 Pour plus d’informations sur les paramètres, consultez [paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md), plus loin dans cette section.

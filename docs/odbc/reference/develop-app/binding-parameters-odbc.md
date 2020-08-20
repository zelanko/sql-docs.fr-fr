---
description: Liaison de paramètres dans ODBC
title: Liaison de paramètres ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- binding parameters [ODBC]
ms.assetid: 7538a82b-b08b-4c8f-9809-e4ccea16db11
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9893d6611ad2bfc7107df1cd2d4ffe72dbf32fad
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499952"
---
# <a name="binding-parameters-odbc"></a>Liaison de paramètres dans ODBC
Chaque paramètre dans une instruction SQL doit être associé, ou *lié,* à une variable dans l’application avant l’exécution de l’instruction. Lorsque l’application lie une variable à un paramètre, elle décrit cette variable-Address, le type de données C, et ainsi de suite, le pilote. Elle décrit également le paramètre, le type de données SQL, la précision, etc. Le pilote stocke ces informations dans la structure qu’il gère pour cette instruction et utilise ces informations pour récupérer la valeur de la variable lors de l’exécution de l’instruction.  
  
 Les paramètres peuvent être liés ou reliés à tout moment avant l’exécution d’une instruction. Si un paramètre est relié après l’exécution d’une instruction, la liaison ne s’applique pas tant que l’instruction n’est pas exécutée de nouveau. Pour lier un paramètre à une variable différente, une application relie simplement le paramètre à la nouvelle variable ; la liaison précédente est automatiquement libérée.  
  
 Une variable reste liée à un paramètre jusqu’à ce qu’une variable différente soit liée au paramètre, jusqu’à ce que tous les paramètres soient indépendants en appelant **SQLFreeStmt** avec l’option SQL_RESET_PARAMS ou jusqu’à ce que l’instruction soit libérée. Pour cette raison, l’application doit s’assurer que les variables ne sont pas libérées tant qu’elles ne sont pas détachées. Pour plus d’informations, consultez [allocation et libération de mémoires tampons](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md).  
  
 Étant donné que les liaisons de paramètres sont simplement des informations stockées dans la structure gérée par le pilote de l’instruction, elles peuvent être définies dans n’importe quel ordre. Elles sont également indépendantes de l’instruction SQL exécutée. Par exemple, supposons qu’une application lie trois paramètres, puis exécute l’instruction SQL suivante :  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Si l’application exécute ensuite immédiatement l’instruction SQL  
  
```  
SELECT * FROM Orders WHERE OrderID = ?, OpenDate = ?, Status = ?  
```  
  
 sur le même descripteur d’instruction, les liaisons de paramètre pour l’instruction **Insert** sont utilisées, car il s’agit des liaisons stockées dans la structure de l’instruction. Dans la plupart des cas, il s’agit d’une pratique de programmation médiocre qui devrait être évitée. Au lieu de cela, l’application doit appeler **SQLFreeStmt** avec l’option SQL_RESET_PARAMS pour dissocier tous les anciens paramètres, puis en lier de nouveaux.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Liaison de marqueurs de paramètre](../../../odbc/reference/develop-app/binding-parameter-markers.md)  
  
-   [Liaison de paramètres par nom (paramètres nommés)](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md)  
  
-   [Décalages des liaisons de paramètres](../../../odbc/reference/develop-app/parameter-binding-offsets.md)  
  
-   [Description des paramètres](../../../odbc/reference/develop-app/describing-parameters.md)

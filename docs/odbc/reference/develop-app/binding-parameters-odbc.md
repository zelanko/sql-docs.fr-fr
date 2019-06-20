---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d62c0864678e116e30a0673bdf2625d70de0cedd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63199608"
---
# <a name="binding-parameters-odbc"></a>Liaison de paramètres dans ODBC
Chaque paramètre dans une instruction SQL doit être associé, ou *lié,* à une variable dans l’application avant que l’instruction est exécutée. Lorsque l’application lie une variable à un paramètre, il décrit cette variable - adresse, type de données C et ainsi de suite - au pilote. Elle décrit également le paramètre lui-même - type de données SQL, précision et ainsi de suite. Le pilote stocke ces informations dans la structure, il tient à jour pour cette instruction et utilise les informations pour extraire la valeur de la variable lorsque l’instruction est exécutée.  
  
 Paramètres peuvent être liés ou reconnectés à tout moment avant l’exécution d’une instruction. Si un paramètre est liée à nouveau après qu’une instruction est exécutée, la liaison ne s’applique pas jusqu'à ce que l’instruction est exécutée à nouveau. Pour lier un paramètre à une variable différente, une application relie simplement le paramètre avec la nouvelle variable ; la liaison précédente est automatiquement publiée.  
  
 Une variable est liée à un paramètre jusqu'à ce qu’une variable différente est liée au paramètre, jusqu'à ce que tous les paramètres sont déliés en appelant **SQLFreeStmt** avec l’option SQL_RESET_PARAMS, ou jusqu'à ce que l’instruction est libérée. Pour cette raison, l’application doit être sûr que les variables ne sont pas libérées jusqu'à ce qu’une fois qu’ils sont dissociées. Pour plus d’informations, consultez [allocation et libération de mémoires tampons](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md).  
  
 Étant donné que les liaisons de paramètres sont simplement des informations stockées dans la structure maintenue par le pilote pour l’instruction, ils peuvent être définies dans n’importe quel ordre. Ils sont également indépendantes de l’instruction SQL qui est exécutée. Par exemple, une application lie les trois paramètres, puis exécute l’instruction SQL suivante :  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Si l’application immédiatement exécute ensuite l’instruction SQL  
  
```  
SELECT * FROM Orders WHERE OrderID = ?, OpenDate = ?, Status = ?  
```  
  
 sur le même descripteur d’instruction, les liaisons de paramètres pour le **insérer** instruction sont utilisés, car ce sont les liaisons stockées dans la structure de l’instruction. Dans la plupart des cas, ceci est une pratique de programmation médiocre et doit être évitée. Au lieu de cela, l’application doit appeler **SQLFreeStmt** avec l’option SQL_RESET_PARAMS pour dissocier tous les paramètres de l’ancien, puis lier d’autres.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Liaison de marqueurs de paramètre](../../../odbc/reference/develop-app/binding-parameter-markers.md)  
  
-   [Liaison de paramètres par nom (paramètres nommés)](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md)  
  
-   [Décalages des liaisons de paramètres](../../../odbc/reference/develop-app/parameter-binding-offsets.md)  
  
-   [Description des paramètres](../../../odbc/reference/develop-app/describing-parameters.md)

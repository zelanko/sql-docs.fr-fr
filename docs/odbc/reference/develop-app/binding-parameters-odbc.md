---
title: Paramètres contraignants ODBC (fr) Microsoft Docs
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
ms.openlocfilehash: 6e314bb9e3a1a979976a450e2a45a286ec54dfe7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306380"
---
# <a name="binding-parameters-odbc"></a>Liaison de paramètres dans ODBC
Chaque paramètre dans une déclaration SQL doit être associé, ou *lié,* à une variable dans la demande avant l’exécution de la déclaration. Lorsque l’application lie une variable à un paramètre, elle décrit cette variable - adresse, type de données C, etc. - au conducteur. Il décrit également le paramètre lui-même - type de données SQL, précision, et ainsi de suite. Le conducteur stocke ces informations dans la structure qu’il conserve pour cette déclaration et utilise les informations pour récupérer la valeur de la variable lorsque l’instruction est exécutée.  
  
 Les paramètres peuvent être liés ou rebondir à tout moment avant qu’une déclaration ne soit exécutée. Si un paramètre est rebondi après l’exécution d’une déclaration, la liaison ne s’applique pas tant que la déclaration n’est pas exécutée à nouveau. Pour lier un paramètre à une variable différente, une application rébinde simplement le paramètre avec la nouvelle variable; la liaison précédente est automatiquement libérée.  
  
 Une variable reste liée à un paramètre jusqu’à ce qu’une variable différente soit liée au paramètre, jusqu’à ce que tous les paramètres ne soient pas liés en appelant **SQLFreeStmt** avec l’option SQL_RESET_PARAMS, ou jusqu’à ce que la déclaration soit publiée. Pour cette raison, l’application doit être sûre que les variables ne sont pas libérées avant qu’elles ne soient non liées. Pour plus d’informations, voir [Allocating and Freeing Buffers](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md).  
  
 Étant donné que les fixations de paramètres ne sont que des informations stockées dans la structure entretenue par le conducteur pour l’instruction, elles peuvent être définies dans n’importe quel ordre. Ils sont également indépendants de la déclaration SQL qui est exécutée. Supposons, par exemple, qu’une application lie trois paramètres et exécute ensuite la déclaration SQL suivante :  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Si l’application exécute immédiatement la déclaration SQL  
  
```  
SELECT * FROM Orders WHERE OrderID = ?, OpenDate = ?, Status = ?  
```  
  
 sur la même poignée de relevé, les fixations de paramètres pour l’instruction **INSERT** sont utilisées parce que ce sont les liaisons stockées dans la structure de l’instruction. Dans la plupart des cas, il s’agit d’une mauvaise pratique de programmation et doit être évitée. Au lieu de cela, l’application devrait appeler **SQLFreeStmt** avec la SQL_RESET_PARAMS option de délier tous les anciens paramètres, puis lier de nouveaux.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Liaison de marqueurs de paramètre](../../../odbc/reference/develop-app/binding-parameter-markers.md)  
  
-   [Liaison de paramètres par nom (paramètres nommés)](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md)  
  
-   [Décalages des liaisons de paramètres](../../../odbc/reference/develop-app/parameter-binding-offsets.md)  
  
-   [Description des paramètres](../../../odbc/reference/develop-app/describing-parameters.md)

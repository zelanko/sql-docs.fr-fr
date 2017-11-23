---
title: "Allocation d’un descripteur d’instruction ODBC | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], statement handles
- statement handles [ODBC]
- allocating statement handles [ODBC]
- handles [ODBC], statement
ms.assetid: 4ce3b446-34ab-46dc-96e5-f40ec95c267e
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2adf6d84d09cb7629f04c66b9ad6e4e66d5f8ee1
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="allocating-a-statement-handle-odbc"></a>Allocation d’un descripteur d’instruction ODBC
Avant de l’application peut exécuter une instruction, elle doit allouer un descripteur d’instruction comme suit :  
  
1.  L’application déclare une variable de type HSTMT. Il appelle ensuite **SQLAllocHandle** et transmet l’adresse de cette variable, le handle de la connexion dans lequel allouer de l’instruction et l’option de SQL_HANDLE_STMT. Exemple :  
  
    ```  
    SQLHSTMT hstmt1;  
  
    SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
    ```  
  
2.  Le Gestionnaire de pilotes alloue une structure permettant de stocker des informations sur l’instruction et les appels **SQLAllocHandle** dans le pilote avec l’option de SQL_HANDLE_STMT.  
  
3.  Le pilote alloue son propre structure dans lequel stocker les informations sur l’instruction et retourne le handle d’instruction de pilote pour le Gestionnaire de pilotes.  
  
4.  Le Gestionnaire de pilotes retourne le handle d’instruction du Gestionnaire de pilotes à l’application dans la variable d’application.  
  
 Le handle d’instruction identifie l’instruction à utiliser lors de l’appel de fonctions ODBC. Pour plus d’informations sur les descripteurs d’instruction, consultez [descripteurs d’instruction](../../../odbc/reference/develop-app/statement-handles.md).

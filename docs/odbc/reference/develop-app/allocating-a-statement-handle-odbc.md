---
title: Allouer une déclaration Poignée ODBC (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], statement handles
- statement handles [ODBC]
- allocating statement handles [ODBC]
- handles [ODBC], statement
ms.assetid: 4ce3b446-34ab-46dc-96e5-f40ec95c267e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bf9a15bc4622b15afa9838327edd90383a812270
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288429"
---
# <a name="allocating-a-statement-handle-odbc"></a>Allocation d’un handle d’instruction dans ODBC
Avant que l’application puisse exécuter une déclaration, elle doit allouer une poignée de déclaration comme suit :  
  
1.  L’application déclare une variable de type HSTMT. Il appelle ensuite **SQLAllocHandle** et passe l’adresse de cette variable, la poignée de la connexion dans laquelle attribuer l’énoncé, et l’option SQL_HANDLE_STMT. Par exemple :  
  
    ```  
    SQLHSTMT hstmt1;  
  
    SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
    ```  
  
2.  Le gestionnaire de chauffeur alloue une structure dans laquelle stocker des informations sur la déclaration et appelle **SQLAllocHandle** dans le conducteur avec l’option SQL_HANDLE_STMT.  
  
3.  Le conducteur alloue sa propre structure pour stocker des informations sur la déclaration et renvoie la poignée de relevé du conducteur au gestionnaire du conducteur.  
  
4.  Le gestionnaire de conducteur renvoie la poignée de relevé de gestionnaire de conducteur à la demande dans la variable d’application.  
  
 La poignée de déclaration identifie l’énoncé à utiliser lors de l’appel des fonctions ODBC. Pour plus d’informations sur les poignées de déclaration, voir [Poignées d’instruction](../../../odbc/reference/develop-app/statement-handles.md).

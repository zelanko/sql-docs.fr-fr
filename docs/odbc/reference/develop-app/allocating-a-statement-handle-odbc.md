---
description: Allocation d’un handle d’instruction dans ODBC
title: Allocation d’un handle d’instruction ODBC | Microsoft Docs
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
ms.openlocfilehash: 624490beee55c7fa37346087fc85b560904f6b93
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487542"
---
# <a name="allocating-a-statement-handle-odbc"></a>Allocation d’un handle d’instruction dans ODBC
Pour que l’application puisse exécuter une instruction, elle doit allouer un descripteur d’instruction comme suit :  
  
1.  L’application déclare une variable de type HSTMT. Il appelle ensuite **SQLAllocHandle** et transmet l’adresse de cette variable, le handle de la connexion dans laquelle l’instruction doit être allouée et l’option SQL_HANDLE_STMT. Par exemple :  
  
    ```  
    SQLHSTMT hstmt1;  
  
    SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
    ```  
  
2.  Le gestionnaire de pilotes alloue une structure dans laquelle stocker des informations sur l’instruction et appelle **SQLAllocHandle** dans le pilote avec l’option SQL_HANDLE_STMT.  
  
3.  Le pilote alloue sa propre structure dans laquelle stocker des informations sur l’instruction et retourne le descripteur d’instruction de pilote au gestionnaire de pilotes.  
  
4.  Le gestionnaire de pilotes renvoie le descripteur d’instruction du gestionnaire de pilotes à l’application dans la variable d’application.  
  
 Le descripteur d’instruction identifie l’instruction à utiliser lors de l’appel de fonctions ODBC. Pour plus d’informations sur les descripteurs d’instruction, consultez [Handles d’instruction](../../../odbc/reference/develop-app/statement-handles.md).

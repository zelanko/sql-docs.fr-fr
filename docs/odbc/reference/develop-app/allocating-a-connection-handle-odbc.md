---
description: Allocation d’un handle de connexion dans ODBC
title: Allocation d’un handle de connexion ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- allocating connection handles [ODBC]
- data sources [ODBC], connection handles
- connecting to data source [ODBC], connection handles
- ODBC drivers [ODBC], connection handles
- connecting to driver [ODBC], connection handles
- connection handles [ODBC]
- handles [ODBC], connection
ms.assetid: c99a8159-7693-4f97-8dcf-401336550e77
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c6c17003ed3746f2953eb167f2dc3d944659e352
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456435"
---
# <a name="allocating-a-connection-handle-odbc"></a>Allocation d’un handle de connexion dans ODBC
Pour que l’application puisse se connecter à une source de données ou à un pilote, elle doit allouer un handle de connexion, comme suit :  
  
1.  L’application déclare une variable de type SQLHDBC. Il appelle ensuite **SQLAllocHandle** et transmet l’adresse de cette variable, le handle de l’environnement dans lequel la connexion doit être allouée et l’option SQL_HANDLE_DBC. Par exemple :  
  
    ```  
    SQLHDBC hdbc1;  
  
    SQLAllocHandle(SQL_HANDLE_DBC, henv1, &hdbc1);  
    ```  
  
2.  Le gestionnaire de pilotes alloue une structure dans laquelle stocker des informations sur l’instruction et retourne le handle de connexion dans la variable.  
  
 Le gestionnaire de pilotes n’appelle pas **SQLAllocHandle** dans le pilote pour l’instant, car il ne sait pas quel pilote appeler. Elle retarde l’appel de **SQLAllocHandle** dans le pilote jusqu’à ce que l’application appelle une fonction pour se connecter à une source de données. Pour plus d’informations, consultez [rôle du gestionnaire de pilotes dans le processus de connexion](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md), plus loin dans cette section.  
  
 Il est important de noter que l’allocation d’un handle de connexion n’est pas la même que le chargement d’un pilote. Le pilote n’est pas chargé tant qu’une fonction de connexion n’a pas été appelée. Ainsi, après avoir alloué un handle de connexion et avant de vous connecter au pilote ou à la source de données, les seules fonctions que l’application peut appeler avec le handle de connexion sont **SQLSetConnectAttr**, **SQLGetConnectAttr**ou **SQLGetInfo** avec l’option SQL_ODBC_VER. L’appel d’autres fonctions avec le descripteur de connexion, tel que **SQLEndTran**, retourne SQLState 08003 (connexion non ouverte). Pour plus d’informations, consultez [annexe B : tables de transition d’État ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Pour plus d’informations sur les handles de connexion, consultez [Handles de connexion](../../../odbc/reference/develop-app/connection-handles.md).

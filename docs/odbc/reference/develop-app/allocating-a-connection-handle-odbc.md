---
title: Allocation d’un descripteur de connexion ODBC | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
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
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a27daadecb685a64d7c5a05e01cda05ec30dd185
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="allocating-a-connection-handle-odbc"></a>Allocation d’un descripteur de connexion ODBC
Avant de l’application peut se connecter à une source de données ou d’un pilote, elle doit allouer un handle de connexion, comme suit :  
  
1.  L’application déclare une variable de type SQLHDBC. Il appelle ensuite **SQLAllocHandle** et transmet l’adresse de cette variable, le handle de l’environnement dans lequel allouer la connexion et l’option de SQL_HANDLE_DBC. Par exemple :  
  
    ```  
    SQLHDBC hdbc1;  
  
    SQLAllocHandle(SQL_HANDLE_DBC, henv1, &hdbc1);  
    ```  
  
2.  Le Gestionnaire de pilotes alloue une structure dans lequel stocker les informations sur l’instruction et retourne le handle de connexion dans la variable.  
  
 Le Gestionnaire de pilotes n’appelle pas **SQLAllocHandle** dans le pilote à cet instant, car il ne connaît pas le pilote à appeler. Il diffère de l’appel **SQLAllocHandle** dans le pilote jusqu'à ce que l’application appelle une fonction pour se connecter à une source de données. Pour plus d’informations, consultez [rôle du Gestionnaire de pilotes dans le processus de connexion](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md), plus loin dans cette section.  
  
 Il est important de noter qu’allouer un handle de connexion n’est pas le même que le chargement d’un pilote. Le pilote n’est pas chargé tant qu’une connexion est appelée. Par conséquent, après avoir alloué un handle de connexion et avant de vous connecter à la source de données ou le pilote, les seules fonctions de l’application peut appeler avec le handle de connexion sont **SQLSetConnectAttr**, **SQLGetConnectAttr**, ou **SQLGetInfo** avec l’option SQL_ODBC_VER. Appel d’autres fonctions avec le handle de connexion, telle que **SQLEndTran**, retourne SQLSTATE 08003 (connexion non ouverte). Pour plus d’informations, consultez [Tables de Transition d’état annexe b : ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Pour plus d’informations sur les handles de connexion, consultez [Handles de connexion](../../../odbc/reference/develop-app/connection-handles.md).

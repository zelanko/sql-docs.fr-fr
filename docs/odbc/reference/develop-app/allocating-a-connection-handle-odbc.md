---
title: Allocation d’un descripteur de connexion ODBC | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 83964bf1e76eef5c7c4ba4121b0c581e8d8a406b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47782407"
---
# <a name="allocating-a-connection-handle-odbc"></a>Allocation d’un handle de connexion dans ODBC
Avant de l’application peut se connecter à une source de données ou d’un pilote, elle doit allouer un handle de connexion, comme suit :  
  
1.  L’application déclare une variable de type SQLHDBC. Il appelle ensuite **SQLAllocHandle** et transfère l’adresse de cette variable, le handle de l’environnement dans lequel d’allouer la connexion et l’option de SQL_HANDLE_DBC. Exemple :  
  
    ```  
    SQLHDBC hdbc1;  
  
    SQLAllocHandle(SQL_HANDLE_DBC, henv1, &hdbc1);  
    ```  
  
2.  Le Gestionnaire de pilotes alloue une structure dans lequel stocker les informations sur l’instruction et retourne le handle de connexion dans la variable.  
  
 Le Gestionnaire de pilotes n’appelle pas **SQLAllocHandle** dans le pilote à cet instant, car il ne sait pas quel pilote à appeler. Celle-ci retarde l’appel **SQLAllocHandle** dans le pilote jusqu'à ce que l’application appelle une fonction pour vous connecter à une source de données. Pour plus d’informations, consultez [rôle du Gestionnaire de pilotes dans le processus de connexion](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md), plus loin dans cette section.  
  
 Il est important de noter qu’allouer un handle de connexion n’est pas le même que le chargement d’un pilote. Le pilote n’est pas chargé jusqu'à ce qu’une fonction de la connexion est appelée. Par conséquent, après avoir alloué un handle de connexion et avant de vous connecter à la source de données ou le pilote, les seules fonctions de l’application peut appeler avec le handle de connexion sont **SQLSetConnectAttr**, **SQLGetConnectAttr**, ou **SQLGetInfo** avec l’option SQL_ODBC_VER. Appelle d’autres fonctions avec le handle de connexion, tel que **SQLEndTran**, retourne SQLSTATE 08003 (connexion non ouverte). Pour plus d’informations, consultez [tableaux des transitions d’état ODBC annexe b :](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Pour plus d’informations sur les handles de connexion, consultez [Handles de connexion](../../../odbc/reference/develop-app/connection-handles.md).

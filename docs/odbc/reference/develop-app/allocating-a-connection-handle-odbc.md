---
title: Allouer une poignée de connexion ODBC (fr) Microsoft Docs
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
ms.openlocfilehash: 12e9f65ee81612e269c1f86ebabd049588443cb8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288519"
---
# <a name="allocating-a-connection-handle-odbc"></a>Allocation d’un handle de connexion dans ODBC
Avant que l’application puisse se connecter à une source de données ou à un pilote, elle doit allouer une poignée de connexion, comme suit :  
  
1.  L’application déclare une variable de type SQLHDBC. Il appelle ensuite **SQLAllocHandle** et passe l’adresse de cette variable, la poignée de l’environnement dans lequel allouer la connexion, et l’option SQL_HANDLE_DBC. Par exemple :  
  
    ```  
    SQLHDBC hdbc1;  
  
    SQLAllocHandle(SQL_HANDLE_DBC, henv1, &hdbc1);  
    ```  
  
2.  Le gestionnaire de conducteur alloue une structure dans laquelle stocker des informations sur l’instruction et renvoie la poignée de connexion dans la variable.  
  
 Le gestionnaire de conducteur n’appelle pas **SQLAllocHandle** dans le conducteur pour le moment parce qu’il ne sait pas quel conducteur appeler. Il retarde l’appel **SQLAllocHandle** dans le conducteur jusqu’à ce que l’application appelle une fonction pour se connecter à une source de données. Pour plus [d’informations,](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md)consultez le rôle du gestionnaire de conducteur dans le processus de connexion , plus tard dans cette section.  
  
 Il est important de noter que l’attribution d’une poignée de connexion n’est pas la même chose que le chargement d’un conducteur. Le conducteur n’est pas chargé jusqu’à ce qu’une fonction de connexion soit appelée. Ainsi, après avoir alloué une poignée de connexion et avant de se connecter au conducteur ou à la source de données, les seules fonctions que l’application peut appeler avec la poignée de connexion sont **SQLSetConnectAttr**, **SQLGetConnectAttr**, ou **SQLGetInfo** avec l’option SQL_ODBC_VER. Appelant d’autres fonctions avec la poignée de connexion, telles que **SQLEndTran**, retourne SQLSTATE 08003 (Connexion non ouverte). Pour plus de détails, voir [Annexe B: ODBC State Transition Tables](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Pour plus d’informations sur les poignées de connexion, voir [Connection Handles](../../../odbc/reference/develop-app/connection-handles.md).

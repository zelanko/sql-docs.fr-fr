---
title: Allouer la poignée de l’environnement Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], environment handles
- allocating environment handles [ODBC]
- connecting to driver [ODBC], environment handles
- environment handles [ODBC]
- data sources [ODBC], environment handles
- connecting to data source [ODBC], environment handles
- handles [ODBC], environment
ms.assetid: 77b5d1d6-7eb7-428d-bf75-a5c5a325d25c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e33b850b2786960a368720deaf89a2203c7dd159
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303002"
---
# <a name="allocating-the-environment-handle"></a>Allocation d’un handle d’environnement
La première tâche pour toute application ODBC est de charger le gestionnaire de conducteur; la façon dont cela est fait dépend du système d’exploitation. Par exemple, sur un ordinateur exécutant Microsoft® Windows NT® Server/Windows 2000 Server, Windows NT Workstation/Windows 2000 Professional, ou Microsoft Windows® 95/98, l’application soit des liens vers la bibliothèque Driver Manager ou appelle **LoadLibrary** pour charger le Driver Manager DLL.  
  
 La tâche suivante, qui doit être faite avant qu’une demande puisse appeler n’importe quelle autre fonction ODBC, est d’initialiser l’environnement ODBC et d’allouer une poignée d’environnement, comme suit :  
  
1.  L’application déclare une variable de type SQLHENV. Il appelle ensuite **SQLAllocHandle** et passe l’adresse de cette variable et l’option SQL_HANDLE_ENV. Par exemple :  
  
    ```  
    SQLHENV henv1;  
  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv1);  
    ```  
  
2.  Le gestionnaire de chauffeur alloue une structure dans laquelle stocker des informations sur l’environnement, et retourne la poignée de l’environnement dans la variable.  
  
 Le gestionnaire de conducteur n’appelle pas **SQLAllocHandle** dans le conducteur pour le moment parce qu’il ne sait pas quel conducteur appeler. Il retarde l’appel **SQLAllocHandle** dans le conducteur jusqu’à ce que l’application appelle une fonction pour se connecter à une source de données. Pour plus [d’informations,](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md)consultez le rôle du gestionnaire de conducteur dans le processus de connexion , plus tard dans cette section.  
  
 Lorsque l’application a terminé l’utilisation d’ODBC, elle libère la poignée de l’environnement avec **SQLFreeHandle**. Après avoir libéré l’environnement, il s’agit d’une erreur de programmation d’applications pour utiliser la poignée de l’environnement dans un appel à une fonction ODBC; conséquences indéfinises mais probablement fatales.  
  
 Lorsque **SQLFreeHandle** est appelé, le conducteur libère la structure utilisée pour stocker des informations sur l’environnement. Notez que **SQLFreeHandle** ne peut pas être appelé pour une poignée d’environnement jusqu’à ce que toutes les poignées de connexion sur cette poignée d’environnement ont été libérées.  
  
 Pour plus d’informations sur la poignée de l’environnement, voir [Environment Handles](../../../odbc/reference/develop-app/environment-handles.md).

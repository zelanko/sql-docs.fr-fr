---
description: Allocation d’un handle d’environnement
title: Allocation du handle d’environnement | Microsoft Docs
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
ms.openlocfilehash: 390d7f4248d43e6fc6cb7910be5f42cb286f37e9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429451"
---
# <a name="allocating-the-environment-handle"></a>Allocation d’un handle d’environnement
La première tâche d’une application ODBC consiste à charger le gestionnaire de pilotes. Cette opération est dépendante du système d’exploitation. Par exemple, sur un ordinateur exécutant Microsoft® Windows NT® Server/Windows 2000 Server, Windows NT Workstation/Windows 2000 Professional ou Microsoft Windows® 95/98, l’application se lie à la bibliothèque du gestionnaire de pilotes ou appelle **LoadLibrary** pour charger la dll du gestionnaire de pilotes.  
  
 La tâche suivante, qui doit être effectuée avant qu’une application puisse appeler une autre fonction ODBC, consiste à initialiser l’environnement ODBC et à allouer un handle d’environnement, comme suit :  
  
1.  L’application déclare une variable de type SQLHENV. Il appelle ensuite **SQLAllocHandle** et transmet l’adresse de cette variable et de l’option SQL_HANDLE_ENV. Par exemple :  
  
    ```  
    SQLHENV henv1;  
  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv1);  
    ```  
  
2.  Le gestionnaire de pilotes alloue une structure dans laquelle stocker des informations sur l’environnement et retourne le handle d’environnement dans la variable.  
  
 Le gestionnaire de pilotes n’appelle pas **SQLAllocHandle** dans le pilote pour l’instant, car il ne sait pas quel pilote appeler. Elle retarde l’appel de **SQLAllocHandle** dans le pilote jusqu’à ce que l’application appelle une fonction pour se connecter à une source de données. Pour plus d’informations, consultez [rôle du gestionnaire de pilotes dans le processus de connexion](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md), plus loin dans cette section.  
  
 Lorsque l’application a terminé d’utiliser ODBC, elle libère le handle d’environnement avec **SQLFreeHandle**. Après la libération de l’environnement, il s’agit d’une erreur de programmation d’application pour utiliser le handle de l’environnement dans un appel à une fonction ODBC. Cela a des conséquences non définies mais probablement irrécupérables.  
  
 Quand **SQLFreeHandle** est appelé, le pilote libère la structure utilisée pour stocker des informations sur l’environnement. Notez que **SQLFreeHandle** ne peut pas être appelé pour un handle d’environnement tant que tous les descripteurs de connexion de ce handle d’environnement n’ont pas été libérés.  
  
 Pour plus d’informations sur le handle d’environnement, consultez [Handles d’environnement](../../../odbc/reference/develop-app/environment-handles.md).

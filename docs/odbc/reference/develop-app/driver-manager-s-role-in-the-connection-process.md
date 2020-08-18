---
description: Rôle&#39;s du gestionnaire de pilotes dans le processus de connexion
title: Rôle&#39;s du gestionnaire de pilotes dans le processus de connexion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver manager [ODBC], role in connection process
- connecting to data source [ODBC], driver manager
- connecting to driver [ODBC], driver manager
- ODBC driver manager [ODBC]
ms.assetid: 77c05630-5a8b-467d-b80e-c705dc06d601
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6fb4eea978604960d87ef6c5b621e5801121c5f1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483042"
---
# <a name="driver-manager39s-role-in-the-connection-process"></a>Rôle&#39;s du gestionnaire de pilotes dans le processus de connexion
N’oubliez pas que les applications n’appellent pas directement les fonctions des pilotes. Au lieu de cela, ils appellent les fonctions du gestionnaire de pilotes avec le même nom et le gestionnaire de pilotes appelle les fonctions du pilote. En règle générale, cela se produit presque immédiatement. Par exemple, l’application appelle **SQLExecute** dans le gestionnaire de pilotes et après quelques vérifications d’erreurs, le gestionnaire de pilotes appelle **SQLExecute** dans le pilote.  
  
 Le processus de connexion est différent. Lorsque l’application appelle **SQLAllocHandle** avec les options SQL_HANDLE_ENV et SQL_HANDLE_DBC, la fonction alloue des handles uniquement dans le gestionnaire de pilotes. Le gestionnaire de pilotes n’appelle pas cette fonction dans le pilote, car il ne sait pas quel pilote appeler. De même, si l’application transmet le descripteur d’une connexion non connectée à **SQLSetConnectAttr** ou **SQLGetConnectAttr**, seul le gestionnaire de pilotes exécute la fonction. Elle stocke ou obtient la valeur de l’attribut à partir de son descripteur de connexion et retourne SQLSTATE 08003 (connexion non ouverte) lors de l’obtention d’une valeur pour un attribut qui n’a pas été défini et pour laquelle ODBC ne définit pas de valeur par défaut.  
  
 Lorsque l’application appelle **SQLConnect**, **SQLDriverConnect**ou **SQLBrowseConnect**, le gestionnaire de pilotes détermine d’abord le pilote à utiliser. Il vérifie ensuite si un pilote est actuellement chargé sur la connexion :  
  
-   Si aucun pilote n’est chargé sur la connexion, le gestionnaire de pilotes vérifie si le pilote spécifié est chargé sur une autre connexion dans le même environnement. Si ce n’est pas le cas, le gestionnaire de pilotes charge le pilote sur la connexion et appelle **SQLAllocHandle** dans le pilote avec l’option SQL_HANDLE_ENV.  
  
     Le gestionnaire de pilotes appelle ensuite **SQLAllocHandle** dans le pilote avec l’option SQL_HANDLE_DBC, qu’il soit ou non chargé. Si l’application définit des attributs de connexion, le gestionnaire de pilotes appelle **SQLSetConnectAttr** dans le pilote. Si une erreur se produit, la fonction de connexion du gestionnaire de pilotes retourne SQLSTATE IM006 (échec **SQLSetConnectAttr** du pilote). Enfin, le gestionnaire de pilotes appelle la fonction de connexion dans le pilote.  
  
-   Si le pilote spécifié est chargé sur la connexion, le gestionnaire de pilotes appelle uniquement la fonction de connexion dans le pilote. Dans ce cas, le pilote doit s’assurer que tous les attributs de connexion de la connexion maintiennent leurs paramètres actuels.  
  
-   Si un autre pilote est chargé sur la connexion, le gestionnaire de pilotes appelle **SQLFreeHandle** dans le pilote pour libérer la connexion. S’il n’existe aucune autre connexion qui utilise le pilote, le gestionnaire de pilotes appelle **SQLFreeHandle** dans le pilote pour libérer l’environnement et décharge le pilote. Le gestionnaire de pilotes effectue ensuite les mêmes opérations que lorsqu’un pilote n’est pas chargé sur la connexion.  
  
 Le gestionnaire de pilotes verrouille le descripteur d’environnement (*henv*) avant d’appeler les appels **SQLAllocHandle** et **SQLFreeHandle** d’un pilote lorsque *comme HandleType* est défini sur **SQL_HANDLE_DBC**.  
  
 Lorsque l’application appelle **SQLDisconnect**, le gestionnaire de pilotes appelle **SQLDisconnect** dans le pilote. Toutefois, il laisse le pilote chargé au cas où l’application se reconnecte au pilote. Lorsque l’application appelle **SQLFreeHandle** avec l’option SQL_HANDLE_DBC, le gestionnaire de pilotes appelle **SQLFreeHandle** dans le pilote. Si le pilote n’est pas utilisé par d’autres connexions, le gestionnaire de pilotes appelle **SQLFreeHandle** dans le pilote avec l’option SQL_HANDLE_ENV et décharge le pilote.

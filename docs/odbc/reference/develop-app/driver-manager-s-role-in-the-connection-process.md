---
title: Driver Manager&#39;s Role in the Connection Process (fr) Microsoft Docs
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
ms.openlocfilehash: 0227a4063573cb05ecaa9434605ba35f2811bd06
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305800"
---
# <a name="driver-manager39s-role-in-the-connection-process"></a>Driver Manager&#39;s Role in the Connection Process
N’oubliez pas que les applications n’appellent pas directement les fonctions du conducteur. Au lieu de cela, ils appellent les fonctions Driver Manager avec le même nom et le gestionnaire de conducteur appelle les fonctions du conducteur. Habituellement, cela arrive presque immédiatement. Par exemple, l’application appelle **SQLExecute** dans le gestionnaire de conducteur et après quelques vérifications d’erreur, le gestionnaire de conducteur appelle **SQLExecute** dans le conducteur.  
  
 Le processus de connexion est différent. Lorsque l’application appelle **SQLAllocHandle** avec les options SQL_HANDLE_ENV et SQL_HANDLE_DBC, la fonction n’attribue que les poignées dans le gestionnaire de conducteur. Le gestionnaire de conducteur n’appelle pas cette fonction dans le conducteur parce qu’il ne sait pas quel conducteur appeler. De même, si l’application passe la poignée d’une connexion non connectée à **SQLSetConnectAttr** ou **SQLGetConnectAttr**, seul le gestionnaire de pilote exécute la fonction. Il stocke ou obtient la valeur d’attribut de sa poignée de connexion et renvoie SQLSTATE 08003 (Connexion non ouverte) lors de l’obtention d’une valeur pour un attribut qui n’a pas été défini et pour lequel ODBC ne définit pas une valeur par défaut.  
  
 Lorsque l’application appelle **SQLConnect**, **SQLDriverConnect**, ou **SQLBrowseConnect**, le gestionnaire de conducteur détermine d’abord quel pilote utiliser. Il vérifie ensuite si un conducteur est actuellement chargé sur la connexion :  
  
-   Si aucun conducteur n’est chargé sur la connexion, le gestionnaire de conducteur vérifie si le conducteur spécifié est chargé sur une autre connexion dans le même environnement. Si ce n’est pas le cas, le gestionnaire de conducteur charge le conducteur sur la connexion et appelle **SQLAllocHandle** dans le conducteur avec l’option SQL_HANDLE_ENV.  
  
     Le gestionnaire du conducteur appelle ensuite **SQLAllocHandle** dans le conducteur avec l’option SQL_HANDLE_DBC, qu’elle soit chargée ou non. Si l’application définit des attributs de connexion, le gestionnaire de pilote appelle **SQLSetConnectAttr** dans le pilote; en cas d’erreur, la fonction de connexion du gestionnaire de conducteur renvoie SQLSTATE IM006 (Driver’s **SQLSetConnectAttr** a échoué). Enfin, le Driver Manager appelle la fonction de connexion dans le conducteur.  
  
-   Si le conducteur spécifié est chargé sur la connexion, le gestionnaire de conducteur n’appelle que la fonction de connexion dans le conducteur. Dans ce cas, le conducteur doit s’assurer que tous les attributs de connexion sur la connexion maintiennent leurs paramètres actuels.  
  
-   Si un autre conducteur est chargé sur la connexion, le gestionnaire de conducteur appelle **SQLFreeHandle** dans le conducteur pour libérer la connexion. S’il n’y a pas d’autres connexions qui utilisent le conducteur, le gestionnaire de conducteur appelle **SQLFreeHandle** dans le conducteur pour libérer l’environnement et décharge le conducteur. Le gestionnaire de conducteur effectue ensuite les mêmes opérations que lorsqu’un conducteur n’est pas chargé sur la connexion.  
  
 Le gestionnaire de conducteur verrouillera la poignée de l’environnement (*henv*) avant d’appeler **SQLAllocHandle** du conducteur et **SQLFreeHandle** lorsque *HandleType* est prêt à **SQL_HANDLE_DBC**.  
  
 Lorsque l’application appelle **SQLDisconnect**, le gestionnaire de conducteur appelle **SQLDisconnect** dans le conducteur. Toutefois, il laisse le conducteur chargé au cas où l’application se reconnecterait au conducteur. Lorsque la demande appelle **SQLFreeHandle** avec l’option SQL_HANDLE_DBC, le gestionnaire de conducteur appelle **SQLFreeHandle** dans le conducteur. Si le conducteur n’est pas utilisé par d’autres connexions, le gestionnaire de conducteur appelle alors **SQLFreeHandle** dans le conducteur avec l’option SQL_HANDLE_ENV et décharge le conducteur.

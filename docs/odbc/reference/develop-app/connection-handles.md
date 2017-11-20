---
title: Handles de connexion | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection handles [ODBC]
- handles [ODBC], connection
ms.assetid: 12222653-f04d-46d6-bdee-61348f5d550f
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ba20d3fcb6d943f4669774013dcb62c8ad896d8d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="connection-handles"></a>Handles de connexion
A *connexion* se compose d’un pilote et une source de données. Un handle de connexion identifie chaque connexion. Le handle de connexion définit non seulement le pilote à utiliser, mais la source de données à utiliser avec ce pilote. Dans un segment de code qui implémente ODBC (le Gestionnaire de pilotes ou un pilote), le handle de connexion identifie une structure qui contient les informations de connexion, tels que les éléments suivants :  
  
-   L’état de la connexion  
  
-   Les diagnostics au niveau de la connexion en cours  
  
-   Les handles d’instructions et les descripteurs actuellement allouées sur la connexion  
  
-   Les paramètres actuels de chaque attribut de connexion  
  
 ODBC n’empêche pas plusieurs connexions simultanées, si le pilote prend en charge les. Par conséquent, dans un environnement ODBC particulier, plusieurs descripteurs de connexion peuvent indiquer une variété de pilotes et les sources de données, sur le même pilote et une variété de sources de données, ou même plusieurs connexions à la même pilote et de la source de données. Certains pilotes de limitent le nombre de connexions actives, qu'ils prennent en charge ; option le SQL_MAX_DRIVER_CONNECTIONS **SQLGetInfo** Spécifie le nombre de connexions actif prend en charge par un pilote spécifique.  
  
 Handles de connexion sont principalement utilisées lors de la connexion à la source de données (**SQLConnect**, **SQLDriverConnect**, ou **SQLBrowseConnect**), déconnexion à partir de la source de données (**SQLDisconnect**), obtention d’informations sur la source de données et de pilote (**SQLGetInfo**), la récupération de diagnostics (**SQLGetDiagField** et **SQLGetDiagRec**) et l’exécution de transactions (**SQLEndTran**). Ils sont également utilisées lors de la définition et l’obtention des attributs de connexion (**SQLSetConnectAttr** et **SQLGetConnectAttr**) et lors de l’obtention du format natif d’une instruction SQL (**SQLNativeSql**).  
  
 Handles de connexion sont allouées avec **SQLAllocHandle** et libérée avec **SQLFreeHandle**.


---
title: Handles de connexion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection handles [ODBC]
- handles [ODBC], connection
ms.assetid: 12222653-f04d-46d6-bdee-61348f5d550f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d5b03e0733e35984350d2a218b885dc148ca8f8f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299019"
---
# <a name="connection-handles"></a>Handles de connexion
Une *connexion* se compose d’un pilote et d’une source de données. Un descripteur de connexion identifie chaque connexion. Le descripteur de connexion définit non seulement le pilote à utiliser mais la source de données à utiliser avec ce pilote. Dans un segment de code qui implémente ODBC (gestionnaire de pilotes ou pilote), le handle de connexion identifie une structure qui contient des informations de connexion, telles que les suivantes :  
  
-   État de la connexion  
  
-   Diagnostics actuels au niveau de la connexion  
  
-   Handles d’instructions et descripteurs actuellement alloués sur la connexion  
  
-   Paramètres actuels de chaque attribut de connexion  
  
 ODBC n’empêche pas plusieurs connexions simultanées, si le pilote les prend en charge. Par conséquent, dans un environnement ODBC particulier, plusieurs descripteurs de connexion peuvent pointer vers une variété de pilotes et de sources de données, vers le même pilote et une variété de sources de données, ou même pour plusieurs connexions au même pilote et à la même source de données. Certains pilotes limitent le nombre de connexions actives qu’ils prennent en charge ; l’option SQL_MAX_DRIVER_CONNECTIONS dans **SQLGetInfo** spécifie le nombre de connexions actives prises en charge par un pilote particulier.  
  
 Les handles de connexion sont principalement utilisés lors de la connexion à la source de données (**SQLConnect**, **SQLDriverConnect**ou **SQLBrowseConnect**), à la déconnexion de la source de données (**SQLDisconnect**), à l’obtention d’informations sur le pilote et la source de données (**SQLGetInfo**), à la récupération des diagnostics (**SQLGetDiagField** et **SQLGetDiagRec**) et à l’exécution des transactions (**SQLEndTran**). Elles sont également utilisées lors de la définition et de l’obtention des attributs de connexion (**SQLSetConnectAttr** et **SQLGetConnectAttr**) et lors de l’obtention du format natif d’une instruction SQL (**SQLNativeSql**).  
  
 Les handles de connexion sont alloués avec **SQLAllocHandle** et libérés avec **SQLFreeHandle**.

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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 77fdb63f346ada40346544a53c3ff69db0a8a9a4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47828938"
---
# <a name="connection-handles"></a>Handles de connexion
Un *connexion* se compose d’un pilote et une source de données. Un handle de connexion identifie chaque connexion. Le handle de connexion définit non seulement le pilote à utiliser, mais la source de données à utiliser avec ce pilote. Dans un segment de code qui implémente ODBC (le Gestionnaire de pilotes ou un pilote), le handle de connexion identifie une structure qui contient les informations de connexion, comme suit :  
  
-   L’état de la connexion  
  
-   Les diagnostics de niveau de la connexion actuelles  
  
-   Les handles d’instructions et descripteurs actuellement alloués sur la connexion  
  
-   Les paramètres actuels de chaque attribut de connexion  
  
 ODBC n’empêche pas plusieurs connexions simultanées, si le pilote prend en charge les. Par conséquent, dans un environnement ODBC particulier, plusieurs handles de connexion peuvent pointer vers une variété de pilotes et les sources de données sur le même pilote et une variété de sources de données, ou même à plusieurs connexions à la même pilote et de la source de données. Certains pilotes de limitent le nombre de connexions actives, qu'elles prennent en charge ; option le SQL_MAX_DRIVER_CONNECTIONS **SQLGetInfo** Spécifie le nombre de connexions actif un pilote spécifique prend en charge.  
  
 Handles de connexion sont principalement utilisées lors de la connexion à la source de données (**SQLConnect**, **SQLDriverConnect**, ou **SQLBrowseConnect**), la déconnexion à partir des données source (**SQLDisconnect**), obtention d’informations sur la source de données et de pilote (**SQLGetInfo**), récupération des diagnostics (**SQLGetDiagField** et **SQLGetDiagRec**) et l’exécution de transactions (**SQLEndTran**). Ils sont également utilisés lors de la définition et l’obtention des attributs de connexion (**SQLSetConnectAttr** et **SQLGetConnectAttr**) et lors de l’obtention du format natif d’une instruction SQL (**SQLNativeSql** ).  
  
 Handles de connexion sont allouées avec **SQLAllocHandle** et libéré avec **SQLFreeHandle**.

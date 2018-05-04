---
title: Handles d’environnement | Documents Microsoft
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
- environment handles [ODBC]
- handles [ODBC], environment
ms.assetid: 917f1b0c-272b-4e37-a1f5-87cd24b9fa21
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0031b874c1fa9d295002518af80b8ea39b48404b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="environment-handles"></a>Handles d’environnement
Un *environnement* est un contexte global d’accès aux données ; associé à un environnement est toute information globale par nature, telles que :  
  
-   État de l’environnement  
  
-   Les diagnostics de niveau de l’environnement actuels  
  
-   Les handles de connexions actuellement allouées sur l’environnement  
  
-   Les paramètres actuels de chaque attribut d’environnement  
  
 Dans un fragment de code qui implémente ODBC (le Gestionnaire de pilotes ou un pilote), un handle d’environnement identifie une structure pour contenir ces informations.  
  
 Handles d’environnement ne sont pas utilisés fréquemment dans les applications ODBC. Ils sont toujours utilisés dans les appels à **SQLDataSources** et **SQLDrivers** et parfois utilisée dans les appels à **SQLAllocHandle**, **SQLEndTran**, **SQLFreeHandle**, **SQLGetDiagField**, et **SQLGetDiagRec**.  
  
 Chaque partie du code qui implémente ODBC (le Gestionnaire de pilotes ou un pilote) contient un ou plusieurs handles d’environnement. Par exemple, le Gestionnaire de pilotes conserve un handle d’environnement distinct pour chaque application qui y est connecté. Handles d’environnement sont allouées avec **SQLAllocHandle** et libérée avec **SQLFreeHandle**.

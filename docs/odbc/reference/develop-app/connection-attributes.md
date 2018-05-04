---
title: Attributs de connexion | Documents Microsoft
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
- data sources [ODBC], connection attributes
- ODBC drivers [ODBC], connection attributes
- connecting to data source [ODBC], connection attributes
- connection attributes [ODBC]
- connecting to driver [ODBC], connection attributes
ms.assetid: e6d03089-30a3-4627-a642-591ba0980894
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8bb986c0cb8b80431a2504d6fa56387a4c08c2c6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="connection-attributes"></a>Attributs de connexion
Attributs de connexion sont des caractéristiques de la connexion. Par exemple, étant donné que les transactions se produisent au niveau de la connexion, le niveau d'isolation de la transaction est un attribut de connexion. De même, le délai de connexion, ou le nombre de secondes d’attente lors de la tentative de connexion avant l’expiration est un attribut de connexion.  
  
 Attributs de connexion sont définis avec **SQLSetConnectAttr** et leurs paramètres actuels sont récupérés avec **SQLGetConnectAttr**. Si **SQLSetConnectAttr** est appelée avant que le pilote est chargé, les magasins de gestionnaire de pilotes les attributs dans la structure de connexion et les définit dans le pilote dans le cadre du processus de connexion. N’est pas obligatoire qu’une application de définir des attributs de connexion ; tous les attributs de connexion ont des valeurs par défaut, dont certaines sont spécifiques au pilote.  
  
 Un attribut de connexion peut être défini avant ou après la connexion ou les deux, en fonction de l’attribut et le pilote. Le délai de connexion (SQL_ATTR_LOGIN_TIMEOUT) s’applique au processus de connexion et est effective uniquement si la valeur est avant de vous connecter. Les attributs qui spécifient si dans utiliser la bibliothèque de curseurs ODBC (SQL_ATTR_ODBC_CURSORS) et le réseau de taille de paquet (SQL_ATTR_PACKET_SIZE) doit être défini avant de vous connecter, car la bibliothèque de curseurs ODBC réside entre le Gestionnaire de pilotes et le pilote et doit être chargée avant le pilote.  
  
 Les attributs pour spécifier si une source de données est en lecture seule ou en lecture-écriture (SQL_ATTR_ACCESS_MODE) et le catalogue actuel (SQL_ATTR_CURRENT_CATALOG) peuvent être définies avant ou après la connexion, selon le pilote. Toutefois, applications interopérables les définir avant de vous connecter, car certains pilotes ne prennent pas en charge modifier ces après vous être connecté.  
  
 Certains attributs de connexion ont une valeur par défaut avant que la connexion est établie, contrairement à d’autres. Celles qui sont SQL_ATTR_ACCESS_MODE SQL_ATTR_AUTOCOMMIT, SQL_ATTR_LOGIN_TIMEOUT, SQL_ATTR_ODBC_CURSORS, SQL_ATTR_TRACE et SQL_ATTR_TRACEFILE.  
  
 Les attributs de connexion de traduction (SQL_ATTR_TRANSLATE_DLL et SQL_ATTR_TRANSLATE_OPTION) doivent être définis après la connexion.  
  
 Tous les autres attributs de connexion peuvent être définies à tout moment. Pour plus d’informations, consultez la [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) description de fonction. (Attributs de connexion ne peut pas être définis au niveau de l’environnement par un appel à **SQLSetEnvAttr**.)

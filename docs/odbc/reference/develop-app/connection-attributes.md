---
title: Attributs de connexion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection attributes
- ODBC drivers [ODBC], connection attributes
- connecting to data source [ODBC], connection attributes
- connection attributes [ODBC]
- connecting to driver [ODBC], connection attributes
ms.assetid: e6d03089-30a3-4627-a642-591ba0980894
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f0fad1db10e40c71d22dd75417420c54cefa7803
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63194439"
---
# <a name="connection-attributes"></a>Attributs de connexion
Attributs de connexion sont les caractéristiques de la connexion. Par exemple, étant donné que les transactions se produisent au niveau de la connexion, le niveau d'isolation de la transaction est un attribut de connexion. De même, le délai de connexion, ou le nombre de secondes d’attente durant la connexion avant l’expiration, est un attribut de connexion.  
  
 Attributs de connexion sont définis avec **SQLSetConnectAttr** et leurs paramètres actuels sont récupérés avec **SQLGetConnectAttr**. Si **SQLSetConnectAttr** est appelée avant que le pilote est chargé, les magasins de gestionnaire de pilotes les attributs dans sa structure de connexion et les définit dans le pilote dans le cadre du processus de connexion. Il n’est pas nécessaire qu’une application définir d’attributs de connexion. tous les attributs de connexion ont des valeurs par défaut, dont certaines sont spécifiques au pilote.  
  
 Un attribut de connexion peut être défini avant ou après la connexion ou les deux, en fonction de l’attribut et le pilote. Le délai d’expiration de connexion (sql_attr_login_timeout permet de contrôler) s’applique au processus de connexion et est effective uniquement si avant de vous connecter. Les attributs qui spécifient s’il faut utiliser la bibliothèque de curseurs ODBC (SQL_ATTR_ODBC_CURSORS) et la taille du paquet réseau (SQL_ATTR_PACKET_SIZE) doivent être définis avant de vous connecter, car la bibliothèque de curseurs ODBC réside entre le Gestionnaire de pilotes et le pilote et Par conséquent, doit être chargé avant le pilote.  
  
 Les attributs pour spécifier si une source de données est en lecture seule ou en lecture-écriture (SQL_ATTR_ACCESS_MODE) et le catalogue actuel (SQL_ATTR_CURRENT_CATALOG) peuvent être définies avant ou après la connexion, selon le pilote. Toutefois, applications interopérables les définir avant de vous connecter, car certains pilotes ne prennent pas en charge modifier ces après s’être connecté.  
  
 Certains attributs de connexion ont une valeur par défaut avant la connexion est établie, contrairement à d’autres pas. Les autres sont SQL_ATTR_ACCESS_MODE SQL_ATTR_AUTOCOMMIT, sql_attr_login_timeout permet de contrôler, SQL_ATTR_ODBC_CURSORS, SQL_ATTR_TRACE et SQL_ATTR_TRACEFILE.  
  
 Les attributs de connexion de traduction (SQL_ATTR_TRANSLATE_DLL et SQL_ATTR_TRANSLATE_OPTION) doivent être définis après la connexion.  
  
 Tous les autres attributs de connexion peuvent être définis à tout moment. Pour plus d’informations, consultez le [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) description de fonction. (Impossible de définir les attributs de connexion sur le niveau de l’environnement par un appel à **SQLSetEnvAttr**.)

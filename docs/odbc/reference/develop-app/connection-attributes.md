---
title: Attributs de connexion Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c295ce88eedf1d4cddc4173f5dea39c44b01f83d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299040"
---
# <a name="connection-attributes"></a>Attributs de connexion
Les attributs de connexion sont des caractéristiques de la connexion. Par exemple, étant donné que les transactions se produisent au niveau de la connexion, le niveau d'isolation de la transaction est un attribut de connexion. De même, le délai de connexion, ou le nombre de secondes à attendre en essayant de se connecter avant de le moment, est un attribut de connexion.  
  
 Les attributs de connexion sont définis avec **SQLSetConnectAttr** et leurs paramètres actuels récupérés avec **SQLGetConnectAttr**. Si **SQLSetConnectAttr** est appelé avant que le conducteur ne soit chargé, le Gestionnaire de conducteur stocke les attributs dans sa structure de connexion et les place dans le conducteur dans le cadre du processus de connexion. Il n’est pas nécessaire qu’une application définisse des attributs de connexion; tous les attributs de connexion ont des défauts, dont certains sont spécifiques au conducteur.  
  
 Un attribut de connexion peut être défini avant ou après la connexion, ou non, selon l’attribut et le pilote. Le délai de connexion (SQL_ATTR_LOGIN_TIMEOUT) s’applique au processus de connexion et n’est efficace que s’il est réglé avant la connexion. Les attributs qui précisent s’il faut utiliser la bibliothèque de curseurs de l’ODBC (SQL_ATTR_ODBC_CURSORS) et la taille du paquet réseau (SQL_ATTR_PACKET_SIZE) doivent être définis avant de se connecter, parce que la bibliothèque de curseurs ODBC se trouve entre le gestionnaire de conducteur et le conducteur et doit donc être chargée avant le conducteur.  
  
 Les attributs pour spécifier si une source de données est lue uniquement ou lue-écriture (SQL_ATTR_ACCESS_MODE) et le catalogue actuel (SQL_ATTR_CURRENT_CATALOG) peuvent être définis avant ou après la connexion, selon le pilote. Cependant, les applications interopérables les définissent avant de se connecter parce que certains pilotes ne prennent pas en charge de les modifier après la connexion.  
  
 Certains attributs de connexion ont un défaut avant que la connexion soit faite, tandis que d’autres ne le font pas. Ceux qui le font sont SQL_ATTR_ACCESS_MODE, SQL_ATTR_AUTOCOMMIT, SQL_ATTR_LOGIN_TIMEOUT, SQL_ATTR_ODBC_CURSORS, SQL_ATTR_TRACE et SQL_ATTR_TRACEFILE.  
  
 Les attributs de connexion de traduction (SQL_ATTR_TRANSLATE_DLL et SQL_ATTR_TRANSLATE_OPTION) doivent être définis après la connexion.  
  
 Tous les autres attributs de connexion peuvent être définis à tout moment. Pour plus d’informations, consultez la description de la fonction [SQLSetConnectAttr.](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) (Les attributs de connexion ne peuvent pas être fixés au niveau de l’environnement par un appel à **SQLSetEnvAttr**.)

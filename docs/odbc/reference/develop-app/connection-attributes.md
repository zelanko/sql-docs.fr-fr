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
ms.openlocfilehash: 09b29277d74383abff1510ca7394aecad036fc7e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036442"
---
# <a name="connection-attributes"></a>Attributs de connexion
Les attributs de connexion sont des caractéristiques de la connexion. Par exemple, étant donné que les transactions se produisent au niveau de la connexion, le niveau d'isolation de la transaction est un attribut de connexion. De même, le délai d’attente de la connexion, ou le nombre de secondes d’attente lors de la tentative de connexion avant expiration, est un attribut de connexion.  
  
 Les attributs de connexion sont définis avec **SQLSetConnectAttr** et leurs paramètres actuels sont récupérés avec **SQLGetConnectAttr**. Si **SQLSetConnectAttr** est appelé avant le chargement du pilote, le gestionnaire de pilotes stocke les attributs dans sa structure de connexion et les définit dans le pilote dans le cadre du processus de connexion. Il n’y a pas d’obligation pour une application de définir des attributs de connexion ; tous les attributs de connexion ont des valeurs par défaut, dont certains sont spécifiques au pilote.  
  
 Un attribut de connexion peut être défini avant ou après la connexion, ou bien, en fonction de l’attribut et du pilote. Le délai d’expiration de connexion (SQL_ATTR_LOGIN_TIMEOUT) s’applique au processus de connexion et est effectif uniquement s’il est défini avant la connexion. Les attributs qui spécifient s’il faut utiliser la bibliothèque de curseurs ODBC (SQL_ATTR_ODBC_CURSORS) et la taille du paquet réseau (SQL_ATTR_PACKET_SIZE) doivent être définis avant la connexion, car la bibliothèque de curseurs ODBC réside entre le gestionnaire de pilotes et le pilote et par conséquent, doit être chargé avant le pilote.  
  
 Les attributs permettant de spécifier si une source de données est en lecture seule ou en lecture-écriture (SQL_ATTR_ACCESS_MODE) et le catalogue actuel (SQL_ATTR_CURRENT_CATALOG) peuvent être définis avant ou après la connexion, en fonction du pilote. Toutefois, les applications interopérables les définissent avant de se connecter, car certains pilotes ne prennent pas en charge leur modification après la connexion.  
  
 Certains attributs de connexion ont une valeur par défaut avant que la connexion ne soit établie, contrairement à d’autres. Ceux qui sont SQL_ATTR_ACCESS_MODE, SQL_ATTR_AUTOCOMMIT, SQL_ATTR_LOGIN_TIMEOUT, SQL_ATTR_ODBC_CURSORS, SQL_ATTR_TRACE et SQL_ATTR_TRACEFILE.  
  
 Les attributs de connexion de traduction (SQL_ATTR_TRANSLATE_DLL et SQL_ATTR_TRANSLATE_OPTION) doivent être définis après la connexion.  
  
 Tous les autres attributs de connexion peuvent être définis à tout moment. Pour plus d’informations, consultez la description de la fonction [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) . (Les attributs de connexion ne peuvent pas être définis au niveau de l’environnement par un appel à **SQLSetEnvAttr**.)

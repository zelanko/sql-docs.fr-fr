---
title: "Sécurisation des Applications JDBC Driver | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90724ec6-a9cb-43ef-903e-793f89410bc0
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e8033e1690fcaa01ca73ce1a7d0d9972ac2d3ba9
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="securing-jdbc-driver-applications"></a>Sécurisation des applications de pilote JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Amélioration de la sécurité d’un [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] application implique plus d’éviter les pièges de codage courants. Une application qui accède à des données présente de nombreux points de défaillance potentiels qu'un intrus peut exploiter en vue d'extraire, de manipuler ou de détruire des données sensibles. Il est important de comprendre tous les aspects de la sécurité, du processus de modélisation des menaces durant la phase de conception de votre application jusqu'à son déploiement final, sans oublier sa maintenance continue.  
  
 Les rubriques de cette section décrivent certains problèmes de sécurité courants, liés entre autres aux chaînes de connexion, à la validation de l'entrée d'utilisateur et à la sécurité générale des applications.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique| Description|  
|-----------|-----------------|  
|[Sécurisation des chaînes de connexion](../../connect/jdbc/securing-connection-strings.md)|Décrit des techniques permettant d'aider à protéger les informations utilisées pour se connecter à une source de données.|  
|[Validation des entrées utilisateur](../../connect/jdbc/validating-user-input.md)|Décrit des techniques permettant de valider l'entrée utilisateur.|  
|[Sécurité des applications](../../connect/jdbc/application-security.md)|Décrit comment utiliser des autorisations de stratégie Java afin d'aider à sécuriser une application de pilote JDBC.|  
|[À l’aide du chiffrement SSL](../../connect/jdbc/using-ssl-encryption.md)|Décrit comment établir un canal de communication sécurisé avec un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] de base de données à l’aide de la couche de Sockets sécurisée (SSL).|  
|[En Mode FIPS](../../connect/jdbc/fips-mode.md)|Décrit comment utiliser le pilote JDBC en mode de plaignant FIPS.| 
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  

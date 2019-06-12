---
title: Sécurisation des Applications de pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 90724ec6-a9cb-43ef-903e-793f89410bc0
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 3a7a8079f60336bbdfe7b837afa2313f5fda2691
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797840"
---
# <a name="securing-jdbc-driver-applications"></a>Sécurisation des applications de pilote JDBC

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

L’amélioration de la sécurité d’une application [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] n’exige pas simplement d’éviter les pièges usuels inhérents au codage. Une application qui accède à des données présente de nombreux points de défaillance potentiels qu'un intrus peut exploiter en vue d'extraire, de manipuler ou de détruire des données sensibles. Il est important de comprendre tous les aspects de la sécurité, du processus de modélisation des menaces durant la phase de conception de votre application jusqu'à son déploiement final, sans oublier sa maintenance continue.  
  
Les rubriques de cette section décrivent certains problèmes de sécurité courants, liés entre autres aux chaînes de connexion, à la validation de l'entrée d'utilisateur et à la sécurité générale des applications.  
  
## <a name="in-this-section"></a>Dans cette section  
  
| Rubrique                                                                            | Description                                                                                                                                                           |
| -------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Sécurisation de chaînes de connexion](../../connect/jdbc/securing-connection-strings.md) | Décrit des techniques permettant d'aider à protéger les informations utilisées pour se connecter à une source de données.                                                                                    |
| [Validation des entrées utilisateur](../../connect/jdbc/validating-user-input.md)             | Décrit des techniques permettant de valider l'entrée utilisateur.                                                                                                                          |
| [Sécurité des applications](../../connect/jdbc/application-security.md)               | Décrit comment utiliser des autorisations de stratégie Java afin d'aider à sécuriser une application de pilote JDBC.                                                                                |
| [Utilisation du chiffrement SSL](../../connect/jdbc/using-ssl-encryption.md)               | Décrit comment établir un canal de communication sécurisé avec une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide du protocole SSL (Secure Sockets Layer). |
| [Mode FIPS](../../connect/jdbc/fips-mode.md)                                     | Décrit comment utiliser le pilote JDBC dans un mode conforme à FIPS.                                                                                                              |
  
## <a name="see-also"></a>Voir aussi  

 [Vue d’ensemble du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  

---
title: "À l’aide du chiffrement SSL | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e566243-2f93-4b21-8065-3c8336649309
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7923995b392dff8c80f1ee6ae3946e421dc46331
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="using-ssl-encryption"></a>Utilisation du chiffrement SSL
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Le chiffrement Secure Sockets Layer (SSL) permet de transmettre les données chiffrées sur le réseau entre une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] et une application cliente.  
  
 Le protocole SSL (Secure Sockets Layer) est un protocole d'établissement de canal de communication sécurisé ayant pour but d'empêcher l'interception d'informations critiques ou sensibles sur les communications réseau et Internet. Il permet au client et au serveur d'effectuer une authentification mutuelle de leur identité. Une fois les participants authentifiés, le protocole SSL fournit des connexions chiffrées entre eux afin de pouvoir transmettre des messages de manière sécurisée.  
  
 Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fournit une infrastructure permettant d’activer et désactiver le chiffrement sur une connexion particulière en fonction de l’utilisateur spécifié des propriétés de connexion, les paramètres de serveur et client. L'utilisateur peut spécifier l'emplacement du magasin de certificats, le mot de passe, un nom d'hôte à utiliser pour valider le certificat et quand chiffrer le canal de communication.  
  
 L'activation du chiffrement SSL améliore la sécurité des données transmises sur des réseaux entre des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] et des applications. Cependant, l'activation du chiffrement ralentit les performances.  
  
 Les rubriques de cette section décrivent comment la [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] version prend en charge le chiffrement SSL, y compris les nouvelles propriétés de connexion, et comment vous pouvez configurer le magasin d’approbations côté client.  
  
> [!NOTE]  
>  Le **hostNameInCertificate** propriété de connexion est recommandée pour valider un certificat SSL.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique| Description|  
|-----------|-----------------|  
|[Présentation de prise en charge SSL](../../connect/jdbc/understanding-ssl-support.md)|Décrit comment la [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] prend en charge le chiffrement SSL.|  
|[La connexion avec le chiffrement SSL](../../connect/jdbc/connecting-with-ssl-encryption.md)|Décrit comment se connecter à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de données à l’aide des nouvelles propriétés de connexion spécifiques de SSL.|  
|[Configuration du Client pour le chiffrement SSL](../../connect/jdbc/configuring-the-client-for-ssl-encryption.md)|Décrit comment configurer le magasin d'approbations par défaut du côté client et comment importer un certificat privé vers le magasin d'approbations de l'ordinateur client.|  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation des Applications du pilote JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  

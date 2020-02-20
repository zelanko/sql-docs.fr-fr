---
title: Utilisation du chiffrement | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: vanto
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8e566243-2f93-4b21-8065-3c8336649309
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9f769e35477d564365df702bd768ac1953c7affa
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "71712973"
---
# <a name="using-encryption"></a>Utilisation du chiffrement

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Le chiffrement TLS (Transport Layer Security) permet la transmission de données chiffrées sur le réseau entre une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et une application cliente.  
  
TLS est un protocole d’établissement de canal de communication sécurisé ayant pour but d’empêcher l’interception d’informations critiques ou sensibles sur les communications réseau et Internet. TLS permet au client et au serveur d’effectuer une authentification mutuelle de leur identité. Une fois les participants authentifiés, TLS fournit des connexions chiffrées entre eux afin de pouvoir transmettre des messages de manière sécurisée.  
  
Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fournit une infrastructure permettant d’activer et de désactiver le chiffrement sur une connexion particulière en fonction des propriétés de connexion spécifiées par l’utilisateur et des paramètres serveur et client. L'utilisateur peut spécifier l'emplacement du magasin de certificats, le mot de passe, un nom d'hôte à utiliser pour valider le certificat et quand chiffrer le canal de communication.  
  
L’activation du chiffrement TLS améliore la sécurité des données transmises sur des réseaux entre des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et des applications. Cependant, l'activation du chiffrement ralentit les performances.  
  
Les rubriques de cette section expliquent comment le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] prend en charge le chiffrement TLS, notamment les nouvelles propriétés de connexion, et comment vous pouvez configurer le magasin d’approbations côté client.  
  
> [!NOTE]  
> La propriété de connexion **hostNameInCertificate** est recommandée pour valider un certificat TLS.  

## <a name="in-this-section"></a>Contenu de cette section  

| Rubrique                                                                                                        | Description                                                                                                                                           |
| ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Présentation de la prise en charge du chiffrement](../../connect/jdbc/understanding-ssl-support.md)                                 | Décrit comment le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] prend en charge le chiffrement TLS.                                              |
| [Connexion avec le chiffrement](../../connect/jdbc/connecting-with-ssl-encryption.md)                       | Décrit comment établir une connexion à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide des nouvelles propriétés de connexion propres au protocole TLS. |
| [Configuration du client pour le chiffrement](../../connect/jdbc/configuring-the-client-for-ssl-encryption.md) | Décrit comment configurer le magasin d'approbations par défaut du côté client et comment importer un certificat privé vers le magasin d'approbations de l'ordinateur client.   |
  
## <a name="see-also"></a>Voir aussi

[Sécurisation des applications du pilote JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  

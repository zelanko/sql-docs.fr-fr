---
title: Utilisation du chiffrement SSL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8e566243-2f93-4b21-8065-3c8336649309
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1453daf6bf9e806a4b3ac79ae8c9a322e5bd0bac
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47771523"
---
# <a name="using-ssl-encryption"></a>Utilisation du chiffrement SSL

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Le chiffrement SSL (Secure Sockets Layer) permet la transmission de données chiffrées sur le réseau entre une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et une application cliente.  
  
Le protocole SSL (Secure Sockets Layer) est un protocole d'établissement de canal de communication sécurisé ayant pour but d'empêcher l'interception d'informations critiques ou sensibles sur les communications réseau et Internet. Il permet au client et au serveur d'effectuer une authentification mutuelle de leur identité. Une fois les participants authentifiés, le protocole SSL fournit des connexions chiffrées entre eux afin de pouvoir transmettre des messages de manière sécurisée.  
  
Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fournit une infrastructure permettant d’activer et de désactiver le chiffrement sur une connexion particulière en fonction des propriétés de connexion spécifiées par l’utilisateur et des paramètres serveur et client. L'utilisateur peut spécifier l'emplacement du magasin de certificats, le mot de passe, un nom d'hôte à utiliser pour valider le certificat et quand chiffrer le canal de communication.  
  
L'activation du chiffrement SSL améliore la sécurité des données transmises sur des réseaux entre des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et des applications. Cependant, l'activation du chiffrement ralentit les performances.  
  
Les rubriques de cette section expliquent comment le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] prend en charge le chiffrement SSL, notamment les nouvelles propriétés de connexion, et comment vous pouvez configurer le magasin d’approbations côté client.  
  
> [!NOTE]  
> Le **hostNameInCertificate** propriété de connexion est recommandée pour valider un certificat SSL.  

## <a name="in-this-section"></a>Dans cette section  

| Rubrique                                                                                                        | Description                                                                                                                                           |
| ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Présentation de la prise en charge de SSL](../../connect/jdbc/understanding-ssl-support.md)                                 | Explique comment le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] prend en charge le chiffrement SSL.                                              |
| [Connexion avec chiffrement SSL](../../connect/jdbc/connecting-with-ssl-encryption.md)                       | Explique comment se connecter à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide des nouvelles propriétés de connexion propres au protocole SSL. |
| [Configuration du client pour le chiffrement SSL](../../connect/jdbc/configuring-the-client-for-ssl-encryption.md) | Décrit comment configurer le magasin d'approbations par défaut du côté client et comment importer un certificat privé vers le magasin d'approbations de l'ordinateur client.   |
  
## <a name="see-also"></a> Voir aussi

[Sécurisation des applications de pilote JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  

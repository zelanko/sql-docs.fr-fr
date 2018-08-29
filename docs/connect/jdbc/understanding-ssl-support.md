---
title: Présentation de prise en charge SSL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 073f3b9e-8edd-4815-88ea-de0655d0325e
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aec0aabb38edc0446728569648dde0a4f4bafedc
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42784894"
---
# <a name="understanding-ssl-support"></a>Fonctionnement de la prise en charge SSL

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Lors de la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], si l’application demande un chiffrement et si l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configurée pour prendre en charge le chiffrement SSL, le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] initie l’établissement d’une liaison SSL. L'établissement d'une liaison permet au serveur et au client de négocier le chiffrement et les algorithmes de chiffrement à utiliser pour protéger les données. Une fois la négociation SSL terminée, le client et le serveur peuvent envoyer les données chiffrées de manière sécurisée. Pendant la négociation SSL, le serveur envoie son certificat de clé publique au client. L'émetteur d'un certificat de clé publique porte le nom d'Autorité de certification. Le client est chargé de vérifier que l'autorité de certification est approuvée par le client.  
  
Si l’application ne nécessite pas de chiffrement, le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] ne force pas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à prendre en charge le chiffrement SSL. Si l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’est pas configurée pour forcer le chiffrement SSL, une connexion est établie sans aucun chiffrement. Si l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configurée pour forcer le chiffrement SSL, le pilote active automatiquement le chiffrement SSL lors de l’exécution sur une machine virtuelle Java (JVM) correctement configurée, sinon la connexion est interrompue et le pilote génère une erreur.  
  
> [!NOTE]  
> Pour garantir une connexion SSL, vérifiez que la valeur transmise à **serverName** correspond exactement au nom CN (Nom commun) ou DNS dans le nom SAN (Autre nom du sujet) du certificat de serveur.  
>
> Pour plus d’informations sur la façon de configurer le protocole SSL pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez la rubrique sur le chiffrement des connexions à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="remarks"></a>Notes 

Pour permettre aux applications d’utiliser le chiffrement SSL, le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] comprend les propriétés de connexion suivantes, à partir de la version 1.2 : **encrypt**, **trustServerCertificate**, **trustStore**, **trustStorePassword** et **hostNameInCertificate**. Pour plus d’informations, consultez [Définition des propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Le tableau suivant résume le comportement de la version du [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] pour les différents scénarios de connexion SSL possibles. Chaque scénario utilise un ensemble différent de propriétés de connexion SSL. Le tableau inclut :  
  
- **vide**: « la propriété n’existe pas dans la chaîne de connexion »  
  
- **valeur**: « la propriété existe dans la chaîne de connexion et sa valeur est valide »  
  
- **n’importe quel**: « Il n’a pas d’importance si la propriété existe dans la chaîne de connexion ou sa valeur n’est valide »  
  
> [!NOTE]  
> Le même comportement s’applique à l’authentification utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et à l’authentification intégrée Windows.  
  
| encrypt        | trustServerCertificate | hostNameInCertificate | trustStore | trustStorePassword | Comportement                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| -------------- | ---------------------- | --------------------- | ---------- | ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| false ou blank | n'importe laquelle                    | n'importe laquelle                   | n'importe laquelle        | n'importe laquelle                | Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] ne forcera pas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à prendre en charge le chiffrement SSL. Si le serveur a un certificat auto-signé, le pilote initie l'échange de certificat SSL. Le certificat SSL ne sera pas validé et seules les informations d'identification (dans le paquet de connexion) sont chiffrées.<br /><br /> Si le serveur requiert que le client prenne en charge le chiffrement SSL, le pilote initiera l'échange de certificat SSL. Le certificat SSL ne sera pas validé, mais la communication entière sera chiffrée.                                                                                                                                                                                    |
| true           | true                   | n'importe laquelle                   | n'importe laquelle        | n'importe laquelle                | Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] demande à utiliser le chiffrement SSL avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Si le serveur requiert que le client prenne en charge le chiffrement SSL ou si le serveur prend en charge le chiffrement, le pilote initiera l'échange de certificat SSL. Notez que si la propriété **trustServerCertificate** a la valeur « true », le pilote ne validera pas le certificat SSL.<br /><br /> Si le serveur n'est pas configuré pour prendre en charge le chiffrement, le pilote déclenchera une erreur et interrompra la connexion.                                                                                                                                                                                          |
| true           | false ou blank         | blank                 | blank      | blank              | Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] demande à utiliser le chiffrement SSL avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Si le serveur requiert que le client prenne en charge le chiffrement SSL ou si le serveur prend en charge le chiffrement, le pilote initiera l'échange de certificat SSL.<br /><br /> Le pilote utilisera la propriété **serverName** spécifiée sur l’URL de connexion pour valider le certificat SSL de serveur et se fiera aux règles de recherche de la fabrique de gestionnaire de confiance pour déterminer le magasin de certificats à utiliser.<br /><br /> Si le serveur n'est pas configuré pour prendre en charge le chiffrement, le pilote déclenchera une erreur et interrompra la connexion.                                                                             |
| true           | false ou blank         | valeur                 | blank      | blank              | Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] demande à utiliser le chiffrement SSL avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Si le serveur requiert que le client prenne en charge le chiffrement SSL ou si le serveur prend en charge le chiffrement, le pilote initiera l'échange de certificat SSL.<br /><br /> Le pilote validera la valeur de sujet du certificat SSL à l’aide de la valeur spécifiée pour la propriété **hostNameInCertificate**.<br /><br /> Si le serveur n'est pas configuré pour prendre en charge le chiffrement, le pilote déclenchera une erreur et interrompra la connexion.                                                                                                                                                                 |
| true           | false ou blank         | blank                 | valeur      | valeur              | Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] demande à utiliser le chiffrement SSL avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Si le serveur requiert que le client prenne en charge le chiffrement SSL ou si le serveur prend en charge le chiffrement, le pilote initiera l'échange de certificat SSL.<br /><br /> Le pilote utilisera la valeur de propriété **trustStore** pour rechercher le fichier trustStore de certificat et la valeur de propriété **trustStorePassword** pour vérifier l’intégrité du fichier trustStore.<br /><br /> Si le serveur n'est pas configuré pour prendre en charge le chiffrement, le pilote déclenchera une erreur et interrompra la connexion.                                                                                                                |
| true           | false ou blank         | blank                 | blank      | valeur              | Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] demande à utiliser le chiffrement SSL avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Si le serveur requiert que le client prenne en charge le chiffrement SSL ou si le serveur prend en charge le chiffrement, le pilote initiera l'échange de certificat SSL.<br /><br /> Le pilote utilisera la valeur de propriété **trustStorePassword** pour vérifier l’intégrité du fichier trustStore par défaut.<br /><br /> Si le serveur n'est pas configuré pour prendre en charge le chiffrement, le pilote déclenchera une erreur et interrompra la connexion.                                                                                                                                                                                  |
| true           | false ou blank         | blank                 | valeur      | blank              | Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] demande à utiliser le chiffrement SSL avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Si le serveur requiert que le client prenne en charge le chiffrement SSL ou si le serveur prend en charge le chiffrement, le pilote initiera l'échange de certificat SSL.<br /><br /> Le pilote utilisera la valeur de propriété **trustStore** pour rechercher l’emplacement du fichier trustStore.<br /><br /> Si le serveur n'est pas configuré pour prendre en charge le chiffrement, le pilote déclenchera une erreur et interrompra la connexion.                                                                                                                                                                                                 |
| true           | false ou blank         | valeur                 | blank      | valeur              | Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] demande à utiliser le chiffrement SSL avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Si le serveur requiert que le client prenne en charge le chiffrement SSL ou si le serveur prend en charge le chiffrement, le pilote initiera l'échange de certificat SSL.<br /><br /> Le pilote utilisera la valeur de propriété **trustStorePassword** pour vérifier l’intégrité du fichier trustStore par défaut. De plus, le pilote utilisera la valeur de propriété **hostNameInCertificate** pour valider le certificat SSL.<br /><br /> Si le serveur n'est pas configuré pour prendre en charge le chiffrement, le pilote déclenchera une erreur et interrompra la connexion.                                                                   |
| true           | false ou blank         | valeur                 | valeur      | blank              | Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] demande à utiliser le chiffrement SSL avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Si le serveur requiert que le client prenne en charge le chiffrement SSL ou si le serveur prend en charge le chiffrement, le pilote initiera l'échange de certificat SSL.<br /><br /> Le pilote utilisera la valeur de propriété **trustStore** pour rechercher l’emplacement du fichier trustStore. De plus, le pilote utilisera la valeur de propriété **hostNameInCertificate** pour valider le certificat SSL.<br /><br /> Si le serveur n'est pas configuré pour prendre en charge le chiffrement, le pilote déclenchera une erreur et interrompra la connexion.                                                                                  |
| true           | false ou blank         | valeur                 | valeur      | valeur              | Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] demande à utiliser le chiffrement SSL avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Si le serveur requiert que le client prenne en charge le chiffrement SSL ou si le serveur prend en charge le chiffrement, le pilote initiera l'échange de certificat SSL.<br /><br /> Le pilote utilisera la valeur de propriété **trustStore** pour rechercher le fichier trustStore de certificat et la valeur de propriété **trustStorePassword** pour vérifier l’intégrité du fichier trustStore. De plus, le pilote utilisera la valeur de propriété **hostNameInCertificate** pour valider le certificat SSL.<br /><br /> Si le serveur n'est pas configuré pour prendre en charge le chiffrement, le pilote déclenchera une erreur et interrompra la connexion. |
  
Si la propriété de chiffrement a la valeur **true**, le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] utilise le fournisseur de sécurité JSSE par défaut de la machine virtuelle Java pour négocier le chiffrement SSL avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le fournisseur de sécurité par défaut peut ne pas prendre en charge toutes les fonctionnalités requises pour négocier le chiffrement SSL avec succès. Par exemple, le fournisseur de sécurité par défaut peut ne pas prendre en charge la taille de la clé publique RSA utilisée dans le certificat SSL [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Dans ce cas, le fournisseur de sécurité par défaut peut générer une erreur qui forcera le pilote JDBC à mettre fin à la connexion. Pour résoudre ce problème, effectuez l'une des opérations suivantes :  
  
- Configurer l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec un certificat de serveur qui a une plus petite clé publique RSA  
  
- Configurer la machine virtuelle Java de façon à utiliser un autre fournisseur de sécurité JSSE dans le fichier de propriétés de sécurité « \<java-home>/lib/security/java.security »  
  
- Utiliser une autre machine virtuelle Java  
  
## <a name="validating-server-ssl-certificate"></a>Validation du certificat SSL de serveur  

Pendant la négociation SSL, le serveur envoie son certificat de clé publique au client. Le client ou pilote JDBC doit confirmer que le certificat de serveur est publié par une autorité de certification approuvée par le client. Le pilote requiert que le certificat de serveur réponde aux conditions suivantes :  
  
- Le certificat a été publié par une autorité de certification approuvée.  
  
- Le certificat doit être publié pour l'authentification de serveur.  
  
- Le certificat n'a pas expiré.  
  
- Le nom CN (Nom commun) du sujet ou le nom DNS du nom SAN (Autre nom du sujet) du certificat correspond exactement à la valeur **serverName** de la chaîne de connexion ou, si elle est spécifiée, à la valeur de la propriété **hostNameInCertificate**.  
  
- Un nom DNS peut comprendre des caractères génériques. En revanche, le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] ne prend pas en charge la correspondance générique. Par exemple, abc.com ne correspondra pas à *.com, mais \*.com correspondra à \*.com.  
  
## <a name="see-also"></a> Voir aussi

[Utilisation du chiffrement SSL](../../connect/jdbc/using-ssl-encryption.md)

[Sécurisation des applications de pilote JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  

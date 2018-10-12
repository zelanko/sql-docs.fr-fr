---
title: Configuration du Client pour le chiffrement SSL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ae34cd1f-3569-4759-80c7-7c9b33b3e9eb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d80c9d8103e7a0a0eeea766487e1fc013ae5e100
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47726627"
---
# <a name="configuring-the-client-for-ssl-encryption"></a>Configuration du client pour le chiffrement SSL
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] ou le client doit s’assurer qu’il s’agit du bon serveur et que son certificat est émis par une autorité de certification approuvée par le client. Pour valider le certificat de serveur, les informations d'approbation doivent être fournies au moment de la connexion. De plus, l'émetteur du certificat de serveur doit être une autorité de certification approuvée par le client.  
  
 Cette rubrique décrit tout d'abord comment fournir les informations d'approbation dans l'ordinateur client. Ensuite, la rubrique décrit comment importer un certificat de serveur vers le magasin d'approbations de l'ordinateur client lorsque l'instance du certificat SSL (Secure Sockets Layer) de l'ordinateur SQL Server est publiée par une autorité de certification privée.  
  
 Pour plus d’informations sur la validation du certificat de serveur, consultez la section Valider le certificat de serveur SSL dans [Comprendre la prise en charge SSL](../../connect/jdbc/understanding-ssl-support.md).  
  
## <a name="configuring-the-client-trust-store"></a>Configuration du magasin d'approbations du client  
 Pour valider le certificat de serveur, il faut que les informations d’approbation soient fournies au moment de la connexion en utilisant explicitement les propriétés de connexion **trustStore** et **trustStorePassword** ou en utilisant implicitement le magasin d’approbations par défaut de la Machine virtuelle Java (JVM) sous-jacente. Pour plus d’informations sur la définition des propriétés **trustStore** et **trustStorePassword** dans une chaîne de connexion, voir [Se connecter avec le chiffrement SSL](../../connect/jdbc/connecting-with-ssl-encryption.md).  
  
 Si la propriété **trustStore** n’est pas spécifiée ou a la valeur Null, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] se fiera au fournisseur de sécurité de la Machine virtuelle Java sous-jacente, SunJSSE (Java Secure Socket Extension). Le fournisseur SunJSSE fournit un TrustManager par défaut, qui permet de valider les certificats X.509 retournés par SQL Server par rapport aux informations d’approbation fournies dans un magasin d’approbations.  
  
 TrustManager tente de localiser le trustStore par défaut dans l’ordre de recherche suivant :  
  
-   Si la propriété système « javax.net.ssl.trustStore » est définie, TrustManager recherche le fichier trustStore par défaut en utilisant le nom de fichier spécifié par cette propriété système.  
  
-   Si la propriété système « javax.net.ssl.trustStore » n’a pas été spécifiée et que le fichier « \<java-home>/lib/security/jssecacerts » existe, c’est ce dernier qui est utilisé.  
  
-   Si le fichier « \<java-home>/lib/security/cacerts » existe, il est utilisé.  
  
 Pour plus d'informations, consultez la documentation d'interface SUNX509 TrustManager sur le site Web de Sun Microsystems.  
  
 Le Java Runtime Environment vous permet de définir les propriétés système trustStore et trustStorePassword comme suit :  
  
```  
java -Djavax.net.ssl.trustStore=C:\MyCertificates\storeName  
java -Djavax.net.ssl.trustStorePassword=storePassword  
```  
  
 Dans ce cas, toute application qui s'exécute sur cette JVM utilisera ces paramètres comme paramètres par défaut. Pour écraser les paramètres par défaut dans votre application, définissez les propriétés de connexion **trustStore** et **trustStorePassword** dans la chaîne de connexion ou dans la méthode setter correspondante de la classe [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md).  
  
 De plus, vous pouvez configurer et gérer les fichiers de magasins d’approbations par défaut, comme « \<java-home>/lib/security/jssecacerts » et « \<java-home>/lib/security/cacerts ». Pour cela, utilisez l'utilitaire « keytool » JAVA installé avec le JRE (Java Runtime Environment). Pour plus d'informations sur l'utilitaire « keytool », consultez la documentation de keytool sur le site Web de Sun Microsystems.  
  
### <a name="importing-the-server-certificate-to-trust-store"></a>Importation du certificat de serveur vers le magasin d'approbations  
 Pendant la négociation SSL, le serveur envoie son certificat de clé publique au client. L'émetteur d'un certificat de clé publique porte le nom d'Autorité de certification. Le client doit s'assurer que l'autorité de certification est approuvée par le client. Il doit pour cela connaître la clé publique des autorités de certification à l'avance. Normalement, la JVM est fournie avec un jeu prédéfini d'autorités de certification approuvées.  
  
 Si l'instance du certificat SSL de SQL Server est publiée par une autorité de certification privée, vous devez ajouter le certificat de l'autorité de certification à la liste de certificats approuvés dans le magasin d'approbations de l'ordinateur client.  
  
 Pour cela, utilisez l’utilitaire « keytool » Java installé avec l’environnement JRE (Java Runtime Environment). L'invite de commandes suivante montre comment utiliser l'utilitaire « keytool » pour importer un certificat à partir d'un fichier :  
  
```  
keytool -import -v -trustcacerts -alias myServer -file caCert.cer -keystore truststore.ks  
```  
  
 L'exemple utilise un fichier nommé « caCert.cer » comme fichier de certificat. Vous devez obtenir ce fichier de certificat à partir du serveur. Les étapes suivantes expliquent comment exporter le certificat de serveur vers un fichier :  
  
1.  Cliquez sur Démarrer, sur Exécuter, puis tapez MMC. (MMC signifie Microsoft Management Console.)  
  
2.  Dans la console MMC, ouvrez le dossier Certificats.  
  
3.  Développez Personnel, puis Certificats.  
  
4.  Cliquez avec le bouton droit sur le certificat de serveur, puis sélectionnez Toutes les tâches\Exporter.  
  
5.  Cliquez sur Suivant pour passer la boîte de dialogue d'accueil de l'Assistant Exportation de certificat.  
  
6.  Vérifiez que l'option « Non, ne pas exporter la clé privée » est sélectionnée, puis cliquez sur Suivant.  
  
7.  Assurez-vous que Binaire codé DER X.509 (.cer) ou Codé à base 64 X.509 (.cer) est sélectionné, puis cliquez sur Suivant.  
  
8.  Entrez un nom de fichier d'exportation.  
  
9. Cliquez sur Suivant, puis cliquez sur Terminer pour exporter le certificat.  
  
## <a name="see-also"></a> Voir aussi  
 [Utilisation du chiffrement SSL](../../connect/jdbc/using-ssl-encryption.md)   
 [Sécurisation des applications de pilote JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  

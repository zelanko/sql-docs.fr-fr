---
title: Connexion avec le chiffrement SSL | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ec91fa8a-ab7e-4c1e-a05a-d7951ddf33b1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5ccbd9db2ae39113ca157651bdc6dc1486307419
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028156"
---
# <a name="connecting-with-ssl-encryption"></a>Connexion avec le chiffrement SSL
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Les exemples de cet article décrivent comment utiliser les propriétés de chaîne de connexion qui permettent aux applications d’utiliser le chiffrement SSL (Secure Sockets Layer) dans une application Java. Pour plus d’informations sur ces nouvelles propriétés de chaîne de connexion, comme **encrypt**, **trustServerCertificate**, **trustStore**, **trustStorePassword** et **hostNameInCertificate**, consultez [Définition des propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Quand la propriété **encrypt** est définie sur **true** et que la propriété **trustServerCertificate** est définie sur **true**, le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] ne valide pas le certificat SSL [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ceci est généralement nécessaire pour autoriser les connexions dans les environnements de test, par exemple quand l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a seulement un certificat auto-signé.  
  
 L’exemple de code suivant montre comment définir la propriété **trustServerCertificate** dans une chaîne de connexion :  
  
```java
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true;trustServerCertificate=true";  
```  
  
 Quand la propriété **encrypt** est définie sur **true** et que la propriété **trustServerCertificate** est définie sur **false**, le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] valide le certificat SSL [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La validation du certificat de serveur est une partie de la négociation SSL qui garantit qu'il s'agit du serveur correct avec lequel établir une connexion. Pour valider le certificat de serveur, les informations d’approbation doivent être fournies au moment de la connexion en utilisant explicitement les propriétés de connexion **trustStore** et **trustStorePassword**, ou en utilisant implicitement le magasin d’approbations par défaut de la machine virtuelle Java (JVM) sous-jacente.  
  
 La propriété **trustStore** spécifie le chemin (y compris le nom de fichier) du fichier trustStore de certificat, qui contient la liste des certificats approuvés par le client. La propriété **trustStorePassword** spécifie le mot de passe utilisé pour vérifier l’intégrité des données trustStore. Pour plus d’informations sur l’utilisation du magasin d’approbations par défaut de la machine virtuelle Java, consultez [configuration du client pour le chiffrement SSL](../../connect/jdbc/configuring-the-client-for-ssl-encryption.md).  
  
 L’exemple de code suivant montre comment définir les propriétés **trustStore** et **trustStorePassword** dans une chaîne de connexion :  
  
```java
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true; trustServerCertificate=false;" +  
     "trustStore=storeName;trustStorePassword=storePassword";  
```  
  
 Le pilote JDBC fournit une propriété supplémentaire, **hostNameInCertificate**, qui spécifie le nom d’hôte du serveur. La valeur de cette propriété doit correspondre à la propriété de sujet du certificat.  
  
 L’exemple de code suivant montre comment utiliser la propriété **hostNameInCertificate** dans une chaîne de connexion :  
  
```java
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true; trustServerCertificate=false;" +  
     "trustStore=storeName;trustStorePassword=storePassword" +  
     "hostNameInCertificate=hostName";  
```  
  
> [!NOTE]  
>  Vous pouvez également définir la valeur des propriétés de connexion en utilisant les méthodes **setter** appropriées fournies par la classe [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md).  
  
 Si la propriété **Encrypt** a la valeur **true** et que la propriété **TrustServerCertificate** a la valeur **false** et si le nom du serveur dans la chaîne de connexion ne correspond pas au nom du serveur dans le certificat SSL, l’erreur suivante est publié le `The driver couldn't establish a secure connection to SQL Server by using Secure Sockets Layer (SSL) encryption. Error: "java.security.cert.CertificateException: Failed to validate the server name in a certificate during Secure Sockets Layer (SSL) initialization."`:. À partir de la version 7,2, le pilote prend en charge la correspondance de modèle de caractères génériques dans l’étiquette la plus à gauche du nom du serveur dans le certificat SSL.
## <a name="see-also"></a>Voir aussi  
 [Utilisation du chiffrement SSL](../../connect/jdbc/using-ssl-encryption.md)   
 [Sécurisation des applications du pilote JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  

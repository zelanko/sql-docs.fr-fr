---
title: Utilisation de l’authentification intégrée Kerberos pour se connecter à SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 687802dc-042a-4363-89aa-741685d165b3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fd82f894db2afc469c40c883deab2071b0e89f98
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51600449"
---
# <a name="using-kerberos-integrated-authentication-to-connect-to-sql-server"></a>Utilisation de l’authentification intégrée Kerberos pour se connecter à SQL Server

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

À compter de [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)], les applications peuvent utiliser la propriété de connexion **authenticationScheme** pour indiquer qu’elles souhaitent se connecter à une base de données à l’aide de l’authentification intégrée Kerberos de type 4. Consultez [définissant les propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md) pour plus d’informations sur les propriétés de connexion. Pour plus d’informations sur Kerberos, consultez [Microsoft Kerberos](https://go.microsoft.com/fwlink/?LinkID=100758).

Lors de l’utilisation de l’authentification intégrée avec le **Krb5LoginModule** Java, vous pouvez configurer le module à l’aide de la [classe Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html).

Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] permet de définir les propriétés suivantes pour les machines virtuelles Java IBM :

- **useDefaultCcache = true**
- **moduleBanner = false**

Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] permet de définir les propriétés suivantes pour toutes les autres machines virtuelles Java :

- **useTicketCache = true**
- **doNotPrompt = true**

## <a name="remarks"></a>Notes 

Antérieures à [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)], applications pouvaient spécifier l’authentification intégrée (à l’aide de Kerberos ou NTLM, selon ce qui est disponible) à l’aide de la **integratedSecurity** propriété de connexion et en référençant  **sqljdbc_auth.dll**, comme décrit dans [Building the Connection URL](../../connect/jdbc/building-the-connection-url.md).

À compter de [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)], les applications peuvent utiliser la propriété de connexion **authenticationScheme** pour indiquer qu’elles souhaitent se connecter à une base de données à l’aide de l’authentification intégrée Kerberos et de l’implémentation pure Kerberos Java :

- Si vous souhaitez à l’aide de l’authentification intégrée **Krb5LoginModule**, vous devez toujours spécifier le **integratedSecurity = true** propriété de connexion. Puis spécifiez également le **authenticationScheme = Java Kerberos** propriété de connexion.

- Pour continuer à utiliser l’authentification intégrée avec **sqljdbc_auth.dll**, il suffit de spécifier **integratedSecurity = true** propriété de connexion (et éventuellement **authenticationScheme = NativeAuthentication**).

- Si vous spécifiez **authenticationScheme = Java Kerberos** mais ne spécifiez pas **integratedSecurity = true**, le pilote ignorera la **authenticationScheme** propriété de connexion et s’attendra à trouver des informations d’identification de nom et mot de passe utilisateur dans la chaîne de connexion.

Quand vous utilisez une source de données pour créer des connexions, vous pouvez définir par programmation le schéma d’authentification à l’aide de setAuthenticationScheme et (éventuellement) de définir le SPN pour les connexions Kerberos à l’aide de **setServerSpn**.

Un nouvel enregistreur d'événements a été ajouté pour la prise en charge de l'authentification Kerberos : com.microsoft.sqlserver.jdbc.internals.KerbAuthentication. Pour plus d’informations, consultez [Suivi du fonctionnement du pilote](../../connect/jdbc/tracing-driver-operation.md).

Les consignes suivantes vous aideront à configurer Kerberos :

1. Définissez **AllowTgtSessionKey** sur 1 dans le Registre pour Windows. Pour plus d’informations, consultez [Entrées de Registre du protocole Kerberos et clés de configuration KDC dans Windows Server 2003](https://support.microsoft.com/kb/837361).
2. Assurez-vous que la configuration Kerberos (krb5.conf dans les environnements UNIX) référence le bon domaine et le centre de distribution de clés (KDC) convenant à votre environnement.
3. Initialisez le cache des tickets TGT à l'aide de l'outil kinit, en vous connectant au domaine.
4. Quand une application utilisant **authenticationScheme=JavaKerberos** s’exécute sur les systèmes d’exploitation Windows Vista ou Windows 7, vous devez utiliser un compte d’utilisateur standard. Toutefois, si vous exécutez l'application à l'aide d'un compte d'administrateur, vous devrez l'exécuter à l'aide de privilèges administrateur.

> [!NOTE]  
> L’attribut de connexion serverSpn est uniquement pris en charge par Microsoft JDBC Driver 4.2 et versions ultérieures.

## <a name="service-principal-names"></a>Noms des principaux du service

Le nom de principal du service (SPN) est le nom par lequel un client identifie de manière unique l'instance d'un service.

Vous pouvez spécifier le SPN à l’aide de la propriété de connexion **serverSpn**, ou simplement laisser le pilote le créer pour vous (par défaut). Cette propriété a le format suivant : « MSSQLSvc/fqdn:port\@REALM », où fqdn désigne le nom de domaine complet, port désigne le numéro de port et REALM désigne le domaine Kerberos du serveur SQL Server en majuscules. La partie domaine de cette propriété est facultative si le domaine par défaut de votre configuration Kerberos est le même que celui du serveur et n'est pas inclus par défaut. Si vous voulez prendre en charge un scénario d'authentification entre domaines où le domaine par défaut dans la configuration Kerberos est différent de celui du serveur, vous devez définir le SPN avec la propriété serverSpn.

Par exemple, votre SPN peut se présenter comme : « MSSQLSvc/some-server.zzz.corp.contoso.com:1433\@ZZZZ. CORP. CONTOSO.COM »

Pour plus d'informations sur les noms des principaux du service (SPN), consultez :

- [Guide pratique pour utiliser l’authentification Kerberos avec SQL Server](https://support.microsoft.com/kb/319723)

- [Utilisation de Kerberos avec SQL Server](https://go.microsoft.com/fwlink/?LinkId=207814)

> [!NOTE]  
> Avant la version 6.2 du pilote JDBC, pour une utilisation correcte du protocole Kerberos Realm Cross, vous devez définir explicitement la **serverSpn**.
>
> Depuis la version 6.2, le pilote sera en mesure de générer le **serverSpn** par défaut, même si vous utilisez Kerberos de domaine Cross. Bien que vous pouvez utiliser **serverSpn** explicitement trop.

## <a name="creating-a-login-module-configuration-file"></a>Création d'un fichier de configuration d'un module de connexion

Vous pouvez, si vous le désirez, créer un fichier de configuration Kerberos. Si vous ne spécifiez pas de fichier de configuration, les paramètres suivants seront appliqués :

Machine virtuelle Java Sun  
 com.sun.security.auth.module.Krb5LoginModule required useTicketCache=true;

Machine virtuelle Java IBM  
 com.ibm.security.auth.module.Krb5LoginModule required useDefaultCcache = true;

Si vous décidez de créer un fichier de configuration de module de connexion, le fichier doit respecter le format suivant :

```java
<name> {  
    <LoginModule> <flag> <LoginModule options>;  
    <optional_additional_LoginModules, flags_and_options>;  
};  
```

Un fichier de configuration de connexion est composé d'une ou plusieurs entrées, chacune spécifiant la technologie d'authentification sous-jacente qui doit être utilisée pour une application en particulier. Par exemple,

```java
SQLJDBCDriver {  
   com.sun.security.auth.module.Krb5LoginModule required useTicketCache=true;  
};  
```

Chaque entrée de fichier de configuration de module de connexion correspond à un nom suivi d'une ou de plusieurs entrées spécifiques à LoginModule, où chaque entrée spécifique à LoginModule est suivie d'un point-virgule et où la totalité des entrées spécifiques à LoginModule est comprise entre accolades. Chaque entrée du fichier de configuration se termine par un point-virgule.

En plus de permettre au pilote d'acquérir les informations d'identification Kerberos à l'aide des paramètres spécifiés dans le fichier de configuration du module de connexion, le pilote peut utiliser les informations d'identification existantes. Cela peut se révéler utile si votre application doit créer des connexions utilisant les informations d'identification de plusieurs utilisateurs.

Le pilote tentera d'utiliser les informations d'identification existantes si disponibles, avant de tenter de se connecter au module de connexion spécifié. Par conséquent, lorsque vous utilisez la méthode Subject.doAs pour exécuter le code dans un contexte particulier, une connexion sera créée avec les informations d'identification transmises à l'appel Subject.doAs.

Pour plus d’informations, consultez [JAAS Login Configuration File](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/LoginConfigFile.html) et [Class Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html).

À compter de Microsoft JDBC Driver 6.2, nom de fichier de configuration de module de connexion peut éventuellement être passé à l’aide de jaasConfigurationName de propriété de connexion, cela permet à chaque connexion à avoir sa propre configuration de connexion.

## <a name="creating-a-kerberos-configuration-file"></a>Création d'un fichier de configuration Kerberos

Pour plus d’informations sur les fichiers de configuration Kerberos, consultez [Kerberos Requirements](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/KerberosReq.html).

Voici un exemple de fichier de configuration de domaine, où YYYY et ZZZZ correspondent aux noms de domaine de votre site.

```ini
[libdefaults]  
default_realm = YYYY.CORP.CONTOSO.COM  
dns_lookup_realm = false  
dns_lookup_kdc = true  
ticket_lifetime = 24h  
forwardable = yes  

[domain_realm]  
.yyyy.corp.contoso.com = YYYY.CORP.CONTOSO.COM  
.zzzz.corp.contoso.com = ZZZZ.CORP.CONTOSO.COM  

[realms]  
        YYYY.CORP.CONTOSO.COM = {  
  kdc = krbtgt/YYYY.CORP. CONTOSO.COM @ YYYY.CORP. CONTOSO.COM  
  default_domain = YYYY.CORP. CONTOSO.COM  
}  

        ZZZZ.CORP. CONTOSO.COM = {  
  kdc = krbtgt/ZZZZ.CORP. CONTOSO.COM @ ZZZZ.CORP. CONTOSO.COM  
  default_domain = ZZZZ.CORP. CONTOSO.COM  
}  

```

## <a name="enabling-the-domain-configuration-file-and-the-login-module-configuration-file"></a>Activation du fichier de configuration de domaine et du fichier de configuration du module de connexion

Le fichier de configuration de domaine peut être activé à l'aide de -Djava.security.krb5.conf. Vous pouvez activer un fichier de configuration de module de connexion avec **-Djava.security.auth.login.config**.

Par exemple, lorsque vous démarrez votre application, vous pouvez utiliser la ligne de commande suivante :

```bash
Java.exe -Djava.security.auth.login.config=SQLJDBCDriver.conf -Djava.security.krb5.conf=krb5.ini <APPLICATION_NAME>  

```

## <a name="verifying-that-sql-server-can-be-accessed-via-kerberos"></a>Vérification de l'accessibilité de SQL Server via Kerberos

Exécutez la requête suivante dans SQL Server Management Studio :

```sql
select auth_scheme from sys.dm_exec_connections where session_id=\@\@spid
```

Assurez-vous de disposer de l'autorisation nécessaire pour exécuter cette requête.

## <a name="constrained-delegation"></a>Délégation contrainte

À compter de Microsoft JDBC Driver 6.2, le pilote prend en charge la délégation contrainte Kerberos. Les informations d’identification déléguées peuvent être passées dans en tant qu’objet de org.ietf.jgss.GSSCredential, ces informations d’identification sont utilisées par le pilote pour établir la connexion.

```java
Properties driverProperties = new Properties();
GSSCredential impersonatedUserCredential = [userCredential]
driverProperties.setProperty("integratedSecurity", "true");
driverProperties.setProperty("authenticationScheme", "JavaKerberos");
driverProperties.put("gsscredential", impersonatedUserCredential);
Connection conn = DriverManager.getConnection(CONNECTION_URI, driverProperties);
```

## <a name="kerberos-connection-using-principal-names-and-password"></a>Connexion de Kerberos à l’aide des noms de Principal et le mot de passe

À compter de Microsoft JDBC Driver 6.2, le pilote peut établir Kerberos à l’aide du nom de Principal et le mot de passe de connexion transmise dans la chaîne de connexion.

```java
jdbc:sqlserver://servername=server_name;integratedSecurity=true;authenticationScheme=JavaKerberos;userName=user@REALM;password=****
```

La propriété de nom d’utilisateur ne nécessite pas de domaine si l’utilisateur appartient à la default_realm définie dans le fichier krb5.conf. Lorsque `userName` et `password` est défini avec `integratedSecurity=true;` et `authenticationScheme=JavaKerberos;` propriété, la connexion est établie avec la valeur du nom d’utilisateur en tant que le Principal Kerberos le long avec le mot de passe fourni.

## <a name="see-also"></a> Voir aussi

[Connexion à SQL Server avec le pilote JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)

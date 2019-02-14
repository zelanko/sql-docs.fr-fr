---
title: Utilisation de l’authentification intégrée Kerberos pour se connecter à SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 687802dc-042a-4363-89aa-741685d165b3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d67a368c1c33d9f3c85e36d15ad2b77fe7837c88
ms.sourcegitcommit: 879a5c6eca99e0e9cc946c653d4ced165905d9c6
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2019
ms.locfileid: "55736990"
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

Quand vous utilisez une source de données pour créer des connexions, vous pouvez définir par programmation le schéma d’authentification à l’aide de **setAuthenticationScheme** et (éventuellement) définir le SPN pour les connexions Kerberos à l’aide de **setServerSpn**.

Un nouvel enregistreur d'événements a été ajouté pour la prise en charge de l'authentification Kerberos : com.microsoft.sqlserver.jdbc.internals.KerbAuthentication. Pour plus d’informations, consultez [Suivi du fonctionnement du pilote](../../connect/jdbc/tracing-driver-operation.md).

Les consignes suivantes vous aideront à configurer Kerberos :

1. Définissez **AllowTgtSessionKey** sur 1 dans le Registre pour Windows. Pour plus d’informations, consultez [Entrées de Registre du protocole Kerberos et clés de configuration KDC dans Windows Server 2003](https://support.microsoft.com/kb/837361).
2. Assurez-vous que la configuration Kerberos (krb5.conf dans les environnements UNIX) référence le bon domaine et le centre de distribution de clés (KDC) convenant à votre environnement.
3. Initialisez le cache des tickets TGT à l'aide de l'outil kinit, en vous connectant au domaine.
4. Quand une application utilisant **authenticationScheme=JavaKerberos** s’exécute sur les systèmes d’exploitation Windows Vista ou Windows 7, vous devez utiliser un compte d’utilisateur standard. Toutefois, si vous exécutez l’application à l’aide d’un compte d’administrateur, vous devrez l’exécuter à l’aide de privilèges d’administrateur.

> [!NOTE]  
> L’attribut de connexion serverSpn est uniquement pris en charge par Microsoft JDBC Driver 4.2 et versions ultérieures.

## <a name="service-principal-names"></a>Noms des principaux du service

Le nom de principal du service (SPN) est le nom par lequel un client identifie de manière unique l'instance d'un service.

Vous pouvez spécifier le SPN à l’aide de la propriété de connexion **serverSpn**, ou simplement laisser le pilote le créer pour vous (par défaut). Cette propriété a le format suivant : « MSSQLSvc/fqdn:port\@REALM », où fqdn désigne le nom de domaine complet, port désigne le numéro de port et REALM désigne le domaine Kerberos du serveur SQL Server en majuscules. La partie domaine (realm) de cette propriété est facultative si le domaine par défaut de votre configuration Kerberos est le même que celui du serveur et n’est pas inclus par défaut. Si vous voulez prendre en charge un scénario d'authentification entre domaines où le domaine par défaut dans la configuration Kerberos est différent de celui du serveur, vous devez définir le SPN avec la propriété serverSpn.

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

En plus de permettre au pilote d'acquérir les informations d'identification Kerberos à l'aide des paramètres spécifiés dans le fichier de configuration du module de connexion, le pilote peut utiliser les informations d'identification existantes. Cela peut se révéler utile si votre application doit créer des connexions utilisant les informations d’identification de plusieurs utilisateurs.

Le pilote tentera d'utiliser les informations d'identification existantes si disponibles, avant de tenter de se connecter au module de connexion spécifié. Par conséquent, quand vous utilisez la méthode `Subject.doAs` pour exécuter le code dans un contexte spécifique, une connexion est créée avec les informations d’identification passées à l’appel `Subject.doAs`.

Pour plus d’informations, consultez [JAAS Login Configuration File](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/LoginConfigFile.html) et [Class Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html).

À compter de Microsoft JDBC Driver 6.2, nom de fichier de configuration de module de connexion peut éventuellement être transmis à l’aide de la propriété de connexion `jaasConfigurationName`, cela permet à chaque connexion à avoir sa propre configuration de connexion.

## <a name="creating-a-kerberos-configuration-file"></a>Création d'un fichier de configuration Kerberos

Pour plus d’informations sur les fichiers de configuration Kerberos, consultez [Kerberos Requirements](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/KerberosReq.html).

Voici un exemple de fichier de configuration de domaine, où YYYY et ZZZZ correspondent aux noms de domaine.

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

Par exemple, la commande suivante peut être utilisée pour démarrer l’application :

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

## <a name="using-kerberos-authentication-from-unix-machines-on-the-same-domain"></a>À l’aide de l’authentification Kerberos à partir d’ordinateurs Unix sur le même domaine

Ce guide suppose un travail de l’installation de Kerberos existe déjà. Exécutez le code suivant sur un ordinateur Windows avec l’utilisation de l’authentification Kerberos pour vérifier si la valeur est true. Le code imprimera « schéma d’authentification : KERBEROS » dans la console en cas de réussite. Aucun des indicateurs d’exécution supplémentaires, des dépendances ou paramètres du pilote ne sont nécessaires en dehors de celles fournies. Le même bloc de code peut être exécuté sur Linux pour vérifier les connexions réussies.

```java
SQLServerDataSource ds = new SQLServerDataSource();
ds.setServerName("<server>");
ds.setPortNumber(1433); // change if necessary
ds.setIntegratedSecurity(true);
ds.setAuthenticationScheme("JavaKerberos");
ds.setDatabaseName("<database>");

try (Connection c = ds.getConnection(); Statement s = c.createStatement();
        ResultSet rs = s.executeQuery("select auth_scheme from sys.dm_exec_connections where session_id=@@spid")) {
    while (rs.next()) {
        System.out.println("Authentication Scheme: " + rs.getString(1));
    }
}
```

1. Joignez l’ordinateur client au même domaine que le serveur.
2. (Facultatif) Définissez l’emplacement de ticket Kerberos par défaut. Cela est effectuée plus facilement en définissant le `KRB5CCNAME` variable d’environnement.
3. Obtenir le ticket Kerberos, soit en générant un nouveau ou en plaçant un existant dans l’emplacement de ticket Kerberos par défaut. Pour générer un ticket, utiliser un terminal et initialiser le ticket via `kinit USER@DOMAIN.AD` où « Utilisateur » et « domaine. AD » est le principal et le domaine respectivement. Par exemple : `kinit SQL_SERVER_USER03@MICROSOFT.COM`. Le ticket est généré dans l’emplacement du ticket par défaut ou dans le `KRB5CCNAME` chemin d’accès si définie.
4. Le terminal vous demandera un mot de passe, entrez le mot de passe.
5. Vérifiez les informations d’identification dans le ticket via `klist` et confirmez les informations d’identification sont celles que vous souhaitez utiliser pour l’authentification.
6. Exécutez l’exemple de code ci-dessus et confirmez la réussite de l’authentification Kerberos.

## <a name="see-also"></a> Voir aussi

[Connexion à SQL Server avec le pilote JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)

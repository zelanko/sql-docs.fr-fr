---
title: Utilisation de l'authentification intégrée Kerberos pour se connecter à SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 687802dc-042a-4363-89aa-741685d165b3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8eaa889f12adb2470040cab4c0fba5df295a1cb2
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86916235"
---
# <a name="using-kerberos-integrated-authentication-to-connect-to-sql-server"></a>Utilisation de l'authentification intégrée Kerberos pour se connecter à SQL Server

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

À compter de [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)], les applications peuvent utiliser la propriété de connexion **authenticationScheme** pour indiquer qu’elles souhaitent se connecter à une base de données à l’aide de l’authentification intégrée Kerberos de type 4. Consultez [Définition des propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md) pour en savoir plus sur les propriétés de connexion. Pour plus d’informations sur Kerberos, consultez [Microsoft Kerberos](https://go.microsoft.com/fwlink/?LinkID=100758).

Lors de l’utilisation de l’authentification intégrée avec le **Krb5LoginModule** Java, vous pouvez configurer le module à l’aide de la [classe Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html).

Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] permet de définir les propriétés suivantes pour les machines virtuelles Java IBM :

- **useDefaultCcache = true**
- **moduleBanner = false**

Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] permet de définir les propriétés suivantes pour toutes les autres machines virtuelles Java :

- **useTicketCache = true**
- **doNotPrompt = true**

## <a name="remarks"></a>Notes

Avant [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)], les applications pouvaient spécifier l'authentification intégrée (à l'aide de Kerberos ou de NTLM, selon les disponibilités) en utilisant la propriété de connexion **integratedSecurity** et en référençant **mssql-jdbc_auth-\<version>-\<arch>.dll**, comme décrit dans [Génération de l'URL de connexion](../../connect/jdbc/building-the-connection-url.md).

À compter de [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)], les applications peuvent utiliser la propriété de connexion **authenticationScheme** pour indiquer qu’elles souhaitent se connecter à une base de données à l’aide de l’authentification intégrée Kerberos et de l’implémentation pure Kerberos Java :

- Si vous souhaitez que l'authentification intégrée utilise **Krb5LoginModule**, vous devez spécifier la propriété de connexion **integratedSecurity=true**. Vous devez alors également spécifier la propriété de connexion **authenticationScheme=JavaKerberos**.

- Pour continuer à utiliser l’authentification intégrée avec **mssql-jdbc_auth-\<version>-\<arch>.dll**, il vous suffit de spécifier la propriété de connexion **integratedSecurity=true** (et éventuellement **authenticationScheme=NativeAuthentication**).

- Si vous spécifiez **authenticationScheme=JavaKerberos** sans spécifier également **integratedSecurity=true**, le pilote ignorera la propriété de connexion **authenticationScheme** et s'attendra à trouver le nom d'utilisateur et les informations d'identification dans la chaîne de connexion.

Quand vous utilisez une source de données pour créer des connexions, vous pouvez définir par programmation le schéma d’authentification à l’aide de **setAuthenticationScheme** et (éventuellement) définir le SPN pour les connexions Kerberos à l’aide de **setServerSpn**.

Un nouvel enregistreur d'événements a été ajouté pour la prise en charge de l'authentification Kerberos : com.microsoft.sqlserver.jdbc.internals.KerbAuthentication. Pour plus d'informations, consultez [Suivi du fonctionnement du pilote](../../connect/jdbc/tracing-driver-operation.md).

Les consignes suivantes vous aideront à configurer Kerberos :

1. Affectez la valeur 1 à **AllowTgtSessionKey** dans le registre pour Windows. Pour plus d’informations, consultez [Entrées de Registre du protocole Kerberos et clés de configuration KDC dans Windows Server 2003](https://support.microsoft.com/kb/837361).
2. Assurez-vous que la configuration Kerberos (krb5.conf dans les environnements UNIX) référence le bon domaine et le centre de distribution de clés (KDC) convenant à votre environnement.
3. Initialisez le cache des tickets TGT à l'aide de l'outil kinit, en vous connectant au domaine.
4. Quand une application utilisant **authenticationScheme=JavaKerberos** s’exécute sur les systèmes d’exploitation Windows Vista ou Windows 7, vous devez utiliser un compte d’utilisateur standard. Toutefois, si vous exécutez l’application à l’aide d’un compte d’administrateur, vous devrez l’exécuter à l’aide de privilèges d’administrateur.

> [!NOTE]  
> L’attribut de connexion serverSpn est uniquement pris en charge par Microsoft JDBC Driver 4.2 et versions ultérieures.

## <a name="service-principal-names"></a>Noms des principaux du service

Le nom de principal du service (SPN) est le nom par lequel un client identifie de manière unique l'instance d'un service.

Vous pouvez spécifier le SPN à l’aide de la propriété de connexion **serverSpn**, ou simplement laisser le pilote le créer pour vous (par défaut). Cette propriété prend la forme suivante : « MSSQLSvc/fqdn:port\@REALM », où fqdn désigne le nom de domaine complet, port désigne le numéro de port et REALM désigne le domaine Kerberos du serveur SQL Server en majuscules. La partie domaine (realm) de cette propriété est facultative si le domaine par défaut de votre configuration Kerberos est le même que celui du serveur et n’est pas inclus par défaut. Si vous voulez prendre en charge un scénario d'authentification entre domaines où le domaine par défaut dans la configuration Kerberos est différent de celui du serveur, vous devez définir le SPN avec la propriété serverSpn.

Par exemple, votre SPN peut ressembler à ce qui suit : "MSSQLSvc/some-server.zzz.corp.contoso.com:1433\@ZZZZ.CORP.CONTOSO.COM"

Pour plus d'informations sur les noms des principaux du service (SPN), consultez :

- [Inscrire un nom de principal du service pour les connexions Kerberos](../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md)

- [Utilisation de Kerberos avec SQL Server](https://docs.microsoft.com/archive/blogs/sql_protocols/using-kerberos-with-sql-server)

> [!NOTE]  
> Avant la version 6.2 du pilote JDBC, pour utiliser correctement l’approbation de domaine croisé, vous deviez définir explicitement le **serverSpn**.
>
> Depuis la version 6.2, le pilote est en mesure de générer le **serverSpn** par défaut, bien qu’il soit possible d’utiliser l’approbation de domaine croisé. Il est également possible d’utiliser explicitement le **serverSpn**.

## <a name="creating-a-login-module-configuration-file"></a>Création du fichier de configuration d'un module de connexion

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

À partir de Microsoft JDBC Driver 6.2, le nom du fichier de configuration du module de connexion peut éventuellement être transmis à l’aide de la propriétés de connexion `jaasConfigurationName`, ce qui permet à chaque connexion d’avoir sa propre configuration de connexion.

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

## <a name="enabling-the-domain-configuration-file-and-the-login-module-configuration-file"></a>Activation du fichier de configuration du domaine et du fichier de configuration du module de connexion

Le fichier de configuration de domaine peut être activé à l'aide de -Djava.security.krb5.conf. Vous pouvez activer le fichier de configuration d’un module de connexion avec **-Djava.security.auth.login.config**.

Par exemple, la commande suivante peut être utilisée pour démarrer l’application :

```bash
Java.exe -Djava.security.auth.login.config=SQLJDBCDriver.conf -Djava.security.krb5.conf=krb5.ini <APPLICATION_NAME>  

```

## <a name="verifying-that-sql-server-can-be-accessed-via-kerberos"></a>Vérification de l'accessibilité de SQL Server via Kerberos

Exécutez la requête suivante dans SQL Server Management Studio :

```sql
select auth_scheme from sys.dm_exec_connections where session_id=\@\@spid
```

Assurez-vous de disposer de l'autorisation nécessaire pour exécuter cette requête.

## <a name="constrained-delegation"></a>Délégation contrainte

À partir du pilote Microsoft JDBC 6.2, le pilote prend en charge la délégation contrainte Kerberos. Les informations d’identification déléguées peuvent être transmises en tant qu’objet org.ietf.jgss.GSSCredential. Ces informations d’identification sont utilisées par le pilote pour établir la connexion.

```java
Properties driverProperties = new Properties();
GSSCredential impersonatedUserCredential = [userCredential]
driverProperties.setProperty("integratedSecurity", "true");
driverProperties.setProperty("authenticationScheme", "JavaKerberos");
driverProperties.put("gsscredential", impersonatedUserCredential);
Connection conn = DriverManager.getConnection(CONNECTION_URI, driverProperties);
```

## <a name="kerberos-connection-using-principal-names-and-password"></a>Connexion Kerberos utilisant les noms des principaux et le mot de passe

À partir du pilote Microsoft JDBC 6.2, le pilote peut établir une connexion Kerberos à l’aide du nom du principal et du mot de passe transmis dans la chaîne de connexion.

```java
jdbc:sqlserver://servername=server_name;integratedSecurity=true;authenticationScheme=JavaKerberos;userName=user@REALM;password=****
```

La propriété username ne requiert pas de domaine si l’utilisateur appartient au default_realm défini dans le fichier krb5.conf. Lorsque `userName` et `password` sont définis avec les propriétés `integratedSecurity=true;` et `authenticationScheme=JavaKerberos;`, la connexion est établie avec la valeur userName en tant que principal Kerberos en même temps que le mot de passe est fourni.

## <a name="using-kerberos-authentication-from-unix-machines-on-the-same-domain"></a>Utilisation de l’authentification Kerberos à partir d’ordinateurs Unix sur le même domaine

Ce guide suppose qu’une configuration Kerberos opérationnelle existe déjà. Exécutez le code suivant sur un ordinateur Windows avec l’authentification Kerberos opérationnelle pour vérifier si la condition ci-dessus est vraie. Le code affiche « Schéma d’authentification : KERBEROS » sur la console en cas de réussite. Des indicateurs d’exécution, dépendances ou paramètre de pilote autres que ceux fournis ne sont pas nécessaires. Le même bloc de code peut être exécuté sur Linux pour vérifier que les connexions sont bien établies.

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

1. Joindre le domaine de l’ordinateur client au même domaine que le serveur.
2. (Facultatif) Définissez l’emplacement par défaut du ticket Kerberos. Pour ce faire, il est plus pratique de définir la variable d’environnement `KRB5CCNAME`.
3. Obtenir le ticket Kerberos en générant un nouveau ou en plaçant un ticket existant dans l’emplacement par défaut du ticket Kerberos. Pour générer un ticket, il vous suffit d’utiliser un terminal et d’initialiser le ticket via `kinit USER@DOMAIN.AD`, où « USER » et « DOMAIN.AD » sont respectivement le principal et le domaine. Par exemple : `kinit SQL_SERVER_USER03@MICROSOFT.COM`. Le ticket sera généré à l’emplacement par défaut du ticket ou dans le chemin `KRB5CCNAME` si ce dernier a été défini.
4. Entrez le mot de passe lorsque le terminal vous y invite.
5. Vérifiez les informations d’identification dans le ticket via `klist` et vérifiez que les informations d’identification sont bien celles que vous envisagez d’utiliser pour l’authentification.
6. Exécutez l’exemple de code ci-dessus et vérifiez que l’authentification Kerberos s’est correctement déroulée.

## <a name="see-also"></a>Voir aussi

[Connexion à SQL Server avec le pilote JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)

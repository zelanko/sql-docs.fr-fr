---
title: Notes de publication pour le pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 02/06/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 074f211e-984a-4b76-bb15-ee36f5946f12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b720f2b146273fb694ad0a55b013d20bd65a6a6a
ms.sourcegitcommit: c61c7b598aa61faa34cd802697adf3a224aa7dc4
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56154867"
---
# <a name="release-notes-for-the-jdbc-driver"></a>Notes de publication pour le pilote JDBC

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

## <a name="updates-in-microsoft-jdbc-driver-72-for-sql-server"></a>Mises à jour apportées à Microsoft JDBC Driver 7.2 pour SQL Server

7.2 de pilote JDBC Microsoft pour SQL Server est entièrement conforme à la spécification de l’API JDBC 4.2. Les fichiers JAR dans le package 7.2 sont nommées en fonction de la compatibilité des versions de Java. Par exemple, le fichier mssql-jdbc-7.2.1.jre11.jar à partir du package 7.2 doit être utilisé avec Java 11.

> [!NOTE]  
> Un problème avec l’analyse des instructions SQL a été trouvé dans le pilote JDBC 7.2 RTW publié le 31 janvier 2019. La modification a été annulée, et les nouveaux fichiers JAR (version 7.2.1) ont été publiées le 11 février 2019. 
>
> Téléchargez les dernières mises à jour pour 7.2 du pilote JDBC à partir de [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=2063159), [GitHub](https://github.com/Microsoft/mssql-jdbc/releases/tag/v7.2.1), et [Maven Central](https://search.maven.org/search?q=g:com.microsoft.sqlserver). Mettez à jour vos projets pour utiliser le 7.2.1 libérer les fichiers JAR. Pour plus d’informations, voir les notes de version pour [7.2.1](https://github.com/Microsoft/mssql-jdbc/releases/tag/v7.2.1).


### <a name="support-for-jdk-11"></a>Prise en charge du Kit JDK 11

7.2 de pilote JDBC Microsoft pour SQL Server est désormais compatible avec Java Development Kit (JDK) version 11.0, en plus de JDK 1.8.

### <a name="support-for-active-directory-managed-service-identity-msi-authentication"></a>Prise en charge pour l’authentification Active Directory Managed Service Identity (MSI)

7.2 de pilote JDBC Microsoft pour SQL Server prend désormais en charge le mode d’authentification Active Directory Managed Service Identity (MSI). Ce mode d’authentification est applicable sur les ressources Azure avec prise en charge de la fonctionnalité « Identité » est activée. Les deux types d’identités système administré (MSI) sont pris en charge par le pilote d’acquérir **accessToken** pour établir une connexion sécurisée.

Plus de détails et un exemple d’application pour utiliser ce mode d’authentification sont accessibles ici : [connexion à l’aide de l’authentification Azure Active Directory](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md)

### <a name="osgi-support"></a>Prise en charge OSGi

7.2 de pilote JDBC Microsoft pour SQL Server prend désormais en charge OSGi au pilote en ajoutant ci-dessous pour les implémentations `org.osgi.service.jdbc.DataSourceFactory` et `org.osgi.framework.BundleActivator` :

- `com.microsoft.sqlserver.jdbc.osgi.SQLServerDataSourceFactory`
- `com.microsoft.sqlserver.jdbc.osgi.Activator`

### <a name="sqlservererror-apis"></a>API de SQLServerError

7.2 de pilote JDBC Microsoft pour SQL Server introduit `SQLServerException.getSQLServerError()` et `SQLServerError` getter API afin de récupérer des détails supplémentaires sur l’erreur générée à partir du serveur. Pour plus d’informations, consultez [Gestion des erreurs](../../connect/jdbc/handling-errors.md).

### <a name="updated-microsoft-azure-active-directory-authentication-library-adal4j-for-java-version-163"></a>Mise à jour de la « bibliothèque d’authentification Microsoft Azure Active Directory (ADAL4J) pour Java » : version 1.6.3

7.2 de pilote JDBC Microsoft pour SQL Server a mis à jour sa dépendance Maven sur « Microsoft Azure Active Directory Authentication Library (ADAL4J) pour Java » vers la version 1.6.3, ce qui introduit également « Exécution de Client Java pour AutoRest » en tant que dépendance Maven (Version : 1.6.5).). Pour plus d’informations sur les dépendances, consultez [dépendances de fonctionnalité de Microsoft JDBC Driver pour SQL Server](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md).

### <a name="updated-microsoft-azure-key-vault-sdk-for-java-version-120"></a>Version de mise à jour « Microsoft Azure Key Vault SDK pour Java » : 1.2.0

7.2 de pilote JDBC Microsoft pour SQL Server a mis à jour sa dépendance Maven, sur « Microsoft Azure clé de coffre SDK pour Java » vers la version 1.2.0, qui introduit également « Microsoft Azure SDK pour Key Vault WebKey » comme une dépendance Maven (Version : 1.2.0). Pour plus d’informations sur les dépendances, consultez [dépendances de fonctionnalité de Microsoft JDBC Driver pour SQL Server](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md).

### <a name="known-issues"></a>Problèmes connus

Avec Microsoft JDBC Driver 7.2 pour SQL Server, il existe un problème connu avec certaines des requêtes paramétrées. Une mise à jour de la version 7.2 (v7.2.1), sera bientôt disponible pour résoudre ce problème.


## <a name="updates-in-microsoft-jdbc-driver-70-for-sql-server"></a>Mises à jour apportées à Microsoft JDBC Driver 7.0 pour SQL Server

7.0 de pilote JDBC Microsoft pour SQL Server est entièrement conforme à la spécification de l’API JDBC 4.2. Les fichiers JAR dans le package 7.0 sont nommées en fonction de la compatibilité des versions de Java. Par exemple, le fichier mssql-jdbc-7.0.0.jre10.jar à partir du package 7.0 doit être utilisé avec Java 10.

### <a name="support-for-jdk-10"></a>Prise en charge de JDK 10

7.0 de pilote JDBC Microsoft pour SQL Server est désormais compatible avec Java Development Kit (JDK) version 10.0, en plus de JDK 1.8. Cette mise à jour expose également le pilote `Automatic-Module-Name` comme `com.microsoft.sqlserver.jdbc` via son fichier de manifeste.

### <a name="support-for-spatial-datatypes"></a>Prise en charge des types de données spatiaux

7.0 de pilote JDBC Microsoft pour SQL Server prend désormais en charge pour SQL Server spatial types de données Geography et Geometry. Pour plus d’informations sur le type de données spatial API et comment les utiliser, consultez [à l’aide des types de données spatiales](../../connect/jdbc/use-spatial-datatypes.md).

### <a name="implementation-for-jdbc-43-introduced-javasqlconnection-apis-beginrequest-and-endrequest"></a>Implémentation des API java.sql.Connection beginRequest() et endRequest() introduites dans JDBC 4.3

7.0 de pilote JDBC Microsoft pour SQL Server maintenant implémente `beginRequest()` et `endRequest()` API à partir de la `java.sql.Connection` classe. Ces API ont été introduites avec les spécifications de JDBC 4.3 et JDK 9. Pour plus d’informations sur l’implémentation du pilote de ces API, consultez [conformité JDBC 4.3 pour le pilote JDBC](../../connect/jdbc/jdbc-4-3-compliance-for-the-jdbc-driver.md).

### <a name="support-for-sql-data-discovery-and-classification"></a>Prise en charge de la découverte et de la classification des données SQL

7.0 de pilote JDBC Microsoft pour SQL Server prend en charge la découverte de données SQL et de classification avec une base de données cible qui prend en charge cette fonctionnalité. Le pilote expose désormais `SQLServerResultSet.getSensitivityClassification()` API pour extraire ces informations à partir de l’extraction `ResultSet`.

Pour plus d’informations sur la façon d’utiliser cette fonctionnalité avec le pilote JDBC, consultez l’exemple dans [SQL données découverte et classification](../../connect/jdbc/data-discovery-classification-sample.md).

### <a name="added-connection-property-usebulkcopyforbatchinsert"></a>Propriété de connexion est ajoutée : useBulkCopyForBatchInsert

7.0 de pilote JDBC Microsoft pour SQL Server introduit une nouvelle propriété de connexion, `useBulkCopyForBatchInsert`. Cette propriété est prise en charge uniquement pour Azure SQL Data Warehouse.

Cette propriété est désactivée par défaut. Vous pouvez lui permettre d’augmenter les performances des applications de l’utilisateur lorsque vous êtes en exécutant un push de données de grandes quantités vers Azure SQL Data Warehouse. L’activation de cette propriété modifie le comportement des opérations d’insertion de lot pour basculer vers les opérations de copie en bloc avec des données fournies par l’utilisateur. Pour plus d’informations sur cette propriété et ses limitations, consultez [opération d’insertion à l’aide des API de copie en bloc pour le lot](../../connect/jdbc/use-bulk-copy-api-batch-insert-operation.md).

### <a name="added-connection-property-cancelquerytimeout"></a>Propriété de connexion est ajoutée : cancelQueryTimeout

7.0 de pilote JDBC Microsoft pour SQL Server introduit une nouvelle propriété de connexion, `cancelQueryTimeout`, pour annuler `queryTimeout` sur `java.sql.Connection` et `java.sql.Statement` objets.

### <a name="added-azure-key-vault-provider-constructors"></a>Constructeurs d’Azure Key Vault Provider ajoutés

7.0 de pilote JDBC Microsoft pour SQL Server réintroduit un constructeur précédemment supprimé, pour `SQLServerColumnEncryptionAzureKeyVaultProvider`. Il autorisé d’authentification via une méthode personnalisée est implémentée via `SQLServerKeyVaultAuthenticationCallback` pour extraire un jeton d’accès.

Les constructeurs de nouveau utiliser la définition suivante :

```java
/* This constructor is added to provide backward compatibility with 6.0
* version of the driver. It is marked deprecated for removal in the next
* stable release.
*/
@Deprecated
public SQLServerColumnEncryptionAzureKeyVaultProvider(
        SQLServerKeyVaultAuthenticationCallback authenticationCallback,
        ExecutorService executorService) throws SQLServerException;

/*New constructor to replace the above constructor*/
public SQLServerColumnEncryptionAzureKeyVaultProvider(
            SQLServerKeyVaultAuthenticationCallback authenticationCallback) throws SQLServerException;
```

### <a name="updated-microsoft-azure-active-directory-authentication-library-adal4j-for-java-version-160"></a>Mise à jour de la « bibliothèque d’authentification Microsoft Azure Active Directory (ADAL4J) pour Java » : version 1.6.0

7.0 de pilote JDBC Microsoft pour SQL Server a mis à jour sa dépendance Maven sur « Microsoft Azure Active Directory Authentication Library (ADAL4J) pour Java » vers la version 1.6.0. Pour plus d’informations sur les dépendances, consultez [dépendances de fonctionnalité de Microsoft JDBC Driver pour SQL Server](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md).

## <a name="updates-in-microsoft-jdbc-driver-64-for-sql-server"></a>Mises à jour apportées à Microsoft JDBC Driver 6.4 pour SQL Server

Microsoft JDBC Driver 6.4 pour SQL Server est entièrement conforme aux spécifications de JDBC 4.1 et 4.2. Les fichiers JAR dans le package de 6,4 sont nommées en fonction de la compatibilité des versions de Java. Par exemple, le fichier mssql-jdbc-6.4.0.jre8.jar à partir du package 6,4 doit être utilisé avec Java 8.

### <a name="support-for-jdk-9"></a>Prise en charge de JDK 9

Le pilote prend en charge JDK version 9.0 en plus de JDK 8.0 et 7.0.

### <a name="jdbc-43-compliance"></a>Conformité JDBC 4.3

Le pilote prend en charge la spécification de l’API Java Database Connectivity 4.3, en plus des versions 4.1 et 4.2. Les méthodes de l’API JDBC 4.3 sont ajoutés, mais pas encore implémentés. Pour plus d’informations, consultez [Conformité à JDBC 4.3 pour le pilote JDBC](../../connect/jdbc/jdbc-4-3-compliance-for-the-jdbc-driver.md).

### <a name="added-connection-property-sslprotocol"></a>Propriété de connexion est ajoutée : sslProtocol

Une nouvelle propriété de connexion permet aux utilisateurs de spécifier le mot de clé du protocole TLS. Les valeurs possibles sont : « TLS », « TLSv1 », « TLSv1.1 » et « TLSv1.2 ». Pour plus d’informations, consultez [SSLProtocol](https://github.com/Microsoft/mssql-jdbc/wiki/SSLProtocol).

### <a name="deprecated-connection-property-fipsprovider"></a>Propriété de connexion déconseillée : fipsProvider

La propriété de connexion `fipsProvider` est supprimé de la liste des propriétés de connexion acceptée. Pour plus d’informations, consultez connexe [demande de tirage GitHub](https://github.com/Microsoft/mssql-jdbc/pull/460).

### <a name="added-connection-properties-for-specifying-a-custom-trustmanager"></a>Propriétés de connexion ajouté pour spécifier un TrustManager personnalisé

Le pilote maintenant ajouté prend en charge en spécifiant un TrustManager personnalisé avec `trustManagerClass` et `trustManagerConstructorArg` propriétés de connexion. Vous pouvez dynamiquement spécifier un jeu de certificats approuvés sur une base par connexion sans modifier les paramètres globaux pour l’environnement de machine virtuelle (JVM) Java.

### <a name="added-support-for-datetimesmalldatetime-in-table-valued-parameters"></a>Prise en charge pour datetime/smallDatetime dans les paramètres table

Le pilote prend désormais en charge les types de données `datetime` et `smallDatetime` lorsque vous utilisez des paramètres table (TVP).

### <a name="added-support-for-the-sqlvariant-datatype"></a>Prise en charge pour le type de données sql_variant

Le pilote JDBC prend désormais en charge `sql_variant` les types de données à utiliser avec SQL Server. Le `sql_variant` type de données est également prise en charge des fonctionnalités telles que les paramètres table et de copie en bloc avec les limitations suivantes :

* **Pour les valeurs de date** : 

  Lorsque vous utilisez TVP pour remplir une table qui contient `datetime`, `smalldatetime`, ou `date` valeurs stockées dans un `sql_variant` colonne, en appelant le `getDateTime()`, `getSmallDateTime()`, ou `getDate()` ne fonctionne pas sur le jeu de résultats (méthode) et lève l’exception suivante :

  `java java.lang.String cannot be cast to java.sql.Timestamp`
    
  Pour résoudre ce problème, utilisez le `getString()` ou `getObject()` méthode à la place.

* **Utilisation d’un paramètre table (TVP) avec sql_variant pour les valeurs null** :
  
  Si vous utilisez TVP pour remplir une table et envoyer une valeur NULL à la `sql_variant` type de colonne, vous rencontrerez une exception. Insertion d’une valeur NULL avec le type de colonne `sql_variant` dans TVP est actuellement pas pris en charge.

### <a name="implemented-prepared-statement-metadata-caching"></a>Implémentation de la mise en cache de métadonnées de l’instruction préparée

Le pilote JDBC a implémenté la mise en cache de métadonnées instruction préparée pour améliorer les performances. Le pilote prend désormais en charge la mise en cache des métadonnées d’instruction préparée dans le pilote avec `disableStatementPooling` et `statementPoolingCacheSize` propriétés de connexion. Cette fonctionnalité est désactivée par défaut. Pour plus d’informations, consultez [préparé instruction mise en cache de métadonnées pour le pilote JDBC](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md).

### <a name="added-support-for-azure-ad-integrated-authentication-on-linuxmac"></a>Prise en charge pour Azure AD l’authentification intégrée sur Linux/Mac

Le pilote JDBC prend maintenant en charge l’authentification intégrée Azure Active Directory (Azure AD) sur tous les systèmes d’exploitation pris en charge (Windows, Linux et Mac) avec Kerberos. Vous pouvez également sur les systèmes d’exploitation Windows, les utilisateurs peuvent s’authentifier avec sqljdbc_auth.dll.

### <a name="updated-microsoft-azure-active-directory-authentication-library-adal4j-for-java-version-140"></a>Mise à jour de la « bibliothèque d’authentification Microsoft Azure Active Directory (ADAL4J) pour Java » : version 1.4.0

Le pilote JDBC a mis à jour sa dépendance Maven sur « Microsoft Azure Active Directory Authentication Library (ADAL4J) pour Java » vers la version 1.4.0. Pour plus d’informations sur les dépendances, consultez [dépendances de fonctionnalité de Microsoft JDBC Driver pour SQL Server](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md).

## <a name="updates-in-microsoft-jdbc-driver-62-for-sql-server"></a>Mises à jour apportées à Microsoft JDBC Driver 6.2 pour SQL Server

Microsoft JDBC Driver 6.2 pour SQL Server est entièrement conforme aux spécifications de JDBC 4.1 et 4.2. Les fichiers JAR dans le package 6.2 sont nommées en fonction de la compatibilité des versions de Java. Par exemple, le fichier mssql-jdbc-6.2.2.jre8.jar à partir du package 6.2 est recommandé pour une utilisation avec Java 8.

> [!NOTE]  
> Un problème avec l’amélioration de la mise en cache de métadonnées a été trouvé dans la RTW 6.2 JDBC a publié le 29 juin 2017. L’amélioration a été restaurée et les nouveaux fichiers JAR (version 6.2.1) ont été publiés à partir du 17 juillet 2017. 
>
> Une autre amélioration mis à niveau la version de bibliothèque dépendante d’Azure Key Vault à 1.0.0 et les nouveaux fichiers JAR (version 6.2.2) ont été publiés sur le 19 octobre 2017.
>
> Téléchargez les dernières mises à jour pour JDBC Driver 6.2 à partir de [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=852460), [GitHub](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.2), et [Maven Central](https://search.maven.org/#search%7Cgav%7C1%7Cg%3A%22com.microsoft.sqlserver%22%20AND%20a%3A%22mssql-jdbc%22). Mettez à jour vos projets pour utiliser le 6.2.2 libérer les fichiers JAR. Pour plus d’informations, voir les notes de version pour [6.2.1](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.1) et [6.2.2](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.2).

### <a name="azure-ad-support-for-linux"></a>Prise en charge de Azure AD pour Linux

Se connecter à vos applications Linux vers Azure SQL Database à l’aide de l’authentification Azure AD via les méthodes jeton d’accès et nom d’utilisateur/mot de passe.

### <a name="fips-enabled-jvms"></a>JVM FIPS activé

Le pilote JDBC est désormais utilisable sur les machines virtuelles Java qui s’exécutent en mode de compatibilité 140 FIPS Federal Information Processing Standard () pour répondre aux normes fédérales sur la conformité.

### <a name="kerberos-authentication-improvements"></a>Améliorations de l’authentification Kerberos

Le pilote JDBC prend désormais en charge pour :

- Méthode principal/mot de passe pour les applications où la configuration de Kerberos ne peut pas être modifiée ou Impossible de récupérer un nouveau jeton ou un fichier keytab. Cette méthode peut être utilisée pour l’authentification auprès d’une instance de SQL Server qui autorise uniquement l’authentification Kerberos.
- Authentification inter-domaines qui utilise l’authentification intégrée Kerberos sans définir explicitement le SPN du serveur. Maintenant le pilote calcule automatiquement le domaine même lorsqu’elle n’est pas fournie.
- La délégation contrainte Kerberos en acceptant empruntée des informations d’identification de l’utilisateur en tant qu’objet d’informations d’identification GSS via la source de données. Ces informations d’identification avec emprunt d’identité sont ensuite utilisée pour établir une connexion Kerberos.

### <a name="added-timeouts"></a>Ajout de délais d’attente

Le pilote JDBC prend désormais en charge les délais d’expiration configurables suivantes. Vous pouvez les modifier selon les besoins de votre application.

- Contrôler le nombre de secondes à attendre avant un délai d’expiration du délai de requête se produit lorsque vous exécutez une requête.
- Délai d’expiration de socket pour spécifier le nombre de millisecondes à attendre avant un délai d’expiration se produit sur un socket de lecture ou accepte.

## <a name="updates-in-microsoft-jdbc-driver-61-for-sql-server"></a>Mises à jour apportées à Microsoft JDBC Driver 6.1 pour SQL Server

Microsoft JDBC Driver 6.1 pour SQL Server est entièrement conforme aux spécifications de JDBC 4.1 et 4.2. Il s’agit de la version open source initiale du pilote JDBC. Il contient les fichiers mssql-jdbc-6.1.0.jre8.jar et mssql-jdbc-6.1.0.jre7.jar, qui correspondent à la compatibilité de version de Java.

## <a name="updates-in-microsoft-jdbc-driver-60-for-sql-server"></a>Mises à jour apportées à Microsoft JDBC Driver 6.0 pour SQL Server

Le pilote Microsoft JDBC 6.0 pour SQL Server est entièrement conforme aux spécifications de JDBC 4.1 et 4.2. Les fichiers JAR dans le package 6.0 sont nommées en fonction de leur conformité avec la version de l’API JDBC. Par exemple, le fichier sqljdbc42.jar à partir du package 6.0 est API compatible avec JDBC 4.2. De même, le fichier sqljdbc41.jar est conforme avec l’API JDBC 4.1.

Pour vous assurer d’avoir le droit sqljdbc42.jar ou le fichier de sqljdbc41.jar, exécutez les lignes de code suivantes. Si la sortie est « version du pilote : 6.0.7507.100 », vous disposez du package de pilote JDBC 6.0.

```java
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```

### <a name="always-encrypted"></a>Always Encrypted

Le pilote prend en charge la fonctionnalité Always Encrypted dans SQL Server 2016. Cette fonctionnalité garantit que les données sensibles ne soient jamais affichées en texte brut dans une instance de SQL Server. Always Encrypted chiffre les données de l’application de manière transparente, de sorte que SQL Server manipule uniquement les données chiffrées, et non des valeurs en texte clair. Même si l’instance SQL Server ou l’ordinateur hôte est compromis, la personne malveillante ne pourra récupérer qu’un texte chiffré des données sensibles. Pour plus d’informations, voir [Utiliser Always Encrypted avec le pilote JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).

### <a name="internationalized-domain-names"></a>Noms de domaine internationaux

Le pilote prend en charge les noms de domaines internationaux (IDN) pour les noms de serveur. Pour plus d’informations, consultez « À l’aide des noms de domaines internationaux » dans le [fonctionnalités internationales du pilote JDBC](../../connect/jdbc/international-features-of-the-jdbc-driver.md) article.

### <a name="parameterized-queries"></a>Requêtes paramétrables

Le pilote prend maintenant en charge la récupération des métadonnées de paramètres avec des instructions préparées pour les requêtes complexes, comme les sous-requêtes et/ou les jointures. Notez que cette amélioration est disponible uniquement quand vous utilisez SQL Server 2012 et des versions plus récentes.

### <a name="azure-active-directory"></a>Azure Active Directory

Authentification Azure AD est un mécanisme de connexion à Azure SQL Database v12 à l’aide d’identités dans Azure AD. Utilisez l’authentification Azure AD pour gérer de manière centralisée les identités des utilisateurs de base de données et comme alternative à l’authentification SQL Server. 

Vous pouvez utiliser le pilote JDBC 6.0 pour spécifier vos informations d’identification Azure AD dans la chaîne de connexion JDBC pour se connecter à la base de données SQL Azure. Pour plus d’informations, consultez la propriété de l’authentification dans le [définissant les propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md) article.

### <a name="table-valued-parameters"></a>Paramètres table

Les paramètres table (TVP) fournissent un moyen simple de marshaler plusieurs lignes de données d’une application cliente vers SQL Server sans avoir recours à plusieurs allers-retours ou à une logique spéciale côté serveur pour traiter les données. Vous pouvez utiliser des TVP pour encapsuler des lignes de données dans une application cliente et envoyer les données au serveur dans une commande paramétrable unique. Les lignes de données entrantes sont stockées dans une variable de table, vous pouvez ensuite utiliser à l’aide de Transact-SQL. Pour plus d’informations, consultez [à l’aide des paramètres table](../../connect/jdbc/using-table-valued-parameters.md).

### <a name="always-on-availability-groups"></a>Groupes de disponibilité Always On

Le pilote prend désormais en charge les connexions transparentes aux groupes de disponibilité AlwaysOn. Le pilote détecte rapidement la topologie Always On actuelle de votre infrastructure serveur et se connecte au serveur actif de manière transparente.

## <a name="updates-in-microsoft-jdbc-driver-42-for-sql-server-and-later"></a>Mises à jour apportées à Microsoft JDBC Driver 4.2 pour SQL Server et versions ultérieures

Microsoft JDBC Driver 4.2 pour SQL Server est entièrement conforme aux spécifications de JDBC 4.1 et 4.2. Les fichiers JAR dans le package 4.2 sont nommées en fonction de leur conformité avec la version de l’API JDBC. Par exemple, le fichier sqljdbc42.jar à partir du package 4.2 est API compatible avec JDBC 4.2. De même, le fichier sqljdbc41.jar est conforme avec l’API JDBC 4.1.

Pour vous assurer, vous avez le droit sqljdbc42.jar ou un fichier sqljdbc41.jar, exécutez les lignes de code suivantes. Si la sortie est « version du pilote : 4.2.6420.100 », vous disposez du package de pilote JDBC 4.2.

```java
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```

### <a name="support-for-jdk-8"></a>Prise en charge de JDK 8

Le pilote prend en charge la version 8.0 en plus de JDK 7.0, 6.0 et 5.0 de JDK.

### <a name="jdbc-41-and-42-compliance"></a>Compatible avec JDBC 4.1 et 4.2

Le pilote prend en charge les spécifications de l’API Java Database Connectivity 4.1 et 4.2, en plus de la version 4.0. Pour plus d’informations, consultez [compatibilité avec JDBC 4.1 pour le pilote JDBC](../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md) et [compatibilité avec JDBC 4.2 pour le pilote JDBC](../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md).

### <a name="bulk-copy"></a>Copie en bloc

Vous utilisez la fonctionnalité de copie en bloc pour copier rapidement de grandes quantités de données dans des tables ou des vues de bases de données SQL Server. Pour plus d’informations, consultez [Utilisation de la copie en bloc avec le pilote JDBC](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md).

### <a name="xa-transaction-rollback-option"></a>Option de restauration des transactions XA

Le pilote dispose de nouvelles options de délai d’attente pour la restauration automatique existante de transactions non préparées. Pour plus d’informations, consultez [des transactions XA de présentation](../../connect/jdbc/understanding-xa-transactions.md).

### <a name="new-kerberos-principal-connection-property"></a>Nouvelle propriété de connexion principale Kerberos

Le pilote utilise une nouvelle propriété de connexion pour faciliter la flexibilité avec les connexions Kerberos. Pour plus d’informations, consultez [Utilisation de l’authentification intégrée Kerberos pour se connecter à SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md).

## <a name="updates-in-microsoft-jdbc-driver-41-for-sql-server-and-later"></a>Mises à jour apportées à Microsoft JDBC Driver 4.1 pour SQL Server et versions ultérieures

### <a name="support-for-jdk-7"></a>Prise en charge de JDK 7

Le pilote prend en charge la version 7.0, en plus de JDK 6.0 et 5.0 de JDK.

## <a name="itanium-not-supported-for-jdbc-driver-64-60-42-and-41-applications"></a>Itanium non pris en charge pour les applications JDBC Driver 6.4, 6.0, 4.2 et 4.1

L’exécution d’applications Microsoft JDBC Driver 6.4, 6.0, 4.2 et 4.1 pour SQL Server n’est pas prise en charge sur un ordinateur Itanium.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)

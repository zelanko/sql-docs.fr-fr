---
title: Notes de publication pour le pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 074f211e-984a-4b76-bb15-ee36f5946f12
caps.latest.revision: 206
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 10f14eedb1a74f74cb1ee055a247a96671224ce0
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39662461"
---
# <a name="release-notes-for-the-jdbc-driver"></a>Notes de publication pour le pilote JDBC

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

## <a name="updates-in-microsoft-jdbc-driver-70-for-sql-server"></a>Mises à jour apportées à Microsoft JDBC Driver 7.0 pour SQL Server

Microsoft JDBC Driver 7.0 pour SQL Server est entièrement conforme à la spécification de l’API JDBC 4.2. Les fichiers JAR dans le package 7.0 sont nommées en fonction de la compatibilité des versions de Java. Par exemple, le fichier mssql-jdbc-7.0.0.jre10.jar à partir du package 7.0 doit être utilisé avec Java 10.

### <a name="support-for-jdk-10"></a>Prise en charge de JDK 10

Microsoft JDBC Driver 7.0 pour SQL Server est désormais compatible avec Java Development Kit (JDK) version 10.0, en plus de JDK 1.8. Cette mise à jour expose également du pilote 'automatique-Module-Name' en tant que `com.microsoft.sqlserver.jdbc` via son fichier de manifeste.

### <a name="support-for-spatial-datatypes"></a>Prise en charge des types de données spatiaux

Microsoft JDBC Driver 7.0 pour SQL Server prend désormais en charge SQL Server Datatypes Spatial 'Geography' et « Geometry ». Pour plus d’informations sur les types de données spatiales API et comment les utiliser, consultez [ici](../../connect/jdbc/use-spatial-datatypes.md).

### <a name="implementation-for-jdbc-43-introduced-javasqlconnection-apis-beginrequest-and-endrequest"></a>Implémentation des API java.sql.Connection beginRequest() et endRequest() introduites dans JDBC 4.3

Microsoft JDBC Driver 7.0 pour SQL Server maintenant implémente `beginRequest()` et `endRequest()` API à partir de `java.sql.Connection` classe. Ces API ont été introduites avec JDBC 4.3 spécifications et JDK 9. Pour plus d’informations sur l’implémentation du pilote de ces API, consultez [ici](../../connect/jdbc/jdbc-4-3-compliance-for-the-jdbc-driver.md).

### <a name="support-for-sql-data-discovery-and-classification"></a>Prise en charge de la découverte et classification des données SQL

Microsoft JDBC Driver 7.0 pour SQL Server prend en charge de la fonctionnalité de découverte de données SQL et à la classification avec une base de données cible qui prend en charge cette fonctionnalité. Le pilote expose désormais `SQLServerResultSet.getSensitivityClassification()` API pour extraire ces informations à partir du jeu de résultats d’extraction.

Pour plus d’informations sur la façon d’utiliser cette fonctionnalité avec le pilote JDBC, consultez l’exemple [ici](../../connect/jdbc/data-discovery-classification-sample.md).

### <a name="added-new-connection-property-usebulkcopyforbatchinsert"></a>Ajouté la nouvelle propriété de connexion : useBulkCopyForBatchInsert

Microsoft JDBC Driver 7.0 pour SQL Server introduit une nouvelle propriété de connexion, « useBulkCopyForBatchInsert », qui est uniquement pris en charge pour **Azure Data Warehouse**.

Cette propriété est **désactivé** par défaut et peut être activée pour améliorer les performances des applications de l’utilisateur en exécutant un push volumineux confère des données dans Azure Data Warehouse. L’activation de cette propriété modifie le comportement des opérations d’insertion de lot pour basculer vers les opérations de copie en bloc avec les données de fournie par l’utilisateur. Pour plus d’informations sur cette propriété et ses limitations, consultez [ici](../../connect/jdbc/use-bulk-copy-api-batch-insert-operation.md).

### <a name="added-new-connection-property-cancelquerytimeout"></a>Ajouté la nouvelle propriété de connexion : cancelQueryTimeout

Microsoft JDBC Driver 7.0 pour SQL Server introduit la nouvelle propriété de connexion, `cancelQueryTimeout`, pour annuler `queryTimeout` sur `java.sql.Connection` et `java.sql.Statement` objets.

### <a name="added-azure-key-vault-provider-constructors"></a>Constructeurs de fournisseur Ajout Azure Key Vault

Microsoft JDBC Driver 7.0 pour SQL Server réintroduit un constructeur précédemment supprimé, pour `SQLServerColumnEncryptionAzureKeyVaultProvider`, authentification autorisée à l’aide d’une méthode personnalisée est implémentée via `SQLServerKeyVaultAuthenticationCallback` pour extraire un jeton d’accès.

Les nouveaux constructeurs ont le ci-dessous définition :

```java
/* This constructor is added to provide backwards compatibility with 6.0
* version of the driver. It is marked deprecated for removal in next
* stable release.
*/
@Deprecated
public SQLServerColumnEncryptionAzureKeyVaultProvider(
        SQLServerKeyVaultAuthenticationCallback authenticationCallback,
        ExecutorService executorService) throws SQLServerException;

/*New Constructor to replace the above constructor*/
public SQLServerColumnEncryptionAzureKeyVaultProvider(
            SQLServerKeyVaultAuthenticationCallback authenticationCallback) throws SQLServerException;
```

### <a name="updated-adal4j-version-to-160"></a>Version ADAL4J mise à jour vers la version 1.6.0

Microsoft JDBC Driver 7.0 pour SQL Server a mis à jour sa dépendance maven sur azure-activedirectory-library-for-java (ADAL4J) vers la version 1.6.0. Pour plus d'informations sur les dépendances, cliquez [ici](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md).

## <a name="updates-in-microsoft-jdbc-driver-64-for-sql-server"></a>Mises à jour apportées à Microsoft JDBC Driver 6.4 pour SQL Server

Microsoft JDBC Driver 6.4 pour SQL Server est entièrement conforme aux spécifications de JDBC 4.1 et 4.2. Les fichiers JAR dans le package de 6,4 sont nommées en fonction de la compatibilité des versions de Java. Par exemple, le fichier mssql-jdbc-6.4.0.jre8.jar à partir du package 6,4 doit être utilisé avec Java 8.

### <a name="support-for-jdk-9"></a>Prise en charge de JDK 9

Prise en charge de Java Development Kit (JDK) version 9.0, en plus des versions 8.0 et 7.0 de JDK.

### <a name="jdbc-43-compliance"></a>Conformité JDBC 4.3

Prise en charge des spécifications de l’API Java Database Connectivity 4.3, en plus des versions 4.2 et 4.1. Les méthodes de l’API JDBC 4.3 sont ajoutés, mais pas encore implémentés. Pour plus d’informations, voir [Conformité à JDBC 4.3 pour le pilote JDBC](../../connect/jdbc/jdbc-4-3-compliance-for-the-jdbc-driver.md).

### <a name="added-new-connection-property-sslprotocol"></a>Ajouté la nouvelle propriété de connexion : sslProtocol

Ajouter une nouvelle propriété de connexion qui permet aux utilisateurs de spécifier le mot de clé du protocole TLS. Les valeurs possibles sont : « TLS », « TLSv1 », « TLSv1.1 », « TLSv1.2 ». Consultez [SSLProtocol](https://github.com/Microsoft/mssql-jdbc/wiki/SSLProtocol) pour plus d’informations.

### <a name="deprecated-connection-property-fipsprovider"></a>Propriété de connexion déconseillée : fipsProvider

Propriété de connexion « fipsProvider » est supprimée de la liste des propriétés de connexion acceptée. Afficher les détails [ici](https://github.com/Microsoft/mssql-jdbc/pull/460).

### <a name="added-connection-properties-for-specifying-custom-trustmanager"></a>Propriétés de connexion ajouté pour la spécification du TrustManager personnalisé

Pilote prend désormais en charge la spécification du TrustManager personnalisé avec l’ajout de « trustManagerClass » et « trustManagerConstructorArg » les propriétés de connexion. Cela permet la spécification dynamique d’un ensemble de certificats approuvés sur un niveau de la connexion sans modifier les paramètres globaux pour l’environnement de machine virtuelle Java.

### <a name="added-support-for-datetimesmalldatetime-in-table-valued-parameters-tvp"></a>Prise en charge pour datetime/smallDatetime dans les paramètres table (TVP)

Le pilote prend désormais en charge les types de données DATETIME et SMALLDATETIME lors de l’utilisation de paramètres table.

### <a name="added-support-for-sqlvariant-datatype"></a>Prise en charge pour le type de données sql_variant

Le pilote JDBC prend désormais en charge les types de données sql_variant à utiliser avec SQL Server. Sql_variant est également prise en charge des fonctionnalités telles que les paramètres table (TVP) et BulkCopy avec ci-dessous limitations :

1. Pour les valeurs de Date : lorsque vous utilisez TVP pour remplir une table qui contient les valeurs datetime/smalldatetime/date stockées dans la colonne sql_variant, appel de méthodes de getDateTime()/getSmallDateTime()/getDate() sur le jeu de résultats ne fonctionne pas et lève l’exception suivante :  `java java.lang.String cannot be cast to java.sql.Timestamp` Solution de contournement : utilisez les méthodes « getString() » ou « getObject() » à la place.

2. Utilisation de paramètres table avec SQL Variant pour les valeurs null

Si vous utilisez TVP pour remplir une table et d’envoyer la valeur NULL à la colonne de type sql_variant, vous rencontrerez une exception comme l’insertion de valeur NULL avec une colonne de type sql_variant dans TVP n’est actuellement pas pris en charge.

### <a name="implemented-prepared-statement-metadata-caching"></a>Implémentation d’instruction préparée la mise en cache des métadonnées

Le pilote JDBC a implémenté les métadonnées instruction préparée mise en cache pour améliorer les performances. Pilote prend désormais en charge la mise en cache des métadonnées de l’instruction préparée dans le pilote avec les propriétés de connexion « disableStatementPooling » et « regroupement d’instructions ». Cette fonctionnalité est désactivée par défaut. Vous trouverez plus d’informations [ici](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md).

### <a name="added-support-for-aad-integrated-authentication-on-linuxmac"></a>Prise en charge pour l’authentification intégrée de AAD sur Linux/Mac

Le pilote JDBC prend aussi en charge l’authentification intégrée Azure Active Directory sur tous les systèmes d’exploitation pris en charge (Windows/Linux/Mac) avec Kerberos. Vous pouvez également sur les systèmes d’exploitation Windows, les utilisateurs peuvent s’authentifier avec sqljdbc_auth.dll.

### <a name="updated-adal4j-version-to-140"></a>ADAL4J version mise à jour 1.4.0

Le pilote JDBC a mis à jour sa dépendance maven sur azure-activedirectory-library-for-java (ADAL4J) vers la version 1.4.0. Pour plus d'informations sur les dépendances, cliquez [ici](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md).

## <a name="updates-in-microsoft-jdbc-driver-62-for-sql-server"></a>Mises à jour apportées à Microsoft JDBC Driver 6.2 pour SQL Server

Microsoft JDBC Driver 6.2 pour SQL Server est entièrement conforme aux spécifications de JDBC 4.1 et 4.2. Les fichiers JAR dans le package 6.2 sont nommées en fonction de la compatibilité des versions de Java. Par exemple, le fichier mssql-jdbc-6.2.2.jre8.jar à partir du package 6.2 est recommandé à utiliser avec Java 8.

> [!NOTE]  
> Un problème avec l’amélioration de la mise en cache de métadonnées a été trouvé dans la RTW 6.2 JDBC a publié le 29 juin 2017. L’amélioration a été restaurée et les nouveaux fichiers JAR (version 6.2.1) ont été publiés à partir du 17 juillet 2017. 
>
> Une autre amélioration pour mettre à niveau la version de bibliothèque dépendante d’Azure Key Vault à 1.0.0 a eu lieu, et les nouveaux fichiers JAR (version 6.2.2) ont été publiés sur le 19 octobre 2017.
>
> Télécharger les dernières mises à jour dans JDBC Driver 6.2 sur [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=852460), [GitHub](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.2), et [Maven Central](http://search.maven.org/#search%7Cgav%7C1%7Cg%3A%22com.microsoft.sqlserver%22%20AND%20a%3A%22mssql-jdbc%22). Mettez à jour vos projets pour utiliser le 6.2.2 libérer les fichiers JAR. Veuillez consulter les notes pour [v6.2.1](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.1) et [v6.2.2](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.2) pour plus d’informations.

### <a name="azure-active-directory-aad-support-for-linux"></a>Prise en charge de Azure Active Directory (AAD) pour Linux

Connectez vos applications Linux vers Azure SQL Database à l’aide de l’authentification AAD via les méthodes jeton d’accès et nom d’utilisateur/mot de passe.

### <a name="federal-information-processing-standard-fips-enabled-jvms"></a>Federal FIPS Information Processing Standard () activé JVM

Le pilote JDBC est désormais utilisable sur les machines virtuelles Java qui s’exécutent en mode de conformité FIPS 140 pour répondre aux normes fédérales et conformité.

### <a name="kerberos-authentication-improvements"></a>Améliorations de l’authentification Kerberos

Le pilote JDBC prend désormais en charge pour :

- Méthode principal/mot de passe pour les applications où la configuration de Kerberos ne peut pas être modifié ou Impossible de récupérer un nouveau jeton ou un fichier keytab. Cette méthode peut être utilisée pour l’authentification auprès d’un serveur SQL Server qui autorise uniquement l’authentification Kerberos.
- Authentification inter-domaines à l’aide de l’authentification Kerberos intégrée sans définir explicitement le SPN du serveur. Maintenant le pilote calcule automatiquement le domaine même lorsqu’elle n’a pas été fournie.
- La délégation contrainte Kerberos en acceptant empruntée des informations d’identification de l’utilisateur en tant qu’informations d’identification GSS objet par le biais de source de données. Ces informations d’identification avec emprunt d’identité sont ensuite utilisée pour établir une connexion Kerberos.

### <a name="added-timeouts"></a>Ajout de délais d’attente

Le pilote JDBC prend désormais en charge le configurable délais d’attente suivants que vous pouvez modifier selon les besoins de votre application :

- Contrôler le nombre de secondes à attendre avant un délai d’expiration du délai de requête se produit lors de l’exécution d’une requête.
- Délai d’expiration de socket pour spécifier le nombre de millisecondes à attendre avant un délai d’expiration se produit sur un socket de lecture ou accepte.

## <a name="updates-in-microsoft-jdbc-driver-61-for-sql-server"></a>Mises à jour apportées à Microsoft JDBC Driver 6.1 pour SQL Server

La version 6.1 de Microsoft JDBC Driver pour SQL Server est entièrement conforme aux spécifications de JDBC 4.1 et 4.2. Ceci est la version open source initiale du pilote JDBC et contient les fichiers de mssql-jdbc-6.1.0.jre7.jar mssql-jdbc-6.1.0.jre8.jar, qui correspondent à la compatibilité de version de Java.

## <a name="updates-in-microsoft-jdbc-driver-60-for-sql-server"></a>Mises à jour apportées à Microsoft JDBC Driver 6.0 pour SQL Server

Le pilote Microsoft JDBC 6.0 pour SQL Server est entièrement conforme aux spécifications de JDBC 4.1 et 4.2. Les fichiers JAR dans le package 6.0 sont nommées en fonction de leur conformité avec la version de l’API JDBC. Par exemple, le fichier sqljdbc42.jar à partir du package 6.0 est API compatible avec JDBC 4.2. De même, le fichier sqljdbc41.jar est conforme avec l’API JDBC 4.1.

Pour garantir que vous avez le droit sqljdbc42.jar ou sqljdbc41.jar, exécutez les lignes de code suivantes. Si la sortie est « version du pilote : 6.0.7507.100 », vous disposez du package de pilote JDBC 6.0.

```java
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```

### <a name="always-encrypted"></a>Always Encrypted

Prise en charge de la fonctionnalité récemment publiée Always Encrypted dans SQL Server 2016, une nouvelle fonctionnalité de sécurité qui veille à ce que les donnés sensibles ne soient jamais affichées en texte clair dans une instance de SQL Server. Always Encrypted chiffre les données de l’application par transparence, de sorte que SQL Server manipule uniquement les données chiffrées, et non des valeurs en texte clair. Même si l’instance SQL ou l’ordinateur hôte est compromis, la personne malveillante ne pourra récupérer qu’un texte chiffré des données sensibles. Pour plus d’informations, voir [Utiliser Always Encrypted avec le pilote JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).

### <a name="internationalized-domain-name-idn"></a>Noms de domaine internationaux

Prise en charge des noms de domaine internationaux pour les noms de serveur. Pour plus d’informations, consultez à l’aide des noms de domaines internationaux sur le [fonctionnalités internationales du pilote JDBC](../../connect/jdbc/international-features-of-the-jdbc-driver.md) page.

### <a name="parameterized-query"></a>Requête paramétrée

Prise en charge de la récupération des métadonnées de paramètres avec des instructions préparées pour les requêtes complexes, comme les sous-requêtes et les jointures. Notez que cette amélioration est disponible uniquement lorsque vous utilisez SQL Server 2012 et les versions plus récentes.

### <a name="azure-active-directory-aad"></a>Azure Active Directory (AAD)

L’authentification AAD est un mécanisme de connexion à Azure SQL Database v12 à l’aide d’identités dans AAD. Utilisez l’authentification AAD pour gérer de manière centralisée les identités des utilisateurs de base de données et comme alternative à l’authentification SQL Server. Le pilote JDBC 6.0 vous permet de spécifier vos informations d’identification dans la chaîne de connexion JDBC pour vous connecter à Azure SQL Database. Pour plus d’informations, consultez la propriété de l’authentification sur le [définissant les propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md) page.

### <a name="table-valued-parameters"></a>Paramètres table

Les paramètres table fournissent un moyen simple de marshaler plusieurs lignes de données d’une application cliente vers SQL Server sans avoir recours à plusieurs allers-retours ou à une logique spéciale côté serveur pour traiter les données. Vous pouvez utiliser des paramètres table pour encapsuler des lignes de données dans une application cliente et envoyer les données au serveur dans une commande paramétrable unique. Les lignes de données entrantes sont stockées dans une variable de table qui peut ensuite être traitée à l’aide de Transact-SQL. Pour plus d’informations, consultez [Using Table-Valued paramètres](../../connect/jdbc/using-table-valued-parameters.md).

### <a name="alwayson-availability-groups-ag"></a>Groupes de disponibilité AlwaysOn

Le pilote prend désormais en charge les connexions transparentes aux groupes de disponibilité AlwaysOn. Le pilote détecte rapidement la topologie AlwaysOn actuelle de votre infrastructure serveur et se connecte au serveur actif en toute transparence.

## <a name="updates-in-microsoft-jdbc-driver-42-for-sql-server-and-later"></a>Mises à jour apportées à Microsoft JDBC Driver 4.2 pour SQL Server et versions ultérieures

Microsoft JDBC Driver 4.2 pour SQL Server est entièrement conforme aux spécifications de JDBC 4.1 et 4.2. Les fichiers JAR dans le package 4.2 sont nommées en fonction de leur conformité avec la version de l’API JDBC. Par exemple, le fichier sqljdbc42.jar à partir du package 4.2 est API compatible avec JDBC 4.2. De même, le fichier sqljdbc41.jar est conforme avec l’API JDBC 4.1.

Pour garantir que vous avez le droit sqljdbc42.jar ou sqljdbc41.jar, exécutez les lignes de code suivantes. Si la sortie est « version du pilote : 4.2.6420.100 », vous disposez du package de pilote JDBC 4.2.

```java
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```

### <a name="support-for-jdk-8"></a>Prise en charge de JDK 8

Prise en charge de Java Development Kit (JDK) version 8.0 en plus de JDK 7.0, 6.0 et 5.0.

### <a name="jdbc-41-and-42-compliance"></a>Compatible avec JDBC 4.1 et 4.2

Prise en charge des spécifications de l'API Java Database Connectivity 4.1 et 4.2, en plus de la version 4.0. Pour plus d’informations, consultez [conformité JDBC 4.1 pour le pilote JDBC](../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md) et [JDBC 4.2 conformité pour le pilote JDBC](../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md).

### <a name="bulk-copy"></a>Copie en bloc

La fonctionnalité de copie en bloc est utilisée pour copier rapidement de grandes quantités de données dans des tables ou des vues de bases de données SQL Server. Pour plus d’informations, voir [Utiliser la copie en bloc avec le pilote JDBC](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md).

### <a name="xa-transaction-rollback-option"></a>Option de restauration des transactions XA

Ajout de nouvelles options de délai d'attente pour la restauration automatique existante des transactions non préparées. Pour plus d’informations, consultez [présentation des Transactions XA](../../connect/jdbc/understanding-xa-transactions.md).

### <a name="new-kerberos-principal-connection-property"></a>Nouvelle propriété de connexion principale Kerberos

Ajout d'une nouvelle propriété de connexion pour faciliter la flexibilité avec les connexions Kerberos. Pour plus d’informations, voir [Utiliser l’authentification intégrée Kerberos pour se connecter à SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md).

## <a name="updates-in-microsoft-jdbc-driver-41-for-sql-server-and-later"></a>Mises à jour apportées à Microsoft JDBC Driver 4.1 pour SQL Server et versions ultérieures

### <a name="support-for-jdk-7"></a>Prise en charge de JDK 7

Prise en charge de Java Development Kit (JDK) version 7.0, en plus des versions 6.0 et 5.0 de JDK.

## <a name="itanium-not-supported-for-jdbc-driver-64-60-42-and-41-applications"></a>Itanium non pris en charge pour les applications JDBC Driver 6.4, 6.0, 4.2 et 4.1

L’exécution d’applications Microsoft JDBC Driver 6.4, 6.0, 4.2 et 4.1 pour SQL Server n’est pas prise en charge sur un ordinateur Itanium.

## <a name="see-also"></a> Voir aussi

[Vue d’ensemble du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)

---
title: Utilisation d’Always Encrypted avec le pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 271c0438-8af1-45e5-b96a-4b1cabe32707
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6ce122713ce5d57daa9a7313d8b6d184bd33b850
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47842747"
---
# <a name="using-always-encrypted-with-the-jdbc-driver"></a>Utilisation d’Always Encrypted avec le pilote JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Cette page fournit des informations sur la façon de développer des applications Java à l’aide de [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md) et le pilote Microsoft JDBC 6.0 (ou version ultérieure) pour SQL Server.

Always Encrypted permet aux clients de chiffrer des données sensibles et de ne jamais révéler les données ou les clés de chiffrement à SQL Server ou Azure SQL Database. À cette fin, un pilote compatible avec Always Encrypted, comme Microsoft JDBC Driver 6.0 (ou version ultérieure) pour SQL Server, chiffre et déchiffre de manière transparente les données sensibles dans l’application cliente. Le pilote détermine automatiquement quelle requête paramètres correspondent aux colonnes de base de données Always Encrypted et chiffre les valeurs de ces paramètres avant de les envoyer à SQL Server ou de la base de données SQL Azure. De même, il déchiffre de manière transparente les données récupérées dans les colonnes de base de données chiffrées, qui figurent dans les résultats de la requête. Pour plus d’informations, consultez [Always Encrypted (moteur de base de données)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) et [toujours chiffré référence des API pour le pilote JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).

## <a name="prerequisites"></a>Conditions préalables requises
- Assurez-vous que Microsoft JDBC Driver 6.0 (ou version ultérieure) pour SQL Server est installé sur votre ordinateur de développement. 
- Téléchargez et installez les fichiers de stratégie Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction.  Veillez à lire le fichier Lisez-moi inclus dans le fichier zip pour obtenir les instructions d’installation et des informations pertinentes sur les éventuels problèmes d’importation/exportation.  

    - Si vous utilisez mssql-jdbc-X.X.X.jre7.jar ou sqljdbc41.jar, vous pouvez télécharger les fichiers de stratégie à partir du site web [Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files 7 Download](http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html).

    - Si vous utilisez mssql-jdbc-X.X.X.jre8.jar ou sqljdbc42.jar, vous pouvez télécharger les fichiers de stratégie à partir du site web [Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files 8 Download](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html).

    - Si vous utilisez le mssql-jdbc-X.X.X.jre9.jar, aucun fichier de stratégie ne doit être téléchargé. La stratégie de compétence dans Java 9 est un nombre illimité de niveau de chiffrement par défaut.

## <a name="working-with-column-master-key-stores"></a>Utilisation de magasins de clés principales de colonne
Pour chiffrer ou déchiffrer des données pour les colonnes chiffrées, SQL Server gère les clés de chiffrement de colonne. Les clés de chiffrement de colonne sont stockées sous forme chiffrée dans les métadonnées de la base de données. Chaque clé de chiffrement de colonne a une clé principale de colonne correspondante qui sert à chiffrer la clé de chiffrement de colonne. Les métadonnées de base de données ne contient pas les clés principales de colonne. Ces clés sont conservées uniquement par le client. Toutefois les métadonnées de base de données contient plus d’informations sur l’emplacement des clés principales de la colonne relative au client. Par exemple, les métadonnées de base de données peuvent dire que le magasin de clés contenant une clé principale de colonne est le Store de certificat de Windows et le certificat spécifique utilisé pour chiffrer et déchiffrer se trouve à un emplacement spécifique dans le Store de certificat de Windows. Si le client a accès à ce certificat dans le Store de certificat Windows, il peut obtenir le certificat. Le certificat peut ensuite être utilisé pour déchiffrer la clé de chiffrement de colonne. Cette clé de chiffrement peut être utilisé pour déchiffrer ou de chiffrer les données pour les colonnes chiffrées qui utilisent cette clé de chiffrement de colonne.

Microsoft JDBC Driver for SQL Server communique avec un magasin de clés à l’aide d’un fournisseur de magasin de clés principales de colonne, qui est une instance d’une classe dérivé de **SQLServerColumnEncryptionKeyStoreProvider**.

### <a name="using-built-in-column-master-key-store-providers"></a>Utilisation des fournisseurs de magasin de clés principales de colonne intégrés
Microsoft JDBC Driver for SQL Server est fourni avec les fournisseurs de magasin de clé principale de la colonne intégrés suivants. Certains de ces fournisseurs sont pré-enregistré avec les noms des fournisseurs spécifiques (utilisées pour rechercher le fournisseur) en fonction des informations d’identification supplémentaires ou de l’inscription explicite.

| Classe                                                 | Description                                        | Nom de fournisseur (pour la recherche)  | Est déjà inscrit ? |
| :---------------------------------------------------- | :------------------------------------------------- | :---------------------- | :----------------- |
| **SQLServerColumnEncryptionAzureKeyVaultProvider**    | Un fournisseur pour un magasin de clés Azure Key Vault. | AZURE_KEY_VAULT         | non                 |
| **SQLServerColumnEncryptionCertificateStoreProvider** | Fournisseur du magasin de certificats Windows.      | MSSQL_CERTIFICATE_STORE | Oui                |
| **SQLServerColumnEncryptionJavaKeyStoreProvider**     | Un fournisseur pour le magasin de clés Java                   | MSSQL_JAVA_KEYSTORE     | Oui                |

Pour les fournisseurs de magasin de clés préalablement inscrit, vous n’avez pas besoin d’apporter des modifications de code d’application à utiliser ces fournisseurs, mais notez les éléments suivants :

- Vous (ou votre administrateur de base de données) devez vérifier que le nom du fournisseur (configuré dans les métadonnées de clé principale de colonne) est correct et que le chemin de la clé principale de colonne est valide pour un fournisseur donné. Nous vous recommandons de configurer les clés à l’aide d’outils tels que SQL Server Management Studio qui génère automatiquement des noms de fournisseurs et des chemins de clés valides lors de l’émission de l’instruction CREATE COLUMN MASTER KEY (Transact-SQL).
- Vérifiez que votre application peut accéder à la clé dans le magasin de clés. Pour cette tâche, vous devrez peut-être accorder à votre application l’accès à la clé et/ou au magasin de clés (en fonction du magasin de clés) ou effectuer d’autres étapes de configuration propres au magasin de clés. Par exemple, pour l’utilisation de la SQLServerColumnEncryptionJavaKeyStoreProvider, vous devez fournir l’emplacement et le mot de passe du magasin de clés dans les propriétés de connexion. 

Tous ces fournisseurs de magasin de clés sont décrits plus en détail dans les sections qui suivent. Vous devez uniquement implémenter un fournisseur de magasin de clés pour utiliser Always Encrypted.

### <a name="using-azure-key-vault-provider"></a>Utilisation du fournisseur Azure Key Vault
Azure Key Vault est un outil est très pratique qui permet de stocker et de gérer des clés principales de colonne Always Encrypted, en particulier si votre application est hébergée dans Azure. Le pilote JDBC de Microsoft pour SQL Server inclut un fournisseur intégré, SQLServerColumnEncryptionAzureKeyVaultProvider, pour les applications qui ont des clés stockées dans Azure Key Vault. Le nom de ce fournisseur est AZURE_KEY_VAULT. Pour pouvoir utiliser le fournisseur de magasin de Azure Key Vault, un développeur d’applications doit créer le coffre et les clés dans Azure Key Vault et créer une inscription d’application dans Azure Active Directory. L’application inscrite doit être accordé obtenir, déchiffrer, chiffrer, désencapsuler la clé, Wrap Key et vérifiez les autorisations dans les stratégies d’accès définis pour le coffre de clés créé pour une utilisation avec Always Encrypted. Pour plus d’informations sur la façon de configurer le coffre de clés et créez une clé principale de colonne, consultez [Azure Key Vault – étape par étape](https://blogs.technet.microsoft.com/kv/2015/06/02/azure-key-vault-step-by-step/) et [création des clés de principales de colonne dans Azure Key Vault](../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md#creating-column-master-keys-in-azure-key-vault).

Pour les exemples dans cette page, si vous avez créé un coffre de clés Azure basé sur clé principale de colonne et de clé de chiffrement de colonne à l’aide de SQL Server Management Studio, le script T-SQL pour recréer les peut ressembler à cet exemple avec ses propres **clé_ Chemin d’accès** et **ENCRYPTED_VALUE**:

```sql
CREATE COLUMN MASTER KEY [MyCMK]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'AZURE_KEY_VAULT',
    KEY_PATH = N'https://<MyKeyValutName>.vault.azure.net:443/keys/Always-Encrypted-Auto1/c61f01860f37302457fa512bb7e7f4e8'
)

CREATE COLUMN ENCRYPTION KEY [MyCEK]
WITH VALUES
(
    COLUMN_MASTER_KEY = [MyCMK],
    ALGORITHM = 'RSA_OAEP',
    ENCRYPTED_VALUE = 0x01BA000001680074507400700073003A002F002F006400610076006...
)
```

Pour utiliser Azure Key Vault, les applications clientes doivent instancier la SQLServerColumnEncryptionAzureKeyVaultProvider et l’inscrire avec le pilote.

Voici un exemple d’initialisation SQLServerColumnEncryptionAzureKeyVaultProvider :  

```java
SQLServerColumnEncryptionAzureKeyVaultProvider akvProvider = new SQLServerColumnEncryptionAzureKeyVaultProvider(clientID, clientKey);
```

**clientID** est l’ID d’Application d’une inscription d’application dans une instance d’Azure Active Directory. **clientKey** est un mot de passe de clé inscrit sous cette Application, qui fournit l’accès à l’API pour Azure Key Vault.

Une fois que l’application crée une instance de SQLServerColumnEncryptionAzureKeyVaultProvider, l’application doit inscrire l’instance avec le pilote à l’aide de la méthode sqlserverconnection.registercolumnencryptionkeystoreproviders (). Il est vivement recommandé que l’instance est inscrite en utilisant le nom de recherche par défaut, AZURE_KEY_VAULT, qui peut être obtenu en appelant l’API SQLServerColumnEncryptionAzureKeyVaultProvider.getName(). En utilisant le nom par défaut vous permettra d’utiliser des outils tels que SQL Server Management Studio ou PowerShell pour approvisionner et gérer des clés Always Encrypted (les outils utilisent le nom par défaut pour générer l’objet de métadonnées pour la clé principale de colonne). L’exemple suivant montre l’inscription du fournisseur Azure Key Vault. Pour plus d’informations sur la méthode sqlserverconnection.registercolumnencryptionkeystoreproviders (), consultez [toujours chiffré référence des API pour le pilote JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).

```java
Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();
keyStoreMap.put(akvProvider.getName(), akvProvider);
SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);
```

> [!IMPORTANT]
>  Si vous utilisez le fournisseur de magasin de clés Azure Key Vault, l’implémentation d’Azure Key Vault du pilote JDBC a des dépendances sur ces bibliothèques (à partir de GitHub) qui doivent être inclus avec votre application :
>
>  [Azure sdk pour java](https://github.com/Azure/azure-sdk-for-java)
>
>  [bibliothèques Azure-activedirectory-library-for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java)
>
> Pour obtenir un exemple montrant comment inclure ces dépendances dans un projet Maven, consultez [télécharger ADAL4J et AKV dépendances avec Apache Maven](https://github.com/Microsoft/mssql-jdbc/wiki/Download-ADAL4J-And-AKV-Dependencies-with-Apache-Maven)

### <a name="using-windows-certificate-store-provider"></a>À l’aide du fournisseur de Store de certificat Windows
SQLServerColumnEncryptionCertificateStoreProvider peut être utilisé pour stocker les clés principales de colonne dans le magasin de certificats Windows. Utilisez l’Assistant Always Encrypted de SQL Server Management Studio (SSMS) ou autres outils pris en charge pour créer les définitions de clé la clé principale de colonne et le chiffrement de colonne dans la base de données. L’Assistant même peut être utilisé pour générer un certificat auto-signé dans le Store de certificat Windows peut servir d’une clé principale de colonne pour les données toujours chiffrées. Pour plus d’informations sur clé principale de colonne et la syntaxe T-SQL clé de chiffrement de colonne, consultez [CREATE COLUMN MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md) et [CREATE COLUMN ENCRPTION KEY](../../t-sql/statements/create-column-encryption-key-transact-sql.md) respectivement.

Le nom de la SQLServerColumnEncryptionCertificateStoreProvider est MSSQL_CERTIFICATE_STORE et peut être interrogé par l’API getName() de l’objet fournisseur. Il est automatiquement enregistré par le pilote et peut être utilisé en toute transparence sans aucune modification de l’application.

Pour les exemples dans cette page, si vous avez créé un Store de certificat Windows basé sur clé principale de colonne et de clé de chiffrement de colonne à l’aide de SQL Server Management Studio, le script T-SQL pour recréer les peut ressembler à cet exemple avec son propre spécifique **KEY_PATH** et **ENCRYPTED_VALUE**:

```sql
CREATE COLUMN MASTER KEY [MyCMK]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'MSSQL_CERTIFICATE_STORE',
    KEY_PATH = N'CurrentUser/My/A2A91F59C461B559E4D962DA9D2BC6131B32CB91'
)

CREATE COLUMN ENCRYPTION KEY [MyCEK]
WITH VALUES
(
    COLUMN_MASTER_KEY = [MyCMK],
    ALGORITHM = 'RSA_OAEP',
    ENCRYPTED_VALUE = 0x016E000001630075007200720065006E0074007500730065007200...
)
```

> [!IMPORTANT]
> Alors que les autres fournisseurs de magasin de clés dans cet article sont disponibles sur toutes les plateformes prises en charge par le pilote, l’implémentation de SQLServerColumnEncryptionCertificateStoreProvider du pilote JDBC est disponible sur les systèmes d’exploitation Windows uniquement. Il a une dépendance sur le fichier sqljdbc_auth.dll qui est disponible dans le package de pilotes. Pour utiliser ce fournisseur, copiez le fichier sqljdbc_auth.dll dans un répertoire sur le chemin du système Windows de l’ordinateur sur lequel le pilote JDBC est installé. Vous pouvez également définir la propriété système java.libary.path afin de spécifier le répertoire du fichier sqljdbc_auth.dll. Si vous exécutez une machine virtuelle Java (JVM) 32 bits, utilisez le fichier sqljdbc_auth.dll dans le dossier x86, même si la version du système d'exploitation est x64. Si vous exécutez une machine virtuelle Java (JVM) 64 bits sur un processeur x64, utilisez le fichier sqljdbc_auth.dll dans le dossier x64. Par exemple, si vous utilisez la machine virtuelle Java 32 bits et que le pilote JDBC est installé dans le répertoire par défaut, vous pouvez spécifier l’emplacement de la DLL à l’aide de l’argument de machine virtuelle suivant lors du démarrage de l’application Java : `-Djava.library.path=C:\Microsoft JDBC Driver <version> for SQL Server\sqljdbc_<version>\enu\auth\x86`

### <a name="using-java-key-store-provider"></a>À l’aide du fournisseur de Java clé Store
Le pilote JDBC est fourni avec une implémentation de fournisseur de magasins de clés intégrée pour le magasin de clés Java. Si le **keyStoreAuthentication** propriété chaîne de connexion est présente dans la chaîne de connexion et il est défini sur « JavaKeyStorePassword », le pilote instancie automatiquement et inscrit le fournisseur pour Java clé Store. Le nom du fournisseur de Java clé Store est MSSQL_JAVA_KEYSTORE. Ce nom peut également être interrogé à l’aide de l’API SQLServerColumnEncryptionJavaKeyStoreProvider.getName(). 

Il existe trois propriétés de chaîne de connexion qui permettent une application cliente spécifier les informations d’identification que le pilote doit s’authentifier sur le Store de clé Java. Le pilote initialise le fournisseur selon les valeurs de ces trois propriétés dans la chaîne de connexion.

**keyStoreAuthentication :** identifie le Store de clé Java à utiliser. Avec le pilote Microsoft JDBC 6.0 et versions ultérieure pour SQL Server, vous pouvez authentifier vers le Store de clé Java uniquement par le biais de cette propriété. Pour le Store de clé Java, la valeur de cette propriété doit être `JavaKeyStorePassword`.

**keyStoreLocation :** le chemin d’accès au fichier Store de clé Java qui stocke la clé principale de colonne. Le chemin d’accès inclut le nom de fichier du magasin de clés.

**keyStoreSecret :** le secret/mot de passe à utiliser pour le keystore ainsi que pour la clé. Pour utiliser le Store de clé Java, le magasin de clés et le mot de passe de clé doivent être le même.

Voici un exemple de fournir ces informations d’identification dans la chaîne de connexion :

```java
String connectionUrl = "jdbc:sqlserver://<server>:<port>;user=<user>;password=<password>;columnEncryptionSetting=Enabled;keyStoreAuthentication=JavaKeyStorePassword;keyStoreLocation=<path_to_the_keystore_file>;keyStoreSecret=<keystore_key_password>";
```

Vous pouvez également obtenir ou définir ces paramètres à l’aide de l’objet SQLServerDataSource. Pour plus d’informations, consultez [toujours chiffré référence des API pour le pilote JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).

Le pilote JDBC instancie automatiquement le SQLServerColumnEncryptionJavaKeyStoreProvider lorsque ces informations d’identification sont présentes dans les propriétés de connexion.

### <a name="creating-a-column-master-key-for-the-java-key-store"></a>Création d’une clé principale de colonne pour le Store de clé Java
Le SQLServerColumnEncryptionJavaKeyStoreProvider peut être utilisé avec les types de magasin de clés JKS ou PKCS12. Pour créer ou importer une clé à utiliser avec ce fournisseur utiliser Java [keytool](http://docs.oracle.com/javase/7/docs/technotes/tools/windows/keytool.html) utilitaire. La clé doit avoir le même mot de passe en tant que le magasin de clés. Voici un exemple montrant comment créer une clé publique et sa clé privée associée à l’aide de l’utilitaire keytool :

```
keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.jks -storepass mypassword -validity 360 -keysize 2048 -storetype jks
```

Cette commande crée une clé publique et encapsulé dans un X.509 auto-signé certificat, qui est stocké dans le magasin de clés 'keystore.jks', ainsi que sa clé privée associée. Cette entrée dans le magasin de clés est identifiée par l’alias « AlwaysEncryptedKey ».

Voici un exemple de la même en utilisant un type de magasin PKCS12 :

```
keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.pfx -storepass mypassword -validity 360 -keysize 2048 -storetype pkcs12 -keypass mypassword
```

Si le magasin de clés est de type PKCS12, l’utilitaire keytool ne demande pas un mot de passe de clé et le mot de passe de clé doit être fourni avec l’option de keypass - comme la SQLServerColumnEncryptionJavaKeyStoreProvider nécessite que le magasin de clés et la clé ont les mêmes mot de passe.

Vous pouvez également exporter un certificat dans le magasin de certificats de Windows au format .pfx et l’utiliser avec le SQLServerColumnEncryptionJavaKeyStoreProvider. Le certificat exporté ne peut également être importé dans le Store de clé Java comme un type de magasin de clés JKS.

Après avoir créé l’entrée de keytool, crée les métadonnées de clé principale de colonne dans la base de données, ce qui nécessite le nom de fournisseur de magasin de clés et le chemin de clé. Pour plus d’informations sur la création des métadonnées de clé principale de colonne, consultez [CREATE COLUMN MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md). Pour SQLServerColumnEncryptionJavaKeyStoreProvider, le chemin de clé est simplement l’alias de la clé et le nom de la SQLServerColumnEncryptionJavaKeyStoreProvider est « MSSQL_JAVA_KEYSTORE ». Vous pouvez également interroger ce nom à l’aide de l’API publique getName() de la classe SQLServerColumnEncryptionJavaKeyStoreProvider. 

La syntaxe T-SQL pour la création de la clé principale de colonne est :

```sql
CREATE COLUMN MASTER KEY [<CMK_name>]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'MSSQL_JAVA_KEYSTORE',
    KEY_PATH = N'<key_alias>'
)
```

Pour le « AlwaysEncryptedKey » créé ci-dessus, la définition de clé principale de colonne serait :

```sql
CREATE COLUMN MASTER KEY [MyCMK]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'MSSQL_JAVA_KEYSTORE',
    KEY_PATH = N'AlwaysEncryptedKey'
)
```

> [!NOTE]
> La gestion de SQL Server intégrée des fonctionnalités de Studio ne peut pas créer des définitions de clé principale de colonne pour le Store de clé Java. Commandes T-SQL doivent être utilisés par programme.

### <a name="creating-a-column-encryption-key-for-the-java-key-store"></a>Création d’une clé de chiffrement de colonne pour le Store de clé Java
SQL Server Management Studio ou tout autre outil ne peut pas être utilisé pour créer des clés de chiffrement à l’aide de clés principales de colonne dans le Store de clé Java de colonne. L’application cliente doit créer la clé de chiffrement de colonne par programmation à l’aide de la classe SQLServerColumnEncryptionJavaKeyStoreProvider. Pour plus d’informations, consultez [à l’aide de fournisseurs de magasin de clés principales de colonne pour l’approvisionnement des clés par programmation](#using-column-master-key-store-providers-for-programmatic-key-provisioning).

### <a name="implementing-a-custom-column-master-key-store-provider"></a>Implémentation d’un fournisseur de magasin de clés principales de colonne personnalisé
Si vous voulez stocker des clés principales de colonne dans un magasin de clés qui n’est pas pris en charge par un fournisseur existant, vous pouvez implémenter un fournisseur personnalisé en étendant la classe SQLServerColumnEncryptionKeyStoreProvider et en inscrivant le fournisseur à l’aide de la méthode SQLServerConnection.registerColumnEncryptionKeyStoreProviders().

```java
public class MyCustomKeyStore extends SQLServerColumnEncryptionKeyStoreProvider{  
    private String name = "MY_CUSTOM_KEYSTORE";

    public void setName(String name)
    {
        this.name = name;
    }

    public String getName()
    {
        return name;
    }

    public byte[] encryptColumnEncryptionKey(String masterKeyPath, String encryptionAlgorithm, byte[] plainTextColumnEncryptionKey)
    {
        // Logic for encrypting the column encryption key
    }

    public byte[] decryptColumnEncryptionKey(String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)
    {
        // Logic for decrypting the column encryption key
    }
}
```

Inscrivez le fournisseur :

```java
SQLServerColumnEncryptionKeyStoreProvider storeProvider = new MyCustomKeyStore();
Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();
keyStoreMap.put(storeProvider.getName(), storeProvider);
SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);
```

## <a name="using-column-master-key-store-providers-for-programmatic-key-provisioning"></a>Utilisation des fournisseurs de magasin de clés principales de colonne pour la mise en service des clés par programmation
Quand il accède à des colonnes chiffrées, Microsoft JDBC Driver pour SQL Server localise et appelle de manière transparente le fournisseur de magasin de clés principales de colonne qui convient pour déchiffrer les clés de chiffrement de colonne. En règle générale, un code d’application normal n’appelle pas directement les fournisseurs de magasin de clés principales de colonne. Toutefois, vous pouvez instancier et appeler un fournisseur par programmation pour approvisionner et gérer des clés Always Encrypted. Cette étape peut être effectuée pour générer une clé de chiffrement de colonne chiffrée et de déchiffrer une clé de chiffrement de colonne en tant que partie rotation de clé principale de la colonne, par exemple. Pour plus d’informations, consultez [Vue d’ensemble de la gestion des clés pour Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md).

Si vous utilisez un fournisseur de magasins de clés personnalisé, l’implémentation de vos propres outils de gestion de clés peut être nécessaire. Lorsque vous utilisez des clés stockées dans le Store de certificats Windows ou dans Azure Key Vault, vous pouvez utiliser les outils existants, tels que SQL Server Management Studio ou PowerShell, pour gérer et configurer des clés. Lorsque vous utilisez des clés stockées dans le Store de clé Java, vous devez configurer les clés par programmation. L’exemple suivant illustre l’utilisation de la classe SQLServerColumnEncryptionJavaKeyStoreProvider pour chiffrer la clé avec une clé stockée dans le Store de clé Java.

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionJavaKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerException;

/**
 * This program demonstrates how to create a column encryption key programmatically for the Java Key Store.
 */
public class AlwaysEncrypted {
    // Alias of the key stored in the keystore.
    private static String keyAlias = "<proide key alias>";

    // Name by which the column master key will be known in the database.
    private static String columnMasterKeyName = "MyCMK";

    // Name by which the column encryption key will be known in the database.
    private static String columnEncryptionKey = "MyCEK";

    // The location of the keystore.
    private static String keyStoreLocation = "C:\\Dev\\Always Encrypted\\keystore.jks";

    // The password of the keystore and the key.
    private static char[] keyStoreSecret = "********".toCharArray();

    /**
     * Name of the encryption algorithm used to encrypt the value of the column encryption key. The algorithm for the system providers must be
     * RSA_OAEP.
     */
    private static String algorithm = "RSA_OAEP";

    public static void main(String[] args) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<databaseName>;user=<user>;password=<password>;columnEncryptionSetting=Enabled;";

        try (Connection connection = DriverManager.getConnection(connectionUrl);
                Statement statement = connection.createStatement();) {

            // Instantiate the Java Key Store provider.
            SQLServerColumnEncryptionKeyStoreProvider storeProvider = new SQLServerColumnEncryptionJavaKeyStoreProvider(keyStoreLocation,
                    keyStoreSecret);

            byte[] encryptedCEK = getEncryptedCEK(storeProvider);

            /**
             * Create column encryption key For more details on the syntax, see:
             * https://docs.microsoft.com/sql/t-sql/statements/create-column-encryption-key-transact-sql Encrypted column encryption key first needs
             * to be converted into varbinary_literal from bytes, for which byteArrayToHex() is used.
             */
            String createCEKSQL = "CREATE COLUMN ENCRYPTION KEY "
                    + columnEncryptionKey
                    + " WITH VALUES ( "
                    + " COLUMN_MASTER_KEY = "
                    + columnMasterKeyName
                    + " , ALGORITHM =  '"
                    + algorithm
                    + "' , ENCRYPTED_VALUE =  0x"
                    + byteArrayToHex(encryptedCEK)
                    + " ) ";
            statement.executeUpdate(createCEKSQL);
            System.out.println("Column encryption key created with name : " + columnEncryptionKey);
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static byte[] getEncryptedCEK(SQLServerColumnEncryptionKeyStoreProvider storeProvider) throws SQLServerException {
        String plainTextKey = "You need to give your plain text";

        // plainTextKey has to be 32 bytes with current algorithm supported
        byte[] plainCEK = plainTextKey.getBytes();

        // This will give us encrypted column encryption key in bytes
        byte[] encryptedCEK = storeProvider.encryptColumnEncryptionKey(keyAlias, algorithm, plainCEK);

        return encryptedCEK;
    }

    public static String byteArrayToHex(byte[] a) {
        StringBuilder sb = new StringBuilder(a.length * 2);
        for (byte b : a)
            sb.append(String.format("%02x", b).toUpperCase());
        return sb.toString();
    }
}
```

## <a name="enabling-always-encrypted-for-application-queries"></a>Activation d’Always Encrypted pour les requêtes d’application
Le moyen le plus simple d’activer le chiffrement des paramètres et le déchiffrement des résultats de requête qui ciblent des colonnes chiffrées consiste à affecter la valeur **Activé** au mot clé de chaîne de connexion **columnEncryptionSetting**.

La chaîne de connexion suivante est un exemple d’activation d’Always Encrypted dans le pilote JDBC :

```java
String connectionUrl = "jdbc:sqlserver://<server>:<port>;user=<user>;password=<password>;databaseName=<database>;columnEncryptionSetting=Enabled;";
SQLServerConnection connection = (SQLServerConnection) DriverManager.getConnection(connectionUrl);
```

Le code suivant est un exemple équivalent à l’aide de l’objet SQLServerDataSource :

```java
SQLServerDataSource ds = new SQLServerDataSource();
ds.setServerName("<server>");
ds.setPortNumber(<port>);
ds.setUser("<user>");
ds.setPassword("<password>");
ds.setDatabaseName("<database>");
ds.setColumnEncryptionSetting("Enabled");
SQLServerConnection con = (SQLServerConnection) ds.getConnection();
```

Always Encrypted peut également être activé pour les requêtes individuelles. Pour plus d’informations, consultez [contrôlant l’impact sur les performances d’Always Encrypted](#controlling-the-performance-impact-of-always-encrypted). L’activation d’Always Encrypted ne suffit pas à la réussite du chiffrement ou du déchiffrement. Vous devez également vérifier ce qui suit :
- L’application dispose des autorisations de base de données *VIEW ANY COLUMN MASTER KEY DEFINITION* et *VIEW ANY COLUMN ENCRYPTION KEY DEFINITION* qui sont nécessaires pour accéder aux métadonnées des clés Always Encrypted dans la base de données. Pour plus d’informations, consultez [Autorisations dans Always Encrypted (moteur de base de données)](../../relational-databases/security/encryption/always-encrypted-database-engine.md#database-permissions).
- L’application peut accéder à la clé principale de colonne qui protège les clés de chiffrement de colonne, qui chiffrent les colonnes de base de données interrogées. Pour utiliser le fournisseur de Java clé Store, vous devez fournir les informations d’identification supplémentaires dans la chaîne de connexion. Pour plus d’informations, consultez [fournisseur de Store de clé Java Using](#using-java-key-store-provider).

### <a name="configuring-how-javasqltime-values-are-sent-to-the-server"></a>Configuration du mode d’envoi des valeurs java.sql.Time au serveur
La propriété de connexion **sendTimeAsDatetime** est utilisée pour configurer la manière dont la valeur java.sql.Time est envoyée au serveur. Lorsque cette propriété a la valeur false, la valeur d’heure est envoyée en tant qu’un type d’heure SQL Server. Lorsque cette propriété a la valeur true, l’heure d’envoi de la valeur en un type datetime. Si une colonne time est chiffrée, le **sendTimeAsDatetime** propriété doit être défini sur false, comme des colonnes chiffrées ne prennent pas en charge la conversion à partir de l’heure en date/heure. Notez également que cette propriété est true par défaut, lorsque vous utilisez des colonnes chiffrées de temps vous devez donc affectez-lui la valeur false. Sinon, le pilote lève une exception. À partir de la version 6.0 du pilote, la classe SQLServerConnection a deux méthodes pour configurer la valeur de cette propriété par programmation :
 
* setSendTimeAsDatetime void publique (sendTimeAsDateTimeValue booléenne)
* public boolean getSendTimeAsDatetime()

Pour plus d’informations sur cette propriété, consultez [java.sql.Time configurer comment les valeurs sont envoyées au serveur](configuring-how-java-sql-time-values-are-sent-to-the-server.md).

### <a name="configuring-how-string-values-are-sent-to-the-server"></a>Configurer comment les valeurs de chaîne sont envoyés au serveur
Le **sendStringParametersAsUnicode** propriété de connexion est utilisée pour configurer comment les valeurs de chaîne sont envoyés à SQL Server. Si elle a la valeur True, les paramètres String sont envoyés au serveur au format Unicode. Si défini sur false, paramètres de chaîne est envoyé dans un format non Unicode, tels que MBCS, Unicode ou ASCII. La valeur par défaut de cette propriété est True. Quand Always Encrypted est activé et une colonne char/varchar/varchar(max) est chiffrée, la valeur de **sendStringParametersAsUnicode** doit être définie sur false. Si cette propriété est définie sur true, le pilote lève une exception lors du déchiffrage des données d’une colonne chiffrée char/varchar/varchar(max) qui comporte des caractères Unicode. Pour plus d’informations sur cette propriété, consultez [définissant les propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md).
  
## <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>Récupération et modification des données dans des colonnes chiffrées
Une fois que vous activez Always Encrypted pour les requêtes de l’application, vous pouvez utiliser l’API JDBC standard pour récupérer ou modifier des données dans les colonnes de la base de données chiffrée. Si votre application dispose des autorisations de base de données requis et peut accéder à la clé principale de colonne, le pilote chiffre tous les paramètres de requête qui ciblent des colonnes chiffrées et déchiffrement les données récupérées à partir des colonnes chiffrées.

Si Always Encrypted n’est pas activé, les requêtes ayant des paramètres qui ciblent des colonnes chiffrées échouent. Une requête peut toujours récupérer des données à partir de colonnes chiffrées, tant qu’aucun de ses paramètres ne cible des colonnes chiffrées. Toutefois, dans ce cas, le pilote ne tente pas de déchiffrer les valeurs extraites des colonnes chiffrées et l’application ne reçoit pas les données chiffrées binaires (sous la forme de tableaux d’octets).

Le tableau ci-dessous récapitule le comportement des requêtes, selon qu’Always Encrypted est activé ou non :

| Caractéristique de la requête                                                                           | Always Encrypted est activé et l’application peut accéder aux clés et à leurs métadonnées                                                                                                                        | Always Encrypted est activé et l’application ne peut pas accéder aux clés et à leurs métadonnées | Always Encrypted est désactivé                                                                                        |
| :--------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------ |
| Requêtes avec des paramètres ciblant des colonnes chiffrées.                                           | Des valeurs de paramètres sont chiffrées en toute transparence.                                                                                                                                                           | Error                                                                             | Error                                                                                                               |
| Requêtes qui récupèrent des données à partir de colonnes chiffrées, sans paramètres ciblant des colonnes chiffrées. | Les résultats de colonnes chiffrées sont déchiffrés de manière transparente. L’application reçoit des valeurs en texte clair des types de données JDBC correspondant aux types SQL Server configurés pour les colonnes chiffrées. | Error                                                                             | Les résultats des colonnes chiffrées ne sont pas déchiffrés. L’application reçoit des valeurs chiffrées sous la forme de tableaux d’octets (byte[]). |

### <a name="inserting-and-retrieving-encrypted-data-examples"></a>Insertion et extraire des exemples de données chiffrées

Les exemples suivants illustrent la récupération et la modification de données dans des colonnes chiffrées. Les exemples supposent que la table cible avec le schéma et les colonnes SSN et BirthDate chiffrées. Si vous avez configuré une clé principale de colonne nommé « MyCMK » et une clé de chiffrement de colonne nommé « MyCEK » (comme décrit dans les sections de fournisseurs de magasin de clés précédentes), vous pouvez créer la table à l’aide de ce script :

```sql
CREATE TABLE [dbo].[Patients]([PatientId] [int] IDENTITY(1,1),
 [SSN] [char](11) COLLATE Latin1_General_BIN2
 ENCRYPTED WITH (ENCRYPTION_TYPE = DETERMINISTIC,
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256',
 COLUMN_ENCRYPTION_KEY = MyCEK) NOT NULL,
 [FirstName] [nvarchar](50) NULL,
 [LastName] [nvarchar](50) NULL,
 [BirthDate] [date]
 ENCRYPTED WITH (ENCRYPTION_TYPE = RANDOMIZED,
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256',
 COLUMN_ENCRYPTION_KEY = MyCEK) NOT NULL
 PRIMARY KEY CLUSTERED ([PatientId] ASC) ON [PRIMARY])
 GO
```

Pour chaque exemple de code Java, vous devez insérer du code spécifique de magasin de clés dans l’emplacement indiqué.

Si vous utilisez un fournisseur de magasin de clés Azure Key Vault :

```java
    String clientID = "<Azure Application ID>";
    String clientKey = "<Azure Application API Key Password>";
    SQLServerColumnEncryptionAzureKeyVaultProvider akvProvider = new SQLServerColumnEncryptionAzureKeyVaultProvider(clientID, clientKey);
    Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();
    keyStoreMap.put(akvProvider.getName(), akvProvider);
    SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);
    String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<databaseName>;user=<user>;password=<password>;columnEncryptionSetting=Enabled;";
```

Si vous utilisez un fournisseur de magasin de clés Windows certificat Store :

```java
    String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<databaseName>;user=<user>;password=<password>;columnEncryptionSetting=Enabled;";
```

Si vous utilisez un fournisseur de magasin de clés Java clé Store :

```java
    String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<databaseName>;user=<user>;password=<password>;columnEncryptionSetting=Enabled;keyStoreAuthentication=JavaKeyStorePassword;keyStoreLocation=<path to jks or pfx file>;keyStoreSecret=<keystore secret/password>";
```

### <a name="inserting-data-example"></a>Exemple d’insertion de données

Cet exemple insère une ligne dans la table Patients. Notez les points suivants :

- L’exemple de code ne contient aucun élément spécifique au chiffrement. Microsoft JDBC Driver for SQL Server détecte automatiquement et chiffre les paramètres qui ciblent des colonnes chiffrées. Ce comportement rend le chiffrement transparent pour l’application.
- Les valeurs insérées dans les colonnes de base de données, y compris les colonnes chiffrées, sont passés comme paramètres à l’aide de SQLServerPreparedStatement. L’utilisation de paramètres est facultative lors de l’envoi de valeurs à des colonnes non chiffrées (même si elle est vivement recommandée, car elle contribue à empêcher l’injection SQL), mais elle est nécessaire pour les valeurs qui ciblent des colonnes chiffrées. Si les valeurs insérées dans les colonnes chiffrées ont été passés en tant que littéraux incorporés dans l’instruction de requête, la requête échoue, car le pilote serait en mesure de déterminer les valeurs de colonnes chiffrées cibles et il n’aurait pas chiffrer les valeurs. Par conséquent, le serveur les rejettera en les considérant comme incompatibles avec les colonnes chiffrées.
- Toutes les valeurs sont imprimées par le programme sous la forme de texte en clair, car Microsoft JDBC Driver pour SQL Server déchiffre de manière transparente les données récupérées à partir des colonnes chiffrées.
- Si vous effectuez une recherche à l’aide d’une clause WHERE, la valeur utilisée dans la clause WHERE doit être transmis en tant que paramètre afin que le pilote peut chiffrer de manière transparente avant de les envoyer à la base de données. Dans l’exemple suivant, le SSN est passé en tant que paramètre, mais le nom est passé comme un littéral comme LastName n’est pas chiffré.
- La méthode setter utilisée pour le paramètre ciblant la colonne SSN est méthodes setString(), qui mappe vers le type de données SQL Server char/varchar. Si, pour ce paramètre, la méthode setter utilisée avait été setNString(), qui mappe vers nchar/nvarchar, la requête aurait échoué, car Always Encrypted ne prend pas en charge les conversions de valeurs nchar/nvarchar chiffrées en valeurs char/varchar chiffrées.

```java
// <Insert keystore-specific code here>
try (Connection sourceConnection = DriverManager.getConnection(connectionUrl);
        PreparedStatement insertStatement = sourceConnection.prepareStatement("INSERT INTO [dbo].[Patients] VALUES (?, ?, ?, ?)")) {
    insertStatement.setString(1, "795-73-9838");
    insertStatement.setString(2, "Catherine");
    insertStatement.setString(3, "Abel");
    insertStatement.setDate(4, Date.valueOf("1996-09-10"));
    insertStatement.executeUpdate();
    System.out.println("1 record inserted.\n");
}
// Handle any errors that may have occurred.
catch (SQLException e) {
    e.printStackTrace();
}
```

### <a name="retrieving-plaintext-data-example"></a>Exemple de récupération de données en texte clair

L’exemple suivant montre le filtrage de données basé sur des valeurs chiffrées, ainsi que la récupération de données en texte clair à partir de colonnes chiffrées. Notez les points suivants :

- La valeur utilisée dans la clause WHERE pour filtrer la colonne SSN doit être passée en tant que paramètre, afin que Microsoft JDBC Driver pour SQL Server puisse la chiffrer de manière transparente avant de l’envoyer à la base de données.
- Toutes les valeurs sont imprimées par le programme sous la forme de texte en clair, car Microsoft JDBC Driver pour SQL Server déchiffre de manière transparente les données récupérées à partir des colonnes SSN et BirthDate.

> [!NOTE]
> Si des colonnes sont chiffrées à l’aide du chiffrement déterministe, les requêtes peuvent effectuer des comparaisons d’égalité sur elles. Pour plus d’informations, consultez [Sélection du chiffrement déterministe ou aléatoire dans Always Encrypted (moteur de base de données)](../../relational-databases/security/encryption/always-encrypted-database-engine.md#selecting--deterministic-or-randomized-encryption).

```java
// <Insert keystore-specific code here>
try (Connection connection = DriverManager.getConnection(connectionUrl);
        PreparedStatement selectStatement = connection
                .prepareStatement("\"SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN = ?;\"");) {
    selectStatement.setString(1, "795-73-9838");
    ResultSet rs = selectStatement.executeQuery();
    while (rs.next()) {
        System.out.println("SSN: " + rs.getString("SSN") + ", FirstName: " + rs.getString("FirstName") + ", LastName:"
                + rs.getString("LastName") + ", Date of Birth: " + rs.getString("BirthDate"));
    }
}
// Handle any errors that may have occurred.
catch (SQLException e) {
    e.printStackTrace();
}
```

### <a name="retrieving-encrypted-data-example"></a>Exemple de récupération de données chiffrées

Si Always Encrypted n’est pas activé, une requête peut toujours récupérer des données à partir de colonnes chiffrées, tant qu’aucun de ses paramètres ne ciblent des colonnes chiffrées.

L’exemple suivant illustre la récupération de données chiffrées binaires à partir de colonnes chiffrées. Notez les points suivants :

- Étant donné qu’Always Encrypted n’est pas toujours activé dans la chaîne de connexion, la requête retourne des valeurs SSN et BirthDate chiffrées sous la forme de tableaux d’octets (le programme convertit les valeurs en chaînes).
- Une requête qui récupère des données à partir de colonnes chiffrées lorsqu’Always Encrypted est désactivé peut avoir des paramètres, tant qu’aucun d’eux ne cible une colonne chiffrée. La requête suivante filtre en fonction des noms (LastName), qui ne sont pas chiffrés dans la base de données. Si la requête filtre par SSN ou BirthDate, la requête échoue.

```java
try (Connection sourceConnection = DriverManager.getConnection(connectionUrl);
        PreparedStatement selectStatement = sourceConnection
                .prepareStatement("SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE LastName = ?;");) {

    selectStatement.setString(1, "Abel");
    ResultSet rs = selectStatement.executeQuery();
    while (rs.next()) {
        System.out.println("SSN: " + rs.getString("SSN") + ", FirstName: " + rs.getString("FirstName") + ", LastName:"
                + rs.getString("LastName") + ", Date of Birth: " + rs.getString("BirthDate"));
    }
}
// Handle any errors that may have occurred.
catch (SQLException e) {
    e.printStackTrace();
}
```

### <a name="avoiding-common-problems-when-querying-encrypted-columns"></a>Éviter les problèmes courants lors de l’interrogation de colonnes chiffrées

Cette section décrit des catégories d’erreurs courantes liées à l’interrogation des colonnes chiffrées à partir d’applications Java, et fournit des conseils sur la façon de les éviter.

### <a name="unsupported-data-type-conversion-errors"></a>Erreurs liées à la conversion de types de données non pris en charge

Always Encrypted ne prend en charge que peu de conversions de types de données chiffrées. Pour obtenir la liste détaillée des conversions de types prises en charge, consultez [Always Encrypted (moteur de base de données)](../../relational-databases/security/encryption/always-encrypted-database-engine.md). Voici comment procéder pour éviter les erreurs de conversion de types de données. Assurez-vous que :

- vous utilisez les méthodes d’accesseur set appropriée lors de la transmission de valeurs pour les paramètres qui ciblent des colonnes chiffrées. Assurez-vous que le type de données SQL Server du paramètre est exactement le même que le type de la colonne cible ou une conversion du type de données SQL Server du paramètre vers le type de cible de la colonne est pris en charge. Méthodes de l’API ont été ajoutées aux classes SQLServerPreparedStatement et SQLServerCallableStatement SQLServerResultSet pour passer des paramètres correspondant aux types de données SQL Server spécifiques. Par exemple, si une colonne ne sont pas chiffrée. vous pouvez utiliser la méthode setTimestamp() pour passer un paramètre à un datetime2 ou à une colonne datetime. Mais quand une colonne est chiffrée, vous devrez utiliser la méthode exacte représentant le type de la colonne dans la base de données. Par exemple, utiliser setTimestamp() pour transmettre des valeurs à une colonne chiffrée datetime2 et utiliser setDateTime() pour transmettre des valeurs à une colonne datetime chiffré. Consultez [toujours chiffré référence des API pour le pilote JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) pour une liste complète des nouvelles API.
- La précision et l’échelle des paramètres ciblant les colonnes des types de données SQL Server decimal et numeric sont les mêmes que celles configurées pour la colonne cible. Méthodes de l’API ont été ajoutées aux classes SQLServerPreparedStatement et SQLServerCallableStatement SQLServerResultSet pour accepter la précision et l’échelle ainsi que les valeurs de données pour les paramètres/colonnes représentant les types de données decimal et numeric. Consultez [toujours chiffré référence des API pour le pilote JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) pour obtenir la liste complète des API de nouveau/surchargé.  
- la précision/échelle de fractions de paramètres ciblant des colonnes de type datetime2, datetimeoffset ou types de données SQL Server n’est pas supérieure à la précision/échelle de fractions pour la colonne cible dans les requêtes qui modifient les valeurs de la colonne cible . Méthodes de l’API ont été ajoutées aux classes SQLServerPreparedStatement et SQLServerCallableStatement SQLServerResultSet pour accepter la précision/échelle de fractions, ainsi que les valeurs de paramètres représentant ces types de données. Pour obtenir une liste complète des API de nouveau/surchargé, consultez [toujours chiffré référence des API pour le pilote JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).

### <a name="errors-due-to-incorrect-connection-properties"></a>Erreurs dues à des propriétés de connexion incorrectes

Cette section décrit comment configurer les paramètres de connexion correctement pour utiliser des données Always Encrypted. Dans la mesure où les types de données chiffrées prennent en charge les conversions limitées, le **sendTimeAsDatetime** et **sendStringParametersAsUnicode** paramètres de connexion nécessitent une configuration appropriée lors de l’utilisation des colonnes chiffrées. Assurez-vous que :

- [sendTimeAsDatetime](setting-the-connection-properties.md) connexion est défini sur false lors de l’insertion de données dans des colonnes de temps chiffrées. Pour plus d’informations, consultez [configurer comment les valeurs java.sql.Time sont envoyées au serveur](configuring-how-java-sql-time-values-are-sent-to-the-server.md).
- [sendStringParametersAsUnicode](setting-the-connection-properties.md) connexion est défini sur true (ou est considérée comme la valeur par défaut) lorsque de l’insertion des données dans des colonnes de char/varchar/varchar(max) chiffrées.

### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>Erreurs dues au passage de texte en clair au lieu de valeurs chiffrées

Les valeurs qui ciblent une colonne chiffrée doivent être chiffrées dans l’application. Toute tentative d’insertion, de modification ou de filtrage par une valeur en texte clair dans une colonne chiffrée entraîne une erreur similaire à celle-ci :

```java
com.microsoft.sqlserver.jdbc.SQLServerException: Operand type clash: varchar is incompatible with varchar(8000) encrypted with (encryption_type = 'DETERMINISTIC', encryption_algorithm_name = 'AEAD_AES_256_CBC_HMAC_SHA_256', column_encryption_key_name = 'MyCEK', column_encryption_key_database_name = 'ae') collation_name = 'SQL_Latin1_General_CP1_CI_AS'
```

Pour éviter ces erreurs, procédez comme suit :

- Activez Always Encrypted pour les requêtes d’application ciblant des colonnes chiffrées (pour la chaîne de connexion ou pour une requête spécifique).
- vous utilisez des instructions préparées et paramètres à envoyer des données ciblant des colonnes chiffrées. L’exemple suivant illustre une requête qui filtre incorrectement une colonne chiffrée (SSN) à l’aide d’un littéral ou d’une constante, au lieu de passer le littéral à l’intérieur d’un paramètre. Cette requête échoue :

```java
ResultSet rs = connection.createStatement().executeQuery("SELECT * FROM Customers WHERE SSN='795-73-9838'");
```

## <a name="force-encryption-on-input-parameters"></a>Forcer le chiffrement sur les paramètres d’entrée

La fonctionnalité de forcer le chiffrement applique le chiffrement d’un paramètre lors de l’utilisation de Always Encrypted. Si le chiffrement forcé est utilisé et que SQL Server informe le pilote que le paramètre ne nécessite pas de chiffrement, la requête utilisant le paramètre échoue. Cette propriété fournit une protection supplémentaire contre les attaques au niveau de la sécurité qui impliquent un serveur SQL Server compromis fournissant des métadonnées de chiffrement incorrectes au client, ce qui peut entraîner la divulgation de données. Les méthodes set * dans les classes SQLServerPreparedStatement et SQLServerCallableStatement et de la mise à jour\* méthodes dans la classe SQLServerResultSet sont surchargées afin d’accepter un argument booléen pour spécifier le paramètre de chiffrement de force. Si la valeur de cet argument est false, le pilote ne sont pas forcer le chiffrement sur les paramètres. Si forcer le chiffrement est défini à true, la requête paramètre est uniquement envoyé si la colonne de destination est chiffrée et Always Encrypted est activé sur la connexion ou sur l’instruction. À l’aide de cette propriété donne une couche supplémentaire de sécurité, d’assurer que le pilote ne par inadvertance envoyer des données vers SQL Server en texte brut lorsqu’elle doit être chiffré.

Pour plus d’informations sur les méthodes SQLServerPreparedStatement et SQLServerCallableStatement sont surchargées avec le paramètre de chiffrement de force, consultez [toujours chiffré référence des API pour le pilote JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)  

## <a name="controlling-the-performance-impact-of-always-encrypted"></a>Contrôle de l’impact d’Always Encrypted sur les performances

Always Encrypted étant une technologie de chiffrement côté client, la dégradation des performances s’observe côté client, et non dans la base de données. Outre les opérations de chiffrement et de déchiffrement, les autres sources de dégradation des performances côté client sont les suivantes :

- Allers-retours supplémentaires vers la base de données pour récupérer des métadonnées pour les paramètres de requête.
- Appels au magasin de clés principales de colonne pour accéder à une clé principale de colonne.

Cette section décrit les outils intégrés d’optimisation des performances dans Microsoft JDBC Driver pour SQL Server et comment vous pouvez contrôler l’impact des deux facteurs ci-dessus sur les performances.

### <a name="controlling-round-trips-to-retrieve-metadata-for-query-parameters"></a>Contrôle des allers-retours vers la base de données en vue de la récupération des métadonnées pour les paramètres de requête

Si Always Encrypted est activé pour une connexion, le pilote appelle par défaut [sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) pour chaque requête paramétrable, en passant l’instruction de requête (sans valeurs de paramètre) à SQL Server. [sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) analyse l’instruction de requête afin de savoir si des paramètres doivent être chiffrés. Si c’est le cas, pour chaque paramètre à chiffrer, il retourne des informations relatives au chiffrement qui permettent au pilote de chiffrer les valeurs de paramètre. Ce comportement garantit un haut niveau de transparence à l’application cliente. Tant que l’application utilise des paramètres pour transmettre des valeurs qui ciblent des colonnes chiffrées au pilote, l’application (et le développeur d’applications) n’a pas besoin de connaître les requêtes qui accèdent à des colonnes chiffrées.

### <a name="setting-always-encrypted-at-the-query-level"></a>Configuration d’Always Encrypted au niveau de la requête

Pour contrôler l’impact sur les performances de la récupération des métadonnées de chiffrement pour les requêtes paramétrables, vous pouvez activer Always Encrypted pour chaque requête, au lieu de le configurer pour la connexion. De cette façon, sys.sp_describe_parameter_encryption est appelé uniquement pour les requêtes dont les paramètres ciblent des colonnes chiffrées. Notez toutefois que de cette façon, vous réduisez la transparence du chiffrement. Si vous modifiez les propriétés de chiffrement de vos colonnes de base de données, vous devrez modifier le code de votre application pour l’aligner sur les modifications du schéma.

Pour contrôler le comportement Always Encrypted des requêtes individuelles, vous devez configurer les objets de l’instruction individuelle en passant un Enum, SQLServerStatementColumnEncryptionSetting, qui spécifie comment les données sont envoyées et reçues lors de la lecture et l’écriture colonnes chiffrées pour cette instruction spécifique. Voici quelques conseils utiles :

- Si la plupart des requêtes qu’une application cliente envoie par le biais d’une connexion de base de données accèdent à des colonnes chiffrées, appliquez les recommandations suivantes :

    - Affectez la valeur **Activé** au mot clé de la chaîne de connexion **columnEncryptionSetting**.
    - Définissez SQLServerStatementColumnEncryptionSetting.Disabled pour les requêtes qui n’accèdent à aucune colonne chiffrée. Ce paramètre désactive à la fois l’appel de sys.sp_describe_parameter_encryption et la tentative de déchiffrement des valeurs du jeu de résultats.
    - Définissez SQLServerStatementColumnEncryptionSetting.ResultSet pour les requêtes qui n’ont aucun paramètre exigeant un chiffrement, mais qui récupèrent des données de colonnes chiffrées. Ce paramètre désactive l’appel de sys.sp_describe_parameter_encryption et le chiffrement des paramètres. La requête est alors en mesure de déchiffrer les résultats des colonnes de chiffrement.

- Si la plupart des requêtes qu’une application cliente envoie par le biais d’une connexion de base de données n’accèdent pas à des colonnes chiffrées, appliquez les recommandations suivantes :

    - Affectez la valeur **Disabled** au mot clé de la chaîne de connexion **columnEncryptionSetting**.
    - Définissez SQLServerStatementColumnEncryptionSetting.Enabled pour les requêtes qui ont des paramètres qui doivent être chiffrés. Ce paramètre active à la fois l’appel de sys.sp_describe_parameter_encryption et le déchiffrement des résultats de requête récupérés à partir des colonnes chiffrées.
    - Définissez SQLServerStatementColumnEncryptionSetting.ResultSet pour les requêtes qui n’ont aucun paramètre exigeant un chiffrement, mais qui récupèrent des données de colonnes chiffrées. Ce paramètre désactive l’appel de sys.sp_describe_parameter_encryption et le chiffrement des paramètres. La requête est alors en mesure de déchiffrer les résultats des colonnes de chiffrement.

Les paramètres SQLServerStatementColumnEncryptionSetting ne peut pas être utilisés pour contourner le chiffrement et accéder aux données de texte en clair. Pour plus d’informations sur la façon de configurer le chiffrement de colonne sur une instruction, consultez [toujours chiffré référence des API pour le pilote JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).  

Dans l’exemple suivant, Always Encrypted est désactivé pour la connexion de base de données. La requête envoyée par l’application comprend un paramètre qui cible la colonne LastName qui n’est pas chiffrée. La requête récupère les données des colonnes SSN et BirthDate qui sont toutes deux chiffrées. Dans ce cas, il n’est pas nécessaire d’appeler sys.sp_describe_parameter_encryption pour récupérer les métadonnées de chiffrement. Toutefois, le déchiffrement des résultats de requête doit être activé, afin que l’application puisse recevoir des valeurs de texte en clair à partir des deux colonnes chiffrées. Le paramètre SQLServerStatementColumnEncryptionSetting.ResultSet est utilisé pour vous assurer que.

```java
// Assumes the same table definition as in Section "Retrieving and modifying data in encrypted columns"
// where only SSN and BirthDate columns are encrypted in the database.
String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<database>;user=<user>;password=<password>;" 
        + "keyStoreAuthentication=JavaKeyStorePassword;"
        + "keyStoreLocation=<keyStoreLocation>" 
        + "keyStoreSecret=<keyStoreSecret>;";

String filterRecord = "SELECT FirstName, LastName, SSN, BirthDate FROM " + tableName + " WHERE LastName = ?";

try (SQLServerConnection connection = (SQLServerConnection) DriverManager.getConnection(connectionUrl);
        PreparedStatement selectStatement = connection.prepareStatement(filterRecord, ResultSet.TYPE_FORWARD_ONLY, ResultSet.CONCUR_READ_ONLY,
                connection.getHoldability(), SQLServerStatementColumnEncryptionSetting.ResultSetOnly);) {

    selectStatement.setString(1, "Abel");
    ResultSet rs = selectStatement.executeQuery();
    while (rs.next()) {
        System.out.println("First name: " + rs.getString("FirstName"));
        System.out.println("Last name: " + rs.getString("LastName"));
        System.out.println("SSN: " + rs.getString("SSN"));
        System.out.println("Date of Birth: " + rs.getDate("BirthDate"));
    }
}
// Handle any errors that may have occurred.
catch (SQLException e) {
    e.printStackTrace();
}
```

### <a name="column-encryption-key-caching"></a>Mise en cache des clés de chiffrement de colonne

Pour réduire le nombre d’appels à un magasin de clés principales de colonne pour déchiffrer les clés de chiffrement de colonne, Microsoft JDBC Driver pour SQL Server met en cache les clés de chiffrement de colonne en texte en clair dans la mémoire. Après avoir reçu la valeur de clé de chiffrement de colonne chiffrée à partir des métadonnées de la base de données, le pilote tente d’abord de trouver la clé de chiffrement de colonne en texte en clair qui correspond à la valeur de clé chiffrée. Le pilote appelle le magasin de clés qui contient la clé principale de colonne uniquement s’il ne peut pas trouver la valeur de clé de chiffrement de colonne chiffrée dans le cache.

Vous pouvez configurer une valeur time-to-live pour les entrées de clés de chiffrement de colonne dans le cache à l’aide de l’API, setColumnEncryptionKeyCacheTtl(), dans la classe SQLServerConnection. La valeur de durée de vie par défaut pour les entrées de clés de chiffrement de colonne dans le cache est de deux heures. Pour désactiver la mise en cache, utilisez la valeur 0. Pour définir n’importe quelle valeur time-to-live, utilisez l’API suivante :

```java
SQLServerConnection.setColumnEncryptionKeyCacheTtl (int columnEncryptionKeyCacheTTL, TimeUnit unit)
```

Par exemple, pour définir une valeur time-to-live de 10 minutes, utilisez :

```java
SQLServerConnection.setColumnEncryptionKeyCacheTtl (10, TimeUnit.MINUTES)
```

Uniquement les jours, heures, MINUTES ou secondes sont prises en charge en tant que l’unité de temps.  

## <a name="copying-encrypted-data-using-sqlserverbulkcopy"></a>Copie les données chiffrées à l’aide de SQLServerBulkCopy

Grâce à SQLServerBulkCopy, les données qui sont déjà chiffrées et stockées dans une table peuvent être copiées vers une autre table, sans que vous ayez à les déchiffrer. Pour cela :

- Vérifiez que la configuration du chiffrement de la table cible est identique à celle de la table source. Les deux tables doivent avoir les mêmes colonnes chiffrées, et ces colonnes doivent être chiffrées à l’aide des mêmes types et des mêmes clés de chiffrement. Si une colonne cible est chiffrée différemment de la colonne source correspondante, vous ne pourrez pas déchiffrer les données de la table cible après les avoir copiées. Les données seront endommagées.
- Configurez les deux connexions de base de données, c’est-à-dire celle vers la table source et celle vers la table cible, sans activer Always Encrypted.
- Définissez l’option allowEncryptedValueModifications. Pour plus d’informations, consultez [à l’aide de copie en bloc avec le pilote JDBC](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md).

> [!NOTE]
> Faites attention quand vous spécifiez AllowEncryptedValueModifications, car cette option peut endommager la base de données. En effet, Microsoft JDBC Driver pour SQL Server ne vérifie pas si les données sont chiffrées, ou si elles sont correctement chiffrées à l’aide du même type de chiffrement, du même algorithme et de la même clé que la colonne cible.

## <a name="see-also"></a> Voir aussi

[Always Encrypted (moteur de base de données)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)

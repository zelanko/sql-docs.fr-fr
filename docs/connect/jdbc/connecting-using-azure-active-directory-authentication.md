---
title: "Connexion à l’aide de l’authentification Azure Active Directory | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.topic: article
ms.assetid: 9c9d97be-de1d-412f-901d-5d9860c3df8c
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 83d5ad3bae131b58dd344c3f5f9bfc7f5d0c4f5a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="connecting-using-azure-active-directory-authentication"></a>Connexion à l’aide de l’authentification Azure Active Directory
Cet article fournit des informations sur la façon de développer des applications Java à utiliser la fonctionnalité d’authentification Azure Active Directory avec Microsoft JDBC Driver 6.0 (ou version ultérieure) pour SQL Server.

À partir de Microsoft JDBC Driver 6.0 pour SQL Server, vous pouvez utiliser l’authentification Azure Directory Direcoty (AAD) qui est un mécanisme de se connecter à la base de données SQL Azure v12 à l’aide des identités dans Azure Active Directory. Utilisez l’authentification Azure Active Directory pour gérer les identités des utilisateurs de base de données et comme alternative à l’authentification SQL Server de manière centralisée. Le pilote JDBC 6.0 (ou version ultérieure) vous permet de spécifier vos informations d’identification Azure Active Directory dans la chaîne de connexion JDBC pour se connecter à la base de données SQL Azure. Pour plus d’informations sur la façon de configurer l’authentification Azure Active Directory, visitez [la connexion à SQL de base de données en utilisant authentification Azure Active Directory](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/). 

Deux nouvelles propriétés de connexion ont été ajoutées pour prendre en charge l’authentification Azure Active Directory :
*   **authentification**: utilisez cette propriété pour indiquer quelle méthode d’authentification SQL à utiliser pour la connexion. Les valeurs possibles sont : **ActiveDirectoryIntegrated**, **ActiveDirectoryPassword**, **SqlPassword** et la valeur par défaut **NotSpecified** .
    * Utilisez ' authentication = ActiveDirectoryIntegrated' pour vous connecter à une base de données SQL à l’aide de l’authentification Windows intégrée. Pour utiliser ce mode d’authentification que vous avez besoin de fédérer le sur site Active Directory Federation Services (ADFS) avec Azure AD dans le cloud. Une fois que c’est le programme d’installation, vous pouvez accéder à base de données SQL Azure sans demande de ceredentials lorsque vous êtes connecté dans un ordinateur joint à un domaine. 
    * Utilisez ' authentication = ActiveDirectoryPassword' pour vous connecter à une base de données SQL à l’aide d’un nom principal de Azure AD et un mot de passe.
    * Utilisez ' authentication = SqlPassword » pour vous connecter à un serveur SQL Server à l’aide des propriétés de l’utilisateur ou le nom d’utilisateur et mot de passe.
    * Utilisez ' authentication = NotSpecified » ou laissez le champ comme valeur par défaut si aucune de ces méthodes d’authentification est nécessaire.

*   **accessToken**: utilisez cette propriété pour se connecter à une base de données SQL à l’aide d’un jeton d’accès. accessToken peut uniquement être définie à l’aide du paramètre de propriétés de la méthode getConnection() dans la classe DriverManager. Il ne peut pas être utilisé dans l’URL de connexion.  

Pour plus d’informations, consultez la propriété d’authentification sur le [définissant les propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md) page.  


## <a name="client-setup-requirements"></a>Configuration requise du programme d’installation client
Assurez-vous que les composants suivants sont installés sur l’ordinateur client :
* Java 7 ou version ultérieure
*   Microsoft JDBC Driver 6.2 (ou version ultérieure) pour SQL Server
*   Si vous utilisez le mode d’authentification par jeton accès, vous devez [azure bibliothèque Active Directory pour java](https://github.com/AzureAD/azure-activedirectory-library-for-java) et ses dépendances pour exécuter les exemples de cet article. Consultez **connexion à l’aide du jeton d’accès** section pour plus d’informations.
*   Si vous utilisez le mode d’authentification ActiveDirectoryPassword vous devez [azure bibliothèque Active Directory pour java](https://github.com/AzureAD/azure-activedirectory-library-for-java) et ses dépendances. Consultez **connexion à l’aide du Mode d’authentification ActiveDirectoryPassword** section pour plus d’informations.
*   Si vous utilisez le mode ActiveDirectoryIntegrated, vous devez installer la bibliothèque d’authentification Active Directory pour SQL Server (ADALSQL. DLL) et sqljdbc_auth.dll.
    * ADALSQL. DLL permet aux applications de s’authentifier auprès de Microsoft Azure SQL Database à l’aide d’Azure Active Directory. Télécharger la DLL de [bibliothèque d’authentification Microsoft Active Directory pour Microsoft SQL Server](http://www.microsoft.com/en-us/download/details.aspx?id=48742)
    * Pour ADALSQL. DLL deux versions binaires X86 et X64 sont disponibles en téléchargement. Si la version binaire incorrecte est installée ou si la DLL est manquante, le pilote génère l’erreur suivante : « Impossible de charger adalsql.dll (Authentication =...). Code d’erreur : 0 x 2. ». Dans ce cas, téléchargez la version appropriée de ADALSQL. DLL. 
    * sqljdbc_auth.dll est disponible dans le package de pilotes. Copiez le fichier sqljdbc_auth.dll dans un répertoire sur le chemin d’accès de système de Windows sur l’ordinateur où est installé le pilote JDBC. Vous pouvez également définir la propriété système java.libary.path afin de spécifier le répertoire du fichier sqljdbc_auth.dll. 
    * Si vous exécutez une machine virtuelle Java (JVM) 64 bits sur un processeur x64, utilisez le fichier sqljdbc_auth.dll dans le dossier x64. 
    * Si vous exécutez une machine virtuelle Java (JVM) 32 bits, utilisez le fichier sqljdbc_auth.dll dans le dossier x86, même si la version du système d'exploitation est x64. 
    * Par exemple, si vous utilisez la machine virtuelle Java 32 bits et le pilote JDBC est installé dans le répertoire par défaut, vous pouvez spécifier l’emplacement de la DLL à l’aide de l’argument suivant de la machine virtuelle (VM) au démarrage de l’application Java :  
        ```
        -Djava.library.path=C:\Microsoft JDBC Driver <version> for SQL Server\sqljdbc_<version>\enu\auth\x86
        ```
    
## <a name="connecting-using-activedirectoryintegrated-authentication-mode"></a>Connexion à l’aide du Mode d’authentification ActiveDirectoryIntegrated
L’exemple suivant montre comment utiliser ' authentication = ActiveDirectoryIntegrated' mode. Exécutez cet exemple sur un ordinateur joint à un domaine fédéré avec Azure Active Directory. Un utilisateur de base de données représentant votre principal de Azure AD, ou l’un des groupes, vous appartenez à, doit exister dans la base de données et devez avoir l’autorisation de se connecter. 
    
Avant d’exécuter l’exemple, remplacez le nom de serveur/base de données avec le nom de votre serveur/base de données dans les lignes suivantes :

```
ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
ds.setDatabaseName("demo"); // replace with your database name
```

L’exemple utilise le mode d’authentification ActiveDirectoryIntegrated :
```
import java.sql.Connection;
import java.sql.ResultSet;
import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class IntegratedExample {

    public static void main(String[] args) throws Exception {
        SQLServerDataSource ds = new SQLServerDataSource();

        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name
        ds.setDatabaseName("demo"); // Replace with your database name
        ds.setAuthentication("ActiveDirectoryIntegrated");
        ds.setHostNameInCertificate("*.database.windows.net");

        Connection connection = ds.getConnection();

        ResultSet rs = connection.createStatement().executeQuery("SELECT SUSER_SNAME()");
        if(rs.next()){
            System.out.println("You have successfully logged on as: " + rs.getString(1));
        }
    }
}
```
Cet exemple en cours d’exécution sur un ordinateur joint à un domaine fédéré avec Azure Active Directory utilisera automatiquement vos informations d’identification Windows et aucun mot de passe n’est requis. Si la connexion est établie, vous voyez le message suivant :
```
You have successfully logged on as: <your domain user name>
```

## <a name="connecting-using-activedirectorypassword-authentication-mode"></a>Connexion à l’aide du Mode d’authentification ActiveDirectoryPassword
L’exemple suivant montre comment utiliser ' authentication = ActiveDirectoryPassword' mode.

Avant de générer et exécuter l’exemple :
1.  Sur l’ordinateur client (sur lequel, vous souhaitez exécuter l’exemple), téléchargez le [bibliothèque azure bibliothèque Active Directory pour java](https://github.com/AzureAD/azure-activedirectory-library-for-java) et ses dépendances et les inclure dans le chemin d’accès de build Java
2.  Recherchez les lignes suivantes du code et remplacez le nom de serveur/base de données par le nom de votre serveur/base de données.
    ```
    ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
    ds.setDatabaseName("demo"); // replace with your database name
    ```
3.  Recherchez les lignes suivantes du code et remplacez le nom d’utilisateur, avec le nom de l’utilisateur Azure AD que vous voulez vous connecter.
    ```
    ds.setUser("bob@cqclinic.onmicrosoft.com"); // replace with your user name
    ds.setPassword("password");     // replace with your password
    ```

L’exemple utilise le mode d’authentification ActiveDirectoryPassword :
```
import java.sql.Connection;
import java.sql.ResultSet;
import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class UserPasswordExample {
    
    public static void main(String[] args) throws Exception{
        SQLServerDataSource ds = new SQLServerDataSource();
        
        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name
        ds.setDatabaseName("demo"); // Replace with your database
        ds.setUser("bob@cqclinic.onmicrosoft.com"); // Replace with your user name
        ds.setPassword("password"); // Replace with your password
        ds.setAuthentication("ActiveDirectoryPassword");
        ds.setHostNameInCertificate("*.database.windows.net");
        
        Connection connection = ds.getConnection();
        
        ResultSet rs = connection.createStatement().executeQuery("SELECT SUSER_SNAME()");
        if(rs.next()){
            System.out.println("You have successfully logged on as: " + rs.getString(1));
        }
    }
}
```
Si la connexion est établie, vous voyez le message suivant en tant que sortie :
```
You have successfully logged on as: <your user name>
```

> [!NOTE]  
> Une base de données utilisateur contenu doit exister et un utilisateur de base de données représentant l’utilisateur Azure AD ou l’un des groupes, Azure spécifié utilisateur AD appartient à, doit exister dans la base de données et doit avoir l’autorisation de se connecter (à l’exception d’Azure Active Directory administrateur du serveur ou groupe)


## <a name="connecting-using-access-token"></a>Connexion à l’aide du jeton d’accès
Applications/services peut récupérer un jeton d’accès à partir d’Azure Active Directory et l’utiliser pour se connecter à la base de données SQL Azure. Notez qu’accessToken peut uniquement être définie à l’aide du paramètre de propriétés de la méthode getConnection() dans la classe DriverManager. Il ne peut pas être utilisé dans la chaîne de connexion.
 
L’exemple ci-dessous contient une simple application Java qui se connecte à la base de données SQL Azure à l’aide de l’authentification basée sur jeton d’accès. Avant de générer et exécuter l’exemple, procédez comme suit :
1.  Créer un compte d’application dans Azure Active Directory pour votre service.
    1. Connectez-vous au portail de gestion Azure
    2. Dans le volet de navigation gauche, cliquez sur Azure Active Directory
    3. Cliquez sur le locataire d’annuaire dans lequel vous souhaitez enregistrer l’exemple d’application. Ce doit être le même répertoire que celui qui est associé à votre base de données (le serveur qui héberge votre base de données).
    4. Cliquez sur l’onglet Applications.
    5. Dans le tiroir, cliquez sur Ajouter.
    6. Cliquez sur « Ajouter une application développée par mon organisation ».
    7. Entrez mytokentest sous la forme d’un nom convivial pour l’application, sélectionnez « Application de Web et/ou API Web » et cliquez sur Suivant.
    8. En supposant que cette application est un service/démon et non une application web, il n’a pas une URL ou connexion URI ID d’application. Pour ces deux champs, entrez http://mytokentest
    9. Dans le portail Azure, cliquez sur l’onglet configurer de votre application
    10. Recherche la valeur d’ID Client et copiez-le mis de côté, vous en aurez besoin plus tard lors de la configuration de votre application (c.-à-d.)  a4bbfe26-dbaa-4fec-8ef5-223d229f647d). Consultez l’instantané ci-dessous.
    11. Sous la section « Clés », sélectionnez la durée de la clé, enregistrer la configuration et copiez la clé pour une utilisation ultérieure. Il s’agit de la clé secrète du client.
    12. En bas, cliquez sur « points de terminaison », puis copiez l’URL sous « OAUTH 2.0 AUTHORIZATION ENDPOINT » pour une utilisation ultérieure. Il s’agit de l’URL STS.


![JDBC_AAD_Token](../../connect/jdbc/media/jdbc_aad_token.png)


2. Ouvrez une session sur la base de données utilisateur de votre serveur SQL Azure en tant qu’un administrateur Azure Active Directory et à l’aide une disposition de la commande T-SQL un utilisateur de base de données pour le principal de votre application. Consultez le [la connexion à la base de données SQL ou SQL données entrepôt par à l’aide d’authentification Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/sql-database-aad-authentication/) pour plus d’informations sur la création d’un administrateur Azure Active Directory et un utilisateur de base de données.

    ```
    CREATE USER [mytokentest] FROM EXTERNAL PROVIDER
    ```

3.  Sur l’ordinateur client (sur lequel, vous souhaitez exécuter l’exemple), téléchargez le [azure bibliothèque Active Directory pour java](https://github.com/AzureAD/azure-activedirectory-library-for-java) bibliothèque et ses dépendances et les inclure dans le chemin d’accès de build Java. Notez que l’azure Active Directory-bibliothèque-de-java est uniquement nécessaire pour exécuter cet exemple spécifique, car il utilise les API à partir de cette bibliothèque pour récupérer le jeton d’accès d’Azure AD. Si vous disposez déjà d’un jeton d’accès, vous pouvez ignorer cette étape. Notez que vous devez également supprimer la section de l’exemple qui Récupère le jeton d’accès.

Dans l’exemple ci-dessous, remplacez l’URL STS, ID de Client, question secrète du Client, serveur et nom de la base de données avec vos valeurs.

```
import java.sql.Connection;
import java.sql.ResultSet;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;
import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

// The azure-activedirectory-library-for-java is needed to retrieve the access token from the AD. 
import com.microsoft.aad.adal4j.AuthenticationContext;
import com.microsoft.aad.adal4j.AuthenticationResult;
import com.microsoft.aad.adal4j.ClientCredential;


public class TokenBasedExample {

    public static void main(String[] args) throws Exception{

        // Retrieve the access token from the AD.
        String spn = "https://database.windows.net/";
        String stsurl = "https://login.microsoftonline.com/..."; // Replace with your STS URL.
        String clientId = "a4bbfe26-dbaa-4fec-8ef5-223d229f647d"; // Replace with your client ID.
        String clientSecret = "..."; // Replace with your client secret.

        AuthenticationContext context = new AuthenticationContext(stsurl, false, Executors.newFixedThreadPool(1));
        ClientCredential cred = new ClientCredential(clientId, clientSecret);

        Future<AuthenticationResult> future = context.acquireToken(spn, cred, null);
        String accessToken = future.get().getAccessToken();

        System.out.println("Access Token: " + accessToken);     
        
        // Connect with the access token.
        SQLServerDataSource ds = new SQLServerDataSource();

        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name.
        ds.setDatabaseName("demo"); // Replace with your database name.
        ds.setAccessToken(accessToken);
        ds.setHostNameInCertificate("*.database.windows.net");

        Connection connection = ds.getConnection();

        ResultSet rs = connection.createStatement().executeQuery("SELECT SUSER_SNAME()");
        if(rs.next()){
            System.out.println("You have successfully logged on as: " + rs.getString(1));
        }
    }
}
``` 

Si la connexion est établie, vous voyez le message suivant en tant que sortie :
```
Access Token: <your access token>
You have successfully logged on as: <your client ID>    
``` 

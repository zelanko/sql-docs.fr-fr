---
title: "Utilisation du chiffrement intégral avec le pilote JDBC | Documents Microsoft"
ms.custom: 
ms.date: 12/30/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 271c0438-8af1-45e5-b96a-4b1cabe32707
caps.latest.revision: 64
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7ddf82a6ef055d951c987c8bc156f025c1162f6c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="using-always-encrypted-with-the-jdbc-driver"></a>Utilisation du chiffrement intégral avec le pilote JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Cet article fournit des informations sur la façon de développer des applications Java à l’aide de [Always Encrypted](https://msdn.microsoft.com/library/mt163865.aspx#Anchor_7) et le pilote Microsoft JDBC 6.0 (ou version ultérieure) pour SQL Server.

Always Encrypted permet aux clients de chiffrer les données sensibles et de ne jamais révéler les données ou les clés de chiffrement dans SQL Server ou de la base de données SQL Azure. Un chiffrement intégral activé pilote, tels que le pilote Microsoft JDBC 6.0 (ou version ultérieure) pour SQL Server, cela, le chiffrement et déchiffrement des données sensibles dans l’application cliente de façon transparente. Le pilote détermine automatiquement la requête les paramètres correspondent aux colonnes de base de données sensibles (protégées avec Always Encrypted) et chiffre les valeurs de ces paramètres avant de transmettre les valeurs SQL Server ou de la base de données SQL Azure. De même, il déchiffre de manière transparente les données récupérées dans les colonnes de base de données chiffrées, qui figurent dans les résultats de la requête. Pour plus d’informations, visitez [Always Encrypted (moteur de base de données)](https://msdn.microsoft.com/library/mt163865.aspx#Anchor_7) et [toujours chiffré référence des API pour le pilote JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).  


## <a name="prerequisites"></a>Conditions préalables

- Configurez Always Encrypted dans votre base de données. Pour cela, vous devez mettre en service des clés Always Encrypted et configurer le chiffrement pour les colonnes de base de données sélectionnées. Si vous n’avez pas déjà une base de données dans laquelle est configuré Always Encrypted, suivez les instructions de [Prise en main d’Always Encrypted](https://msdn.microsoft.com/library/mt163865.aspx#Anchor_5).
- Assurez-vous que Microsoft JDBC Driver 6.0 (ou version ultérieure) pour SQL Server est installé sur votre ordinateur de développement. 
-   Téléchargez et installez les fichiers de stratégie Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction.  Veillez à lire le fichier Lisez-moi inclus dans le fichier zip pour obtenir les instructions d’installation et des informations pertinentes sur les éventuels problèmes d’importation/exportation.  
  
    -   Si vous utilisez sqljdbc41.jar, les fichiers de stratégie peuvent être téléchargés à partir de [téléchargement des fichiers de stratégie juridiction Java Cryptography Extension (JCE) Unlimited 7](http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html)  
  
    -   Si vous utilisez sqljdbc42.jar, les fichiers de stratégie peuvent être téléchargés à partir de [téléchargement des fichiers de stratégie juridiction Java Cryptography Extension (JCE) Unlimited 8](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html)   
    
## <a name="enabling-always-encrypted-for-application-queries"></a>Activation d’Always Encrypted pour les requêtes d’application  
Le moyen le plus simple pour activer le chiffrement des paramètres et le déchiffrement des résultats de requête ciblant des colonnes chiffrées, est en définissant la valeur de la **columnEncryptionSetting** mot clé de chaîne de connexion à ** Activé**.

Voici un exemple de chaîne de connexion qui active le chiffrement intégral dans le pilote JDBC :
  
```  
String connectionString = "jdbc:sqlserver://localhost;user=<user>;password=<password>;databaseName=<database>;columnEncryptionSetting=Enabled;"; 
SQLServerConnection connection = (SQLServerConnection) DriverManager.getConnection(connectionString);
     
```  
  
Et Voici un exemple équivalent à l’aide de l’objet SQLServerDataSource.  
  
```  
SQLServerDataSource ds = new SQLServerDataSource();  
ds.setServerName("localhost");
ds.setUser("<user>");
ds.setPassword("<password>");
ds.setDatabaseName("<database>");
ds.setColumnEncryptionSetting("Enabled");  
SQLServerConnection con = (SQLServerConnection) ds.getConnection(); 
```    

Always Encrypted peut également être activé pour les requêtes individuelles. Consultez le **contrôle Performance Impact d’Always Encrypted** section ci-dessous. Notez que l’activation d’Always Encrypted ne suffit pas à la réussite du chiffrement ou du déchiffrement. Vous devez également vérifier ce qui suit :
- L’application dispose des autorisations de base de données *VIEW ANY COLUMN MASTER KEY DEFINITION* et *VIEW ANY COLUMN ENCRYPTION KEY DEFINITION* qui sont nécessaires pour accéder aux métadonnées des clés Always Encrypted dans la base de données. Pour plus d’informations, consultez la [section « Autorisations » de la rubrique « Always Encrypted (moteur de base de données) »](https://msdn.microsoft.com/library/mt163865.aspx#Anchor_7).
- L’application peut accéder à la clé principale de colonne qui protège les clés de chiffrement de colonne, en chiffrant les colonnes de base de données interrogées. Notez que, pour utiliser le fournisseur de magasin de clés Java que vous devez fournir les informations d’identification supplémentaires dans la chaîne de connexion. Consultez **fournisseur de magasin de clés à l’aide Java** section pour plus d’informations.

### <a name="configuring-how-javasqltime-values-are-sent-to-the-server"></a>Configurer la façon dont les valeurs java.sql.Time sont envoyées au serveur

Le **sendTimeAsDatetime** propriété de connexion est utilisée pour configurer la façon dont la valeur java.sql.Time est envoyée au serveur. Lorsque sendTimeAsDatetime = false, l’heure d’envoi de la valeur en tant que type au moment de SQL Server et à quel moment sendTimeAsDatetime = true, l’heure d’envoi de la valeur en un type datetime. Notez que, lorsqu’une colonne time est chiffrée, la propriété sendTimeAsDatetime doit être false comme des colonnes chiffrées ne prennent pas en charge la conversion à partir de l’heure en datetime. Notez également que cette propriété est par la valeur true par défaut, donc lorsque vous utilisez les colonnes chiffrées, vous devrez affecter la valeur false. Sinon, le pilote génère en tant qu’exception. La classe SQLServerConnection possède deux méthodes, en commençant par la version 6.0 du pilote pour configurer la valeur de cette propriété par programmation :
 
* setSendTimeAsDatetime void publique (boolean sendTimeAsDateTimeValue)
* public boolean getSendTimeAsDatetime()

Pour plus d’informations sur cette propriété, visitez [java.sql.Time configurer comment les valeurs sont envoyées au serveur](https://msdn.microsoft.com/library/ff427224(v=sql.110).aspx). 

### <a name="configuring-how-string-values-are-sent-to-the-server"></a>Configurer comment les valeurs de chaîne sont envoyés au serveur

Le **sendStringParametersAsUnicode** propriété de connexion est utilisée pour configurer la façon dont les valeurs de chaîne sont envoyés à SQL Server. Si la valeur « trues », paramètres de chaîne est envoyée au serveur au format Unicode. Si la valeur « false », paramètres de chaîne est envoyée dans un format non Unicode, par exemple ASCII/MBCS au lieu d’Unicode. La valeur par défaut de cette propriété est « true ». Lorsque Always Encrypted est activé, et une colonne char/varchar/varchar(max) est chiffrée, la valeur de **sendStringParametersAsUnicode** doit avoir la valeur true (ou être considérée comme la valeur par défaut). Le pilote JDBC Microsoft pour SQL Server lève une exception lors de l’insertion de données à une colonne chiffrée char/varchar/varchar(max) si cette propriété est définie sur false. Pour plus d’informations sur cette propriété, consultez [définissant les propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md). 
  
## <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>Récupération et modification des données dans des colonnes chiffrées

Une fois que vous activez Always Encrypted pour les requêtes de l’application, vous pouvez utiliser l’API JDBC standard pour récupérer ou modifier des données dans les colonnes de la base de données chiffrée. En supposant que votre application possède les autorisations de base de données requise et pouvez accès la clé principale de colonne, le pilote JDBC Microsoft pour SQL Server chiffre tous les paramètres de requête qui ciblent des colonnes chiffrées et déchiffrement les données extraites des colonnes chiffrées types de données qui retournent des valeurs de texte en clair des types JDBC, correspondant au serveur SQL définie pour les colonnes dans le schéma de base de données.
Si Always Encrypted n’est pas activé, les requêtes ayant des paramètres qui ciblent des colonnes chiffrées échouent. Une requête peut toujours récupérer des données à partir de colonnes chiffrées, tant qu’aucun de ses paramètres ne cible des colonnes chiffrées. Toutefois, le pilote JDBC Microsoft pour SQL Server ne tente pas de déchiffrer les valeurs extraites des colonnes chiffrées et l’application reçoit des données chiffrées binaires (en tant que tableaux d’octets).

Le tableau ci-dessous récapitule le comportement des requêtes, selon qu’Always Encrypted est activé ou non :

|Caractéristique de la requête | Always Encrypted est activé et l’application peut accéder aux clés et à leurs métadonnées|Always Encrypted est activé et l’application ne peut pas accéder aux clés et à leurs métadonnées | Always Encrypted est désactivé|
|:---|:---|:---|:---|
| Requêtes avec des paramètres ciblant des colonnes chiffrées. | Des valeurs de paramètres sont chiffrées en toute transparence. | Erreur | Erreur|
| Requêtes qui récupèrent des données à partir de colonnes chiffrées, sans paramètres ciblant des colonnes chiffrées.| Les résultats de colonnes chiffrées sont déchiffrés de manière transparente. L’application reçoit des valeurs de texte en clair des types de données JDBC correspondant aux types SQL Server configurées pour les colonnes chiffrées. | Erreur | Les résultats des colonnes chiffrées ne sont pas déchiffrés. L’application reçoit des valeurs chiffrées sous la forme de tableaux d’octets (byte[]).
      
 
### <a name="inserting-and-retrieving-encrypted-data-examples"></a>Insertion et la récupération des exemples de données chiffrées 
Les exemples suivants illustrent la récupération et la modification de données dans des colonnes chiffrées. Ces exemples impliquent une table cible avec le schéma ci-dessous. Notez que les colonnes SSN et BirthDate sont chiffrées.

```
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
 
### <a name="inserting-data-example"></a>Exemple d’insertion de données

Cet exemple insère une ligne dans la table Patients. Notez les points suivants :
- L’exemple de code ne contient aucun élément spécifique au chiffrement. Le pilote JDBC Microsoft pour SQL Server détecte automatiquement et chiffre les paramètres qui ciblent des colonnes chiffrées. Le chiffrement est donc transparent pour l’application. 
- Les valeurs insérées dans des colonnes de la base de données, y compris les colonnes chiffrées, sont passés comme paramètres à l’aide de SQLServerPreparedStatement. Lors de l’utilisation de paramètres est facultative lors de l’envoi des valeurs pour les colonnes non chiffrées (même si, il est fortement recommandé, car elle contribue à empêcher l’injection SQL), il est nécessaire pour les valeurs ciblant des colonnes chiffrées. Si les valeurs insérées dans les colonnes chiffrées ont été passés en tant que littéraux incorporés dans l’instruction de requête, la requête échoue, car le pilote JDBC Microsoft pour SQL Server ne serait pas en mesure de déterminer les valeurs dans les colonnes chiffrées cibles, afin qu’il ne l’est pas chiffrer les valeurs. Par conséquent, le serveur les rejettera en les considérant comme incompatibles avec les colonnes chiffrées.
- Toutes les valeurs sont imprimées par le programme sera en texte brut, comme le pilote JDBC Microsoft pour SQL Server déchiffre de manière transparente les données récupérées à partir des colonnes chiffrées.
- Si vous effectuez une recherche à l’aide lorsque la clause, la valeur utilisée dans la clause WHERE doit être passée en tant que paramètre, afin que le pilote JDBC Microsoft pour SQL Server peut en toute transparence chiffrer avant de l’envoyer à la base de données. Dans l’exemple ci-dessous, notez que SSN est passé en tant que paramètre, mais le nom est passé en tant que littéral en tant que nom n’est pas chiffré.
- La méthode setter utilisée pour le paramètre ciblant la colonne SSN est setString(), qui est mappé avec le type de données SQL Server char/varchar. Si, pour ce paramètre, la méthode d’accesseur Set utilisée a été setNString(), qui est mappée vers nchar/nvarchar, la requête échoue, car Always Encrypted ne prend pas en charge les conversions de valeurs nchar/nvarchar chiffrées en valeurs char/varchar chiffrées.  

```
String connectionString = "jdbc:sqlserver://localhost:1433;databaseName=Clinic;user=sa;password=******;columnEncryptionSetting=Enabled;";
try  
{           
     Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
     try (Connection sourceConnection = DriverManager.getConnection(connectionString))  
     {                  
        String insertRecord="INSERT INTO [dbo].[Patients] VALUES (?, ?, ?, ?)";        
        try (PreparedStatement insertStatement = sourceConnection.prepareStatement(insertRecord))  
        {
            insertStatement.setString(1, "795-73-9838");  
            insertStatement.setString(2, "Catherine");   
            insertStatement.setString(3, "Abel");                   
            insertStatement.setDate(4, Date.valueOf("1996-09-10"));  
            insertStatement.executeUpdate();  
            System.out.println("1 record inserted.\n");  
        }         
     }  
}  
catch (Exception e)  
{  
    e.printStackTrace();  
}
```

### <a name="retrieving-plaintext-data-example"></a>Exemple de récupération de données en texte clair

L’exemple suivant montre le filtrage de données basé sur des valeurs chiffrées, ainsi que la récupération de données en texte clair à partir de colonnes chiffrées. Notez les points suivants :
- Valeur utilisée dans la clause WHERE pour filtrer sur la colonne SSN doit être passé en tant que paramètre, afin que le pilote JDBC Microsoft pour SQL Server peut chiffrer de manière transparente avant de l’envoyer à la base de données.
- Toutes les valeurs sont imprimées par le programme sera en texte brut, comme le pilote JDBC Microsoft pour SQL Server déchiffre de manière transparente les données récupérées à partir des colonnes SSN et BirthDate.

> [!NOTE]  
>  Les requêtes peuvent effectuer des comparaisons d’égalité sur des colonnes si elles sont chiffrées à l’aide du chiffrement déterministe. Pour plus d’informations, consultez la **chiffrement en sélectionnant déterministe ou aléatoire** section de la [Always Encrypted (moteur de base de données)](https://msdn.microsoft.com/library/mt163865.aspx) rubrique.  

```
String connectionString =  "jdbc:sqlserver://localhost:1433;databaseName=Clinic;user=sa;password=******;columnEncryptionSetting=Enabled;" ;
String filterRecord="SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN = ?;";  

try (PreparedStatement selectStatement = sourceConnection.prepareStatement(filterRecord))  
{  
    selectStatement.setString(1, "795-73-9838");  
    ResultSet rs = selectStatement.executeQuery();   
    while(rs.next()) 
    {  
    System.out.println("SSN: " +rs.getString("SSN") + 
    ", FirstName: " + rs.getString("FirstName") + 
    ", LastName:"+ rs.getString("LastName")+
     ", Date of Birth: " + rs.getString("BirthDate"));  
          }  
}
catch (Exception e)  
{  
    e.printStackTrace();  
}
```
  
### <a name="retrieving-encrypted-data-example"></a>Exemple de récupération de données chiffrées

Si Always Encrypted n’est pas activé, une requête peut toujours récupérer des données à partir de colonnes chiffrées, tant qu’aucun de ses paramètres ne ciblent des colonnes chiffrées.

L’exemple suivant illustre la récupération de données chiffrées binaires à partir de colonnes chiffrées. Notez les points suivants :

- Étant donné qu’Always Encrypted n’est pas toujours activé dans la chaîne de connexion, la requête retourne des valeurs SSN et BirthDate chiffrées sous la forme de tableaux d’octets (le programme convertit les valeurs en chaînes).
- Une requête qui récupère des données à partir de colonnes chiffrées lorsqu’Always Encrypted est désactivé peut avoir des paramètres, tant qu’aucun d’eux ne cible une colonne chiffrée. La requête ci-dessus filtre par nom (LastName), ce qui n’est pas chiffré dans la base de données. Si la requête filtre par SSN ou BirthDate, la requête échoue.

```
String connectionString  = "jdbc:sqlserver://localhost:1433;" + "databaseName=Clinic;user=sa;password=******";

String filterRecord="SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE LastName = ?;"; 
 
try (PreparedStatement selectStatement = sourceConnection.prepareStatement(filterRecord))  
{  
    selectStatement.setString(1, "Abel");  
    ResultSet rs = selectStatement.executeQuery();   
    while(rs.next())
    {  
        System.out.println("SSN: " + rs.getString("SSN") +
         ", FirstName: " + rs.getString("FirstName") + 
        ", LastName:"+ rs.getString("LastName")+ 
        ", Date of Birth: " + rs.getString("BirthDate"));  
    } 
}  
catch (Exception e)  
{  
    e.printStackTrace();  
}
```

### <a name="avoiding-common-problems-when-querying-encrypted-columns"></a>Éviter les problèmes courants lors de l’interrogation de colonnes chiffrées

Cette section décrit les catégories d’erreurs courantes lors de l’interrogation des colonnes chiffrées à partir des applications Java et quelques instructions sur la façon de les éviter.

### <a name="unsupported-data-type-conversion-errors"></a>Erreurs de Conversion de Type de données non pris en charge

Always Encrypted ne prend en charge que peu de conversions de types de données chiffrées. Consultez [Always Encrypted (moteur de base de données)](https://msdn.microsoft.com/library/mt163865.aspx) pour la liste détaillée des conversions de type pris en charge. Pour éviter les erreurs de conversion de types de données, procédez comme suit :

- vous utilisez les méthodes d’accesseur set appropriée lors du passage de valeurs pour les paramètres ciblant des colonnes chiffrées, afin que le type de données SQL Server du paramètre est exactement la même que le type de la colonne cible, ou une conversion du type de données SQL Server du paramètre type de la colonne est pris en charge à la cible. Notez que les nouvelles méthodes d’API ont été ajoutées aux classes SQLServerPreparedStatement et SQLServerCallableStatement de SQLServerResultSet pour passer des paramètres correspondant aux types de données SQL Server spécifiques. Par exemple, si une colonne n’est pas chiffrée, vous pouvez utiliser setTimestamp() méthode pour passer un paramètre à un datetime2 ou à une colonne datetime. Mais quand une colonne est chiffrée, vous devez utiliser la méthode exacte représentant le type de la colonne dans la base de données. Par exemple, utilisez setTimestamp() pour passer des valeurs à une colonne chiffrée datetime2 et setDateTime() permet de passer des valeurs à une colonne datetime chiffré. Consultez [toujours chiffré référence des API pour le pilote JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) pour une liste complète des nouvelles API. 
- La précision et l’échelle des paramètres ciblant les colonnes des types de données SQL Server decimal et numeric sont les mêmes que celles configurées pour la colonne cible. Notez que les nouvelles méthodes d’API ont été ajoutées aux classes SQLServerPreparedStatement et SQLServerCallableStatement de SQLServerResultSet pour accepter la précision et l’échelle en même temps que les valeurs de données pour les paramètres ou des colonnes représentant les types de données decimal et numeric. Consultez [toujours chiffré référence des API pour le pilote JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) pour une liste complète des API de nouveau/surchargé.  
- le fractions de seconde/échelle de précision des paramètres ciblant des colonnes de type datetime2, datetimeoffset ou types de données SQL Server n’est pas supérieure à celle de la colonne cible, dans les requêtes qui modifient les valeurs de la colonne cible. Notez que les nouvelles méthodes d’API ont été ajoutées aux classes SQLServerPreparedStatement et SQLServerCallableStatement de SQLServerResultSet pour accepter l’échelle de précision/en fractions de seconde, ainsi que les valeurs de paramètres représentant ces types de données. Consultez [toujours chiffré référence des API pour le pilote JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) pour une liste complète des API de nouveau/surchargé.   

### <a name="errors-due-to-incorrect-connection-properties"></a>Erreurs dues à des propriétés de connexion Incorrect
Cette section décrit comment configurer les paramètres de connexion correctement pour utiliser des données Always Encrypted. Types de données chiffrées prenant en charge limitée des conversions, les paramètres de connexion 'sendTimeAsDatetime' et 'sendStringParametersAsUnicode' nécessitent une configuration appropriée lors de l’utilisation des colonnes chiffrées. Assurez-vous que : 
- [sendTimeAsDatetime](https://msdn.microsoft.com/library/ff427224(v=sql.110).aspx) connexion est défini sur false lorsque vous insérez des données chiffrées des colonnes de temps. Pour plus d’informations, consultez « Comment les valeurs java.sql.Time sont envoyées au serveur de configuration ».
- [sendStringParametersAsUnicode](../../connect/jdbc/setting-the-connection-properties.md) connexion est défini sur true (ou est considérée comme la valeur par défaut) lors de l’insertion des données dans des colonnes de char/varchar/varchar(max) chiffrées. Pour plus d’informations, consultez « Comment les valeurs de chaîne sont envoyés au serveur de configuration ».

### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>Erreurs en raison de passer du texte brut au lieu des valeurs de chiffré

Les valeurs qui ciblent une colonne chiffrée doivent être chiffrées dans l’application. Toute tentative d’insertion, de modification ou de filtrage par une valeur en texte clair dans une colonne chiffrée entraîne une erreur similaire à celle-ci :


```
com.microsoft.sqlserver.jdbc.SQLServerException: Operand type clash: varchar is incompatible with varchar(8000) encrypted with (encryption_type = 'DETERMINISTIC', encryption_algorithm_name = 'AEAD_AES_256_CBC_HMAC_SHA_256', column_encryption_key_name = 'MyCEK', column_encryption_key_database_name = 'ae') collation_name = 'SQL_Latin1_General_CP1_CI_AS'
```

Pour éviter ces erreurs, procédez comme suit :
- Always Encrypted est activé pour les requêtes d’application ciblant des colonnes chiffrées (pour la chaîne de connexion ou d’une requête spécifique).
- vous utilisez des instructions préparées et paramètres à envoyer des données ciblant des colonnes chiffrées. L’exemple ci-dessous illustre une requête qui filtre incorrectement par une littéral ou d’une constante sur une colonne chiffrée (SSN), au lieu de passer de l’intérieur du littéral en tant que paramètre. Cette requête échoue.

```
ResultSet rs = connection.createStatement().executeQuery("SELECT * FROM Customers WHERE SSN='795-73-9838'");  
```

## <a name="working-with-column-master-key-stores"></a>Utilisation de magasins de clés principales de colonne
Pour chiffrer une valeur de paramètre ou déchiffrer les données dans les résultats de la requête, le pilote JDBC Microsoft pour SQL Server doit obtenir une clé de chiffrement de colonne qui est configurée pour la colonne cible. Les clés de chiffrement de colonne sont stockées sous forme chiffrée dans les métadonnées de la base de données. Chaque clé de chiffrement de colonne a une clé principale de colonne correspondante qui a été utilisée pour chiffrer la clé de chiffrement de colonne. Les métadonnées de la base de données ne stockent pas les clés principales de colonne. Elles contiennent uniquement des informations sur un magasin de clés contenant une clé principale de colonne et sur l’emplacement de cette clé dans le magasin.

Pour obtenir une valeur de texte en clair d’une clé de chiffrement de colonne, le pilote JDBC Microsoft pour SQL Server commence par obtenir les métadonnées relatives à la clé de chiffrement de colonne et la clé principale de colonne correspondante, puis il utilise les informations dans les métadonnées pour contacter la clé magasin, contenant la clé principale de colonne et pour déchiffrer la clé de chiffrement de colonne chiffrée. Le pilote JDBC Microsoft pour SQL Server communique avec un magasin de clés à l’aide d’un fournisseur de magasin de clés principales de colonne – qui est une instance d’une classe dérivé de **SQLServerColumnEncryptionKeyStoreProvider** classe.


### <a name="using-built-in-column-master-key-store-providers"></a>Utilisation des fournisseurs de magasin de clés principales de colonne intégrés
  
Le pilote JDBC Microsoft pour SQL Server est fourni avec les fournisseurs de magasins de clé principale de la colonne intégrés suivants. Notez que certaines de ces fournisseurs sont pré-inscrits avec des noms de fournisseurs spécifiques (utilisés pour rechercher le fournisseur) en fonction des informations d’identification supplémentaires ou de l’inscription explicite.

| Classe | Description | Nom de fournisseur (pour la recherche) |Pré-enregistré ?|
|:---|:---|:---|:---|
|**SQLServerColumnEncryptionAzureKeyVaultProvider**| Un fournisseur pour un magasin de clés pour le coffre de clés Azure.| AZURE_KEY_VAULT|Non|
|**SQLServerColumnEncryptionCertificateStoreProvider**| Un fournisseur pour le magasin de certificats Windows.|MSSQL_CERTIFICATE_STORE|Oui
|**SQLServerColumnEncryptionJavaKeyStoreProvider**| Un fournisseur pour le keystore Java|MSSQL_JAVA_KEYSTORE|Oui|

Pour les fournisseurs de magasins de clés pré-enregistré, vous n’avez pas besoin d’apporter des modifications de code d’application à utiliser ces fournisseurs, mais notez les points suivants :

- Vous (ou votre administrateur de base de données) devez vérifier que le nom du fournisseur (configuré dans les métadonnées de clé principale de colonne) est correct et que le chemin de la clé principale de colonne est valide pour un fournisseur donné. Il est recommandé de configurer les clés à l’aide d’outils tels que SQL Server Management Studio, qui génère automatiquement des noms de fournisseurs et des chemins de clés valides lors de l’émission de l’instruction CREATE COLUMN MASTER KEY (Transact-SQL).
- Vous devez vérifier que votre application peut accéder à la clé dans le magasin de clés. Pour cela, vous devrez peut-être accorder à votre application l’accès à la clé ou au magasin de clés (selon le magasin de clés) ou effectuer d’autres étapes de configuration spécifiques au magasin de clés. Par exemple, pour l’utilisation de la SQLServerColumnEncryptionJavaKeyStoreProvider, vous devez fournir l’emplacement et le mot de passe de combinaison de touches dans les propriétés de connexion. 

Tous ces fournisseurs de magasin de clés sont décrits plus en détail ci-dessous.
  
### <a name="using-azure-key-vault-provider"></a>Utilisation du fournisseur Azure Key Vault
Azure Key Vault est un outil est très pratique qui permet de stocker et de gérer des clés principales de colonne Always Encrypted, en particulier si vos applications sont hébergées dans Azure. Le pilote JDBC Microsoft pour SQL Server inclut un fournisseur intégré, SQLServerColumnEncryptionAzureKeyVaultProvider, pour les applications qui ont des clés stockées dans le coffre de clés Azure. Le nom de ce fournisseur est AZURE_KEY_VAULT. Pour pouvoir utiliser le fournisseur de magasins d’Azure Key Vault, un développeur d’applications a besoin créer l’archivage et les clés dans Azure et configurer l’application pour accéder aux clés. Pour plus d’informations sur la façon de configurer le coffre de clés et de créer la clé principale de colonne, reportez-vous à [Azure Key Vault – étape par étape pour plus d’informations sur la configuration de l’archivage de clé](https://blogs.technet.microsoft.com/kv/2015/06/02/azure-key-vault-step-by-step/) et [création des clés de principales de colonne dans le coffre de clés Azure](https://msdn.microsoft.com/library/mt723359.aspx#Anchor_2).  
  
Pour utiliser le coffre de clés Azure, les applications clientes doivent instancier le SQLServerColumnEncryptionAzureKeyVaultProvider et l’inscrire avec le pilote. L’authentification de délégués du pilote JDBC pour l’application via une interface appelée SQLServerKeyVaultAuthenticationCallback qui a une méthode pour récupérer un jeton d’accès du coffre de clés. Pour instancier le fournisseur de magasins de coffre de clés Azure, le développeur doit fournir une implémentation de la seule méthode appelée **getAccessToken** qui extrait le jeton d’accès de la clé stockée dans Azure Key Vault.  
  
Voici un exemple d’initialisation SQLServerKeyVaultAuthenticationCallback et SQLServerColumnEncryptionAzureKeyVaultProvider :  
  
```  
// String variables clientID and clientSecret hold the client id and client secret values respectively.  
  
ExecutorService service = Executors.newFixedThreadPool(10);  
SQLServerKeyVaultAuthenticationCallback authenticationCallback = new SQLServerKeyVaultAuthenticationCallback() {  
       @Override  
    public String getAccessToken(String authority, String resource, String scope) {  
        AuthenticationResult result = null;  
        try{  
                AuthenticationContext context = new AuthenticationContext(authority, false, service);  
            ClientCredential cred = new ClientCredential(clientID, clientSecret);  
  
            Future<AuthenticationResult> future = context.acquireToken(resource, cred, null);  
            result = future.get();  
        }  
        catch(Exception e){  
            e.printStackTrace();  
        }  
        return result.getAccessToken();  
    }  
};  
  
SQLServerColumnEncryptionAzureKeyVaultProvider akvProvider = new SQLServerColumnEncryptionAzureKeyVaultProvider(authenticationCallback, service);  
  
```

Une fois que l’application crée une instance de SQLServerColumnEncryptionAzureKeyVaultProvider, l’application doit inscrire l’instance dans le pilote JDBC Microsoft pour SQL Server à l’aide de la Méthode Sqlserverconnection.registercolumnencryptionkeystoreproviders (). Il est fortement recommandé, l’instance est inscrite en utilisant le nom de recherche par défaut, AZURE_KEY_VAULT, ce qui peut être obtenu en appelant l’API SQLServerColumnEncryptionAzureKeyVaultProvider.getName(). En utilisant le nom par défaut, vous permettra d’utiliser les outils, tels que SQL Server Management Studio ou PowerShell, à configurer et gérer des clés Always Encrypted (les outils permet d’utiliser le nom par défaut pour générer l’objet de métadonnées pour la clé principale de colonne). L’exemple ci-dessous illustre l’inscription du fournisseur Azure Key Vault. Pour plus d’informations sur la méthode sqlserverconnection.registercolumnencryptionkeystoreproviders (), consultez [toujours chiffré référence des API pour le pilote JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md). 

```
Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();   
keyStoreMap.put(akvProvider.getName(), akvProvider);   
SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);   
```
  
> [!IMPORTANT]  
>  L’implémentation de coffre de clés Azure du pilote JDBC présente des dépendances sur ces bibliothèques (à partir de GitHub) :  
>   
>  [Kit de développement logiciel Azure pour java](https://github.com/Azure/azure-sdk-for-java)  
>   
>  [bibliothèques Azure bibliothèque Active Directory pour java](https://github.com/AzureAD/azure-activedirectory-library-for-java)  
  
### <a name="using-windows-certificate-store-provider"></a>À l’aide du fournisseur de magasin de certificats Windows
Le SQLServerColumnEncryptionCertificateStoreProvider peut servir à stocker des clés principales de colonne dans le magasin de certificats Windows. Pour créer la clé principale de colonne et le chiffrement de colonne clées définitions dans la base de données, utilisez l’Assistant chiffrement intégral de SQL Server Management Studio (SSMS) ou autres outils pris en charge. L’Assistant même peut être utilisé pour générer un certificat auto-signé dans le magasin de certificats Windows qui est utilisé comme clé principale de colonne pour les données toujours chiffrées. Pour plus d’informations sur la clé principale de colonne et de chiffrement de colonne clée syntaxe T-SQL visiter [CREATE COLUMN MASTER KEY](https://msdn.microsoft.com/library/mt146393.aspx) et [CREATE COLUMN ENCRPTION KEY](https://msdn.microsoft.com/library/mt146372.aspx) respectivement.

Le nom de la SQLServerColumnEncryptionCertificateStoreProvider est « MSSQL_CERTIFICATE_STORE » et peut être interrogé par les API getName() de l’objet fournisseur. Il est automatiquement enregistré par le pilote et peut être utilisé en toute transparence sans aucune modification de l’application.

> [!IMPORTANT]  
>  L’implémentation SQLServerColumnEncryptionCertificateStoreProvider du pilote JDBC est disponible avec les systèmes d’exploitation Windows uniquement et a une dépendance sur le fichier sqljdbc_auth.dll qui est disponible dans le package de pilotes.  Pour utiliser ce fournisseur, copiez le fichier sqljdbc_auth.dll dans un répertoire sur le chemin d’accès de système de Windows sur l’ordinateur où est installé le pilote JDBC. Vous pouvez également définir la propriété système java.libary.path afin de spécifier le répertoire du fichier sqljdbc_auth.dll. Si vous exécutez une machine virtuelle Java (JVM) 32 bits, utilisez le fichier sqljdbc_auth.dll dans le dossier x86, même si la version du système d'exploitation est x64. Si vous exécutez une machine virtuelle Java (JVM) 64 bits sur un processeur x64, utilisez le fichier sqljdbc_auth.dll dans le dossier x64. Par exemple, si vous utilisez la machine virtuelle Java 32 bits et le pilote JDBC est installé dans le répertoire par défaut, vous pouvez spécifier l’emplacement de la DLL à l’aide de l’argument suivant de la machine virtuelle (VM) au démarrage de l’application Java :  
`-Djava.library.path=C:\Microsoft JDBC Driver <version> for SQL Server\sqljdbc_<version>\enu\auth\x86`
        
### <a name="using-java-key-store-provider"></a>À l’aide du fournisseur de magasin de clés de Java  
Le pilote JDBC est fourni avec une clé de génération de stocker l’implémentation du fournisseur pour le magasin de clés de Java. Le pilote instancie automatiquement et enregistre le fournisseur de magasin de clés Java, si le **keyStoreAuthentication** propriété de chaîne de connexion est présente dans la chaîne de connexion et a la valeur « JavaKeyStorePassword » (, consultez plus de détails ci-dessous). Le nom du fournisseur de magasin de clés de Java est MSSQL_JAVA_KEYSTORE. Ce nom peut également être interrogé par l’API SQLServerColumnEncryptionJavaKeyStoreProvider.getName(). 

Trois nouveaux mots clés de chaîne connexion sont introduites pour permettre à une client de l’application spécifier de façon déclarative les informations d’identification que le pilote doit s’authentifier auprès du magasin de clés de Java. Le pilote initialise le fournisseur, selon les valeurs des trois propriétés suivantes de la chaîne de connexion pour les connexions spécifiques. 
  
 **keyStoreAuthentication :** identifie le magasin de clés à utiliser. Avec le pilote Microsoft JDBC 6.0 pour SQL Server, vous pouvez authentifier pour le magasin de clés Java uniquement par le biais de cette propriété. Pour le magasin de clés Java, la valeur de cette propriété doit être « JavaKeyStorePassword ».   
  
 **keyStoreLocation :** le chemin d’accès au fichier keystore Java qui stocke la clé principale de colonne. Notez que le chemin d’accès inclut le nom de fichier du magasin de clés.  
  
 **keyStoreSecret :** le secret/mot de passe à utiliser pour le keystore ainsi que pour la clé. Notez que pour utiliser le magasin de clés le keystore Java et le mot de passe de clé doit être identiques.  

Voici un exemple sur la fourniture de ces informations d’identification dans la chaîne de connexion :

    String connectionString = "jdbc:sqlserver://localhost;user=<user>;password=<password>;columnEncryptionSetting=Enabled;keyStoreAuthentication=JavaKeyStorePassword;keyStoreLocation=<path_to_the_keystore_file>;keyStoreSecret=<keystore_key_password>";
    
Ces paramètres peuvent également être set/get à l’aide de l’objet SQLServerDataSource. Consultez [toujours chiffré référence des API pour le pilote JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) pour plus d’informations.     
  
Le pilote JDBC instancie automatiquement le SQLServerColumnEncryptionJavaKeyStoreProvider lorsque ces informations d’identification sont présentes dans les propriétés de connexion. 
  
### <a name="creating-a-column-master-key-for-the-java-key-store"></a>Création d’une clé principale de colonne pour le magasin de clés de Java
Le SQLServerColumnEncryptionJavaKeyStoreProvider peut être utilisé avec les types de magasins de clés JKS ou PKCS12. Pour créer ou importer une clé à utiliser avec ce fournisseur utiliser Java [keytool](http://docs.oracle.com/javase/7/docs/technotes/tools/windows/keytool.html) utilitaire. Notez que la clé doit avoir le même mot de passe en tant que le magasin de clés. Voici un exemple montrant comment créer une clé publique et sa clé privée associée à l’aide de l’utilitaire keytool.

    keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.jks -storepass mypassword -validity 360 -keysize 2048 -storetype jks    

Cette commande crée une clé publique et il est encapsulé dans un X.509 auto-signé certificat qui est ensuite stockée dans le magasin de clés 'keystore.jks', ainsi que sa clé privée associée. Cette entrée dans le magasin de clés est identifiée par l’alias 'AlwaysEncryptedKey'. 

Voici un exemple de ce même en utilisant un storetype PKCS12. 

    keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.pfx -storepass mypassword -validity 360 -keysize 2048 -storetype pkcs12 -keypass mypassword   

Notez que si le magasin de clés est de type PKCS12 le keytool ne demande pas de mot de passe de clé et le mot de passe de clé doit être fourni avec l’option de - keypass en tant que le SQLServerColumnEncryptionJavaKeyStoreProvider nécessite que le magasin de clés et la clé possèdent le même mot de passe.

Vous pouvez également exporter un certificat à partir du magasin de certificats Windows au format .pfx et l’utiliser avec le SQLServerColumnEncryptionJavaKeyStoreProvider. Le certificat exporté ne peut également être importé dans le magasin de clés Java comme un type de magasin de clés JKS. 

Après avoir créé l’entrée keytool, vous devrez créer les métadonnées de clé principale de colonne dans la base de données nécessite le nom de fournisseur de magasin de clés et le chemin de clé. Pour plus d’informations sur la création des métadonnées de clé principale de colonne, visitez [CREATE COLUMN MASTER KEY](https://msdn.microsoft.com/library/mt146393.aspx). Pour SQLServerColumnEncryptionJavaKeyStoreProvider, le chemin de clé est simplement l’alias de la clé. Et le nom de la SQLServerColumnEncryptionJavaKeyStoreProvider 'MSSQL_JAVA_KEYSTORE'. Vous pouvez également interroger ce nom à l’aide de l’API publique de getName() de la classe SQLServerColumnEncryptionJavaKeyStoreProvider. 

La syntaxe T-SQL pour la création de la clé principale de colonne est la suivante :

```  
CREATE COLUMN MASTER KEY [<CMK_name>]  
WITH  
(  
    KEY_STORE_PROVIDER_NAME = N'MSSQL_JAVA_KEYSTORE',  
    KEY_PATH = N'<key_alias>'  
)  
```  

Pour le 'AlwaysEncryptedKey' créé ci-dessus, la définition de clé principale de colonne serait :

```  
CREATE COLUMN MASTER KEY [MyCMK]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'MSSQL_JAVA_KEYSTORE',
    KEY_PATH = N'AlwaysEncryptedKey'
)
```  
    
> [!NOTE]  
>  Intégré dans SQL Server Studio fonctionnalités de gestion ne peut pas créer colonne définitions de la clé principale pour le magasin de clés de Java pour lequel vous devez utiliser la commande T-SQL.  
  
### <a name="creating-a-column-encryption-key-for-the-java-key-store"></a>Création d’une clé de chiffrement de colonne pour le magasin de clés de Java
Notez que SQL Server management Studio ou tout autre outil ne peut pas être utilisé pour créer des clés de chiffrement à l’aide des clés principales de colonne dans le magasin de clés Java de colonne. L’application cliente doit créer la clé de chiffrement de colonne par programmation à l’aide de la classe SQLServerColumnEncryptionJavaKeyStoreProvider. Pour plus d’informations consultez la section « À l’aide de colonne clé principale de fournisseurs de magasins pour la configuration de la programmation clé ». 

  
### <a name="implementing-a-custom-column-master-key-store-provider"></a>Implémentation d’un fournisseur de magasin de clés principales de colonne personnalisé
Si vous souhaitez stocker des clés principales de colonne dans un magasin de clés n’est pas pris en charge par un fournisseur existant, vous pouvez implémenter un fournisseur personnalisé en étendant la classe SQLServerColumnEncryptionKeyStoreProvider et l’inscription du fournisseur à l’aide de la Méthode Sqlserverconnection.registercolumnencryptionkeystoreproviders ().
  
```  
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
  
```  
SQLServerColumnEncryptionKeyStoreProvider storeProvider = new MyCustomKeyStore();  
Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();  
keyStoreMap.put(storeProvider.getName(), storeProvider);  
SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);  
  
```  
  
## <a name="using-column-master-key-store-providers-for-programmatic-key-provisioning"></a>Utilisation des fournisseurs de magasin de clés principales de colonne pour la mise en service des clés par programmation

Pour accéder à des colonnes chiffrées, le pilote JDBC Microsoft pour SQL Server en toute transparence par la recherche et appelle le fournisseur de magasins de clé principale de colonne de droite pour déchiffrer les clés de chiffrement de colonne. En règle générale, un code d’application normal n’appelle pas directement les fournisseurs de magasin de clés principales de colonne. Vous pouvez, toutefois, instancier et appeler explicitement un fournisseur afin de mettre en service et de gérer par programmation les clés Always Encrypted, et ce, dans le but de générer une clé de chiffrement de colonne chiffrée et de déchiffrer une clé de chiffrement de colonne (par exemple, dans le cadre d’une permutation de clé principale de colonne). Pour plus d’informations, consultez [Vue d’ensemble de la gestion des clés pour Always Encrypted](https://msdn.microsoft.com/library/mt708953.aspx).
Notez que l’implémentation de vos propres outils de gestion de clés peut n’être nécessaire que si vous utilisez un fournisseur de magasin de clés personnalisé. Lorsque vous utilisez des clés stockées dans le magasin de certificats Windows ou dans le coffre de clés Azure, vous pouvez utiliser des outils existants, tels que SQL Server Management Studio ou PowerShell, pour gérer et configurer des clés. Lorsque vous utilisez des clés stockées dans le magasin de clés Java, vous devez configurer par programmation les clés. L’exemple ci-dessous, illustre l’utilisation de la classe de SQLServerColumnEncryptionJavaKeyStoreProvider pour chiffrer la clé avec une clé stockée dans le magasin de clés de Java.

```  
import java.sql.*;
import javax.xml.bind.DatatypeConverter;
import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionJavaKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerException;

/**
 * This program demonstrates how to create a column encryption key programatically for the Java Key Store.
 */
public class AlwaysEncrypted
{
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
     * Name of the encryption algorithm used to encrypt the value of
     * the column encryption key. The algorithm for the system providers must be RSA_OAEP.
     */
    private static String algorithm = "RSA_OAEP";

    public static void main(String[] args)
    {
        String connectionString = GetConnectionString();
        try
        {
            // Note: if you are not using try-with-resources statements (as here),
            // you must remember to call close() on any Connection, Statement,
            // ResultSet objects that you create.

            // Open a connection to the database.
            Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");
            try (Connection sourceConnection = DriverManager.getConnection(connectionString))
            {
                // Instantiate the Java Key Store provider.
                SQLServerColumnEncryptionKeyStoreProvider storeProvider = 
                        new SQLServerColumnEncryptionJavaKeyStoreProvider(
                                keyStoreLocation,
                                keyStoreSecret);

                byte [] encryptedCEK=getEncryptedCEK(storeProvider);

                /**
                 * Create column encryption key 
                 * For more details on the syntax refer: 
                 * https://msdn.microsoft.com/library/mt146372.aspx
                 * Encrypted column encryption key first needs to be converted into varbinary_literal from bytes, 
                 * for which DatatypeConverter.printHexBinary is used
                 */
                String createCEKSQL = "CREATE COLUMN ENCRYPTION KEY " 
                        + columnEncryptionKey
                        + " WITH VALUES ( "
                        + " COLUMN_MASTER_KEY = " 
                        + columnMasterKeyName
                        + " , ALGORITHM =  '" 
                        + algorithm
                        + "' , ENCRYPTED_VALUE =  0x" 
                        + DatatypeConverter.printHexBinary(encryptedCEK)
                        + " ) ";

                try (Statement cekStatement = sourceConnection.createStatement())
                {
                    cekStatement.executeUpdate(createCEKSQL);
                    System.out.println("Column encryption key created with name : " + columnEncryptionKey);
                }
            }
        }
        catch (Exception e)
        {
            // Handle any errors that may have occurred.
            e.printStackTrace();
        }
    }

    // To avoid storing the sourceConnection String in your code,
    // you can retrieve it from a configuration file.
    private static String GetConnectionString()
    {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://localhost:1433;" +
                "databaseName=ae2;user=sa;password=********;";

        return connectionUrl;
    }

    private static byte[] getEncryptedCEK(SQLServerColumnEncryptionKeyStoreProvider storeProvider) throws SQLServerException
    {
        /**
         * Following arguments needed by  SQLServerColumnEncryptionJavaKeyStoreProvider
         * 1) keyStoreLocation : 
         *      Path where keystore is located, including the keystore file name. 
         * 2) keyStoreSecret : 
         *      Password of the keystore and the key.  
         */
        String plainTextKey = "You need to give your plain text";

        // plainTextKey has to be 32 bytes with current algorithm supported
        byte[] plainCEK = plainTextKey.getBytes();

        // This will give us encrypted column encryption key in bytes
        byte[] encryptedCEK = storeProvider.encryptColumnEncryptionKey(
                keyAlias,
                algorithm,
                plainCEK);

        return encryptedCEK;
    }
}

```  
  
## <a name="force-encryption-on-input-parameters"></a>Forcer le chiffrement sur les paramètres d’entrée
  
La fonctionnalité de forcer le chiffrement applique le chiffrement d’un paramètre lors de l’utilisation de Always Encrypted. Si forcer le chiffrement est utilisé et que SQL Server informe le pilote que le paramètre ne doit pas être chiffré, la requête en utilisant le paramètre échoue. Cette propriété fournit une protection supplémentaire contre les attaques au niveau de la sécurité qui impliquent un serveur SQL Server compromis fournissant des métadonnées de chiffrement incorrectes au client, ce qui peut entraîner la divulgation de données. Les méthodes des classes SQLServerPreparedStatement et SQLServerCallableStatement ainsi que la mise à jour ensemble *\* méthodes de la classe SQLServerResultSet sont surchargées afin d’accepter un argument booléen pour spécifier le paramètre de chiffrement de force. Si la valeur de cet argument est false, le pilote ne force pas le chiffrement sur les paramètres. Si forcer le chiffrement est défini sur true, la requête paramètre est uniquement envoyé si la colonne de destination est chiffrée et chiffrement intégral est activé sur la connexion ou l’instruction. Cela fournit une couche supplémentaire de sécurité, d’assurer qu’aucune donnée est par erreur envoyée à SQL Server en tant que texte brut lorsqu’elle est censée être chiffrée.  
  
 Pour plus d’informations sur les méthodes SQLServerPreparedStatement et SQLServerCallableStatement qui sont surchargées avec le paramètre de chiffrement de force, consultez [toujours chiffré référence des API pour le pilote JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)  

## <a name="controlling-performance-impact-of-always-encrypted"></a>Contrôle de l’impact d’Always Encrypted sur les performances

Étant donné qu’Always Encrypted est une technologie côté client, la dégradation des performances s’observe côté client, et non dans la base de données. Outre les opérations de chiffrement et de déchiffrement, les autres sources de dégradation des performances côté client sont les suivantes :
- Allers-retours supplémentaires vers la base de données pour récupérer des métadonnées pour les paramètres de requête.
- Appels au magasin de clés principales de colonne pour accéder à une clé principale de colonne.

Cette section décrit les optimisations des performances intégrés dans Microsoft JDBC Driver pour SQL Server et comment vous pouvez contrôler l’impact de ces deux facteurs sur les performances.

### <a name="controlling-round-trips-to-retrieve-metadata-for-query-parameters"></a>Contrôle des allers-retours vers la base de données en vue de la récupération des métadonnées pour les paramètres de requête

Si Always Encrypted est activé pour une connexion, par défaut, le pilote JDBC Microsoft pour SQL Server appelle [sys.sp_describe_parameter_encryption](https://msdn.microsoft.com/library/mt631693.aspx?f=255&MSPPError=-2147217396) pour chaque requête paramétrable, en passant l’instruction de requête (sans les valeurs de paramètre) à SQL Server. [Sys.sp_describe_parameter_encryption](https://msdn.microsoft.com/library/mt631693.aspx?f=255&MSPPError=-2147217396) analyse l’instruction de requête pour savoir si des paramètres doivent être chiffrées, et par conséquent, pour chacun de ces, elle retourne les informations relatives au chiffrement qui permettant de Microsoft JDBC Driver pour SQL Server pour chiffrer les valeurs de paramètre. Ce comportement garantit un haut niveau de transparence à l’application cliente. L’application (et le développeur d’applications) n’a pas besoin de connaître les requêtes qui accèdent à des colonnes chiffrées, tant que les valeurs ciblant des colonnes chiffrées sont passées au pilote JDBC Microsoft pour SQL Server en tant que paramètres.


#### <a name="setting-always-encrypted-at-the-query-level"></a>Configuration d’Always Encrypted au niveau de la requête

Pour contrôler l’impact sur les performances de la récupération des métadonnées de chiffrement pour les requêtes paramétrables, vous pouvez activer Always Encrypted pour chaque requête, au lieu de le configurer pour la connexion. De cette façon, sys.sp_describe_parameter_encryption est appelé uniquement pour les requêtes dont les paramètres ciblent des colonnes chiffrées. Notez toutefois que de cette façon, vous réduisez la transparence du chiffrement. Si vous modifiez les propriétés de chiffrement de vos colonnes de base de données, vous devrez modifier le code de votre application pour l’aligner sur les modifications du schéma.


Pour contrôler le comportement d’Always Encrypted des requêtes individuelles, vous devez configurer les objets de l’instruction individuelle en passant un Enum, SQLServerStatementColumnEncryptionSetting, qui spécifie comment les données sont envoyées et reçues lors de la lecture et en écriture colonnes chiffrées pour cette instruction spécifique. Voici quelques conseils utiles :
- Si la plupart des requêtes qu’une application cliente envoie via une connexion de base de données accèdent à des colonnes chiffrées :
    - La valeur du mot-clé de chaîne de connexion columnEncryptionSetting activé.
    - Définissez SQLServerStatementColumnEncryptionSetting.Disabled pour les requêtes qui n’accèdent pas à toutes les colonnes chiffrées. Cela désactive à la fois l’appel de sys.sp_describe_parameter_encryption et la tentative de déchiffrement des valeurs du jeu de résultats.
    - Définissez SQLServerStatementColumnEncryptionSetting.ResultSet pour les requêtes qui n’ont pas aucun paramètre exigeant un chiffrement, mais qui récupèrent des données des colonnes chiffrées. Cela désactive l’appel de sys.sp_describe_parameter_encryption et le chiffrement des paramètres. La requête est alors en mesure de déchiffrer les résultats des colonnes de chiffrement.
- Si la plupart des requêtes qu’une application cliente envoie via une connexion de base de données n’accèdent pas à des colonnes chiffrées :
    - Définissez le mot-clé de chaîne de connexion columnEncryptionSetting sur désactivé.
    - Définissez SQLServerStatementColumnEncryptionSetting.Enabled pour les requêtes qui ont des paramètres qui doivent être chiffrés. Cela active à la fois l’appel de sys.sp_describe_parameter_encryption et le déchiffrement des résultats de requête récupérés à partir des colonnes chiffrées.
    - Définissez SQLServerStatementColumnEncryptionSetting.ResultSet pour les requêtes qui n’ont pas de n’importe quel paramètre exigeant un chiffrement, mais récupèrent des données des colonnes chiffrées. Cela désactive l’appel de sys.sp_describe_parameter_encryption et le chiffrement des paramètres. La requête est alors en mesure de déchiffrer les résultats des colonnes de chiffrement.

Notez que les paramètres SQLServerStatementColumnEncryptionSetting ne peut pas être utilisés pour contourner le chiffrement et accéder aux données en texte brut. Pour plus d’informations sur la façon de configurer le chiffrement de colonne dans une instruction, consultez [toujours chiffré référence des API pour le pilote JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).  

Dans l’exemple ci-dessous, Always Encrypted est désactivé pour la connexion de base de données. La requête envoyée par l’application comprend un paramètre qui cible la colonne LastName qui n’est pas chiffrée. La requête récupère les données des colonnes SSN et BirthDate qui sont toutes deux chiffrées. Dans ce cas, il n’est pas nécessaire d’appeler sys.sp_describe_parameter_encryption pour récupérer les métadonnées de chiffrement. Toutefois, le déchiffrement des résultats de requête doit être activé, afin que l’application puisse recevoir des valeurs de texte en clair à partir des deux colonnes chiffrées. Paramètre de SQLServerStatementColumnEncryptionSetting.ResultSet est utilisé pour garantir que.

```
// Assumes the same table definition as in Section "Retrieving and modifying data in encrypted columns"
// where only SSN and BirthDate columns are encrypted in the database.
String connectionUrl = "jdbc:sqlserver://localhost;databaseName=ae;user=sa;password=******;"
        + "keyStoreAuthentication=JavaKeyStorePassword;"
        + "keyStoreLocation=" + keyStoreLocation + ";"
        + "keyStoreSecret=******;";
SQLServerConnection connection = (SQLServerConnection) DriverManager.getConnection(connectionString);

String filterRecord="SELECT FirstName, LastName, SSN, BirthDate FROM " + tblName + " WHERE LastName = ?";  
PreparedStatement selectStatement = connection.prepareStatement(
        filterRecord, 
        ResultSet.TYPE_FORWARD_ONLY, 
        ResultSet.CONCUR_READ_ONLY, 
        connection.getHoldability(), 
        SQLServerStatementColumnEncryptionSetting.ResultSetOnly);
selectStatement.setString(1, "Abel");  
ResultSet rs = selectStatement.executeQuery();  
while(rs.next()) {  
    System.out.println("First name: " + rs.getString("FirstName"));  
    System.out.println("Last name: " + rs.getString("LastName"));  
    System.out.println("SSN: " + rs.getString("SSN"));  
    System.out.println("Date of Birth: " + rs.getDate("BirthDate"));  
}  
rs.close();
selectStatement.close();
connection.close();
```


### <a name="column-encryption-key-caching"></a>Mise en cache des clés de chiffrement de colonne

Pour réduire le nombre d’appels à un magasin de clés principales de colonne pour déchiffrer les clés de chiffrement de colonne, le pilote JDBC Microsoft pour SQL Server met en cache les clés de chiffrement de colonne de texte en clair dans la mémoire. Après avoir reçu la valeur de clé de chiffrement de colonne chiffrée à partir des métadonnées de la base de données, le pilote tente d’abord de trouver la clé de chiffrement de colonne en texte en clair qui correspond à la valeur de clé chiffrée. Le pilote appelle le magasin de clés qui contient la clé principale de colonne uniquement s’il ne peut pas trouver la valeur de clé de chiffrement de colonne chiffrée dans le cache.

Vous pouvez configurer une valeur de durée de vie pour les entrées de clé de chiffrement de colonne dans le cache à l’aide de l’API, setColumnEncryptionKeyCacheTtl(), dans la classe SQLServerConnection. La valeur de durée de vie par défaut pour les entrées de clé de chiffrement de colonne dans le cache est de 2 heures. Pour désactiver la mise en cache utilisent la valeur 0. Pour définir toute utilisation de la valeur de durée de vie de l’API suivante :
    
    SQLServerConnection.setColumnEncryptionKeyCacheTtl (int columnEncryptionKeyCacheTTL, TimeUnit unit)
   
Par exemple, pour définir une valeur de durée de vie de 10 minutes, utilisez :
    
    SQLServerConnection.setColumnEncryptionKeyCacheTtl (10, TimeUnit.MINUTES)

Notez que seuls des jours, heures, MINUTES ou secondes sont pris en charge en tant que l’unité de temps.  


## <a name="copying-encrypted-data-using-sqlserverbulkcopy"></a>Copie de données chiffrées à l’aide de SQLServerBulkCopy

Avec SQLServerBulkCopy, vous pouvez copier des données, qui sont déjà chiffrées et stockées dans une table, à une autre table, sans déchiffrage des données. Pour cela :

- Vérifiez que la configuration du chiffrement de la table cible est identique à celle de la table source. Les deux tables doivent avoir les mêmes colonnes chiffrées, et ces colonnes doivent être chiffrées à l’aide des mêmes types et des mêmes clés de chiffrement. Remarque : Si les colonnes cibles sont chiffrées différemment de la colonne source correspondante, vous ne pourrez pas déchiffrer les données de la table cible après les avoir copiées. Les données seront endommagées.
- Configurez les deux connexions de base de données, c’est-à-dire, celle vers la table source et celle vers la table cible, sans activer Always Encrypted. 
- Définissez l’option allowEncryptedValueModifications. Consultez [à l’aide de copie en bloc avec le pilote JDBC](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md) pour plus d’informations.
 
Remarque : Faites attention lorsque vous spécifiez AllowEncryptedValueModifications, car cela peut endommager la base de données, car le pilote JDBC Microsoft pour SQL Server ne vérifie pas si les données sont chiffrées en effet, ou si elle est correctement chiffrée à l’aide de la même chiffrement type, algorithme et clé que la colonne cible.

## <a name="see-also"></a>Voir aussi  
 [Always Encrypted (moteur de base de données)](https://msdn.microsoft.com/library/mt163865.aspx)  
  
  

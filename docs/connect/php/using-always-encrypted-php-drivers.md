---
title: Utilisation d’Always Encrypted avec Microsoft Drivers for PHP for SQL Server | Microsoft Docs
ms.date: 01/08/2018
ms.prod: sql
ms.prod_service: connectivity
ms.suite: sql
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
manager: mbarwin
ms.openlocfilehash: 12f0427b4ff23452f244c830c9116913dfb03968
ms.sourcegitcommit: c37da15581fb34250d426a8d661f6d0d64f9b54c
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39174966"
---
# <a name="using-always-encrypted-with-the-php-drivers-for-sql-server"></a>Utilisation d’Always Encrypted avec Microsoft Drivers for PHP for SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

## <a name="applicable-to"></a>Applicable à
 -   Microsoft Drivers 5.2 for PHP for SQL Server
 
## <a name="introduction"></a>Introduction

Cet article fournit des informations sur la façon de développer des applications PHP avec [Always Encrypted (moteur de base de données)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) et [pilotes PHP pour SQL Server](../../connect/php/Microsoft-php-driver-for-sql-server.md).

Always Encrypted permet aux applications clientes de chiffrer des données sensibles et de ne jamais révéler les données ou les clés de chiffrement à SQL Server ou Azure SQL Database. Un pilote avec Always Encrypted, tels que le pilote ODBC pour SQL Server, en toute transparence chiffre et déchiffre les données sensibles dans l’application cliente. Le pilote détermine automatiquement les paramètres de requêtes qui correspondent aux colonnes de base de données sensibles (protégées avec Always Encrypted) et chiffre les valeurs de ces paramètres avant de transmettre les données à SQL Server ou Azure SQL Database. De même, il déchiffre de manière transparente les données récupérées dans les colonnes de base de données chiffrées, qui figurent dans les résultats de la requête. Pour plus d’informations, consultez [Always Encrypted (moteur de base de données)](../../relational-databases/security/encryption/always-encrypted-database-engine.md). Les pilotes PHP pour SQL Server utilisent le pilote ODBC pour SQL Server chiffrer les données sensibles.

## <a name="prerequisites"></a>Conditions préalables requises

 -   Configurez Always Encrypted dans votre base de données. Pour cela, vous devez mettre en service des clés Always Encrypted et configurer le chiffrement pour les colonnes de base de données sélectionnées. Si vous n’avez pas déjà une base de données dans laquelle est configuré Always Encrypted, suivez les instructions de [Prise en main d’Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md#getting-started-with-always-encrypted). En particulier, votre base de données doit contenir les définitions de métadonnées pour une clé principale de colonne (CMK), une clé de chiffrement de colonne (CEK) et une table contenant une ou plusieurs colonnes chiffrées à l’aide de cette clé CEK.
 -   Assurez-vous que le pilote ODBC pour SQL Server version 17 ou ultérieure est installé sur votre ordinateur de développement. Pour plus d’informations, consultez [ODBC Driver for SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md).

## <a name="enabling-always-encrypted-in-a-php-application"></a>Activer le chiffrement intégral dans une Application PHP

Le moyen le plus simple d’activer le chiffrement des paramètres ciblant des colonnes chiffrées, et le déchiffrement des résultats de requête, est de définir la valeur du mot clé de chaîne de connexion `ColumnEncryption` sur `Enabled`. Voici quelques exemples de l’activation de Always Encrypted dans les pilotes SQLSRV et PDO_SQLSRV :

SQLSRV :
```
$connectionInfo = array("Database"=>$databaseName, "UID"=>$uid, "PWD"=>$pwd, "ColumnEncryption"=>"Enabled");
$conn = sqlsrv_connect($server, $connectionInfo);
```

PDO_SQLSRV :
```
$connectionInfo = "Database = $databaseName; ColumnEncryption = Enabled;";
$conn = new PDO("sqlsrv:server = $server; $connectionInfo", $uid, $pwd);
```

Activation d’Always Encrypted n’est pas suffisant pour le chiffrement ou déchiffrement réussisse. Vous devez également vous assurer que :
 -   L’application dispose des autorisations de base de données VIEW ANY COLUMN MASTER KEY DEFINITION et VIEW ANY COLUMN ENCRYPTION KEY DEFINITION qui sont nécessaires pour accéder aux métadonnées des clés Always Encrypted dans la base de données. Pour plus d’informations, consultez [autorisation de base de données](../../relational-databases/security/encryption/always-encrypted-database-engine.md#database-permissions).
 -   L’application peut accéder à la clé principale de colonne qui protège les clés cek pour les colonnes chiffrées les interrogé. Cette exigence est dépendante du fournisseur de magasin de clés qui stocke la clé CMK. Pour plus d’informations, consultez [utilisation des magasins de clés principales de colonne](#working-with-column-master-key-stores).

## <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>Récupération et modification des données dans des colonnes chiffrées

Une fois que vous activez Always Encrypted sur une connexion, vous pouvez utiliser les API SQLSRV standard (consultez [référence API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)) ou les API PDO_SQLSRV (consultez [référence API du pilote PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)) pour récupérer ou modifier des données dans les colonnes de la base de données chiffrée. En supposant que votre application dispose des autorisations de base de données requis et peut accéder à la clé principale de colonne, le pilote chiffre tous les paramètres de requête qui ciblent des colonnes chiffrées et déchiffrement les données extraites des colonnes chiffrées, qui se comporte de manière transparente à la application comme si les colonnes n’ont pas été chiffrés.

Si Always Encrypted n’est pas activé, les requêtes ayant des paramètres qui ciblent des colonnes chiffrées échouent. Les données peuvent toujours être récupérées à partir des colonnes chiffrées, tant que la requête n’a aucun paramètre qui cible des colonnes chiffrées. Toutefois, le pilote ne tente pas de n’importe quel déchiffrement et l’application reçoit les données chiffrées binaires (en tant que tableaux d’octets).

Le tableau ci-dessous récapitule le comportement des requêtes, selon qu’Always Encrypted est activé ou non :

|Caractéristique de la requête|Always Encrypted est activé et l’application peut accéder aux clés et à leurs métadonnées|Always Encrypted est activé et l’application ne peut pas accéder aux clés et à leurs métadonnées|Always Encrypted est désactivé|
|---|---|---|---|
|Paramètres ciblant des colonnes chiffrées.|Des valeurs de paramètres sont chiffrées en toute transparence.|Error|Error|
|Récupération des données à partir de colonnes chiffrées, sans paramètres ciblant des colonnes chiffrées.|Les résultats de colonnes chiffrées sont déchiffrés de manière transparente. L’application reçoit des valeurs de colonne en texte clair. |Error|Les résultats des colonnes chiffrées ne sont pas déchiffrés. L’application reçoit des valeurs chiffrées sous la forme de tableaux d’octets.|
 
Les exemples suivants illustrent la récupération et la modification de données dans des colonnes chiffrées. Les exemples reposent sur une table avec le schéma suivant. Les colonnes SSN et BirthDate sont chiffrées.
```
CREATE TABLE [dbo].[Patients](
 [PatientId] [int] IDENTITY(1,1),
 [SSN] [char](11) COLLATE Latin1_General_BIN2
 ENCRYPTED WITH (ENCRYPTION_TYPE = DETERMINISTIC,
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256',
 COLUMN_ENCRYPTION_KEY = CEK1) NOT NULL,
 [FirstName] [nvarchar](50) NULL,
 [LastName] [nvarchar](50) NULL,
 [BirthDate] [date]
 ENCRYPTED WITH (ENCRYPTION_TYPE = RANDOMIZED,
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256',
 COLUMN_ENCRYPTION_KEY = CEK1) NOT NULL
 PRIMARY KEY CLUSTERED ([PatientId] ASC) ON [PRIMARY])
 GO
```

### <a name="data-insertion-example"></a>Exemple d’Insertion de données

Les exemples suivants montrent comment utiliser les pilotes SQLSRV et PDO_SQLSRV pour insérer une ligne dans la table patients. Notez les points suivants :
 -   L’exemple de code ne contient aucun élément spécifique au chiffrement. Le pilote détecte automatiquement et chiffre les valeurs des paramètres SSN et BirthDate qui ciblent des colonnes chiffrées. Ce mécanisme rend le chiffrement transparent pour l’application.
 -   Les valeurs insérées dans les colonnes de base de données, y compris les colonnes chiffrées, sont passées en tant qu’objets liés. L’utilisation de paramètres est facultative lors de l’envoi de valeurs aux colonnes non chiffrées (même si elle est vivement recommandée, car elle contribue à empêcher l’injection SQL), mais elle est nécessaire pour les valeurs qui ciblent des colonnes chiffrées. Si les valeurs insérées dans les colonnes SSN ou BirthDate ont été passées en tant que littéraux incorporés dans l’instruction de requête, la requête échoue, car le pilote ne tente pas de chiffrer ou traiter des littéraux dans les requêtes. Par conséquent, le serveur les rejettera en les considérant comme incompatibles avec les colonnes chiffrées.
 -   Lors de l’insertion de valeurs à l’aide des paramètres de liaison, un type SQL qui est identique au type de données de la colonne cible ou dont le type de données de la colonne cible de la conversion est prise en charge doit être passé à la base de données. Cette exigence est prenant en charge Always Encrypted peu de conversions de type (pour plus d’informations, consultez [Always Encrypted (moteur de base de données)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)). Les deux pilotes PHP, SQLSRV et PDO_SQLSRV, chacune a un mécanisme pour déterminer le type SQL de la valeur de l’utilisateur. Par conséquent, l’utilisateur ne devra pas fournir le type SQL explicitement.
  -   Pour le pilote SQLSRV, l’utilisateur a deux options :
   -   S’appuient sur le pilote PHP pour déterminer et définir le type SQL approprié. Dans ce cas, l’utilisateur doit utiliser `sqlsrv_prepare` et `sqlsrv_execute` pour exécuter une requête paramétrable.
   -   Définir explicitement le type SQL.
  -   Pour le pilote PDO_SQLSRV, l’utilisateur ne dispose pas de l’option pour définir explicitement le type SQL d’un paramètre. Le pilote PDO_SQLSRV permet automatiquement l’utilisateur de déterminer le type SQL lors de la liaison d’un paramètre.
 -   Pour les pilotes déterminer le type SQL, certaines limitations s’appliquent :
  -   Pilote SQLSRV :
   -   Si l’utilisateur veut le pilote pour déterminer les types SQL pour les colonnes chiffrées, l’utilisateur doit utiliser `sqlsrv_prepare` et `sqlsrv_execute`.
   -   Si `sqlsrv_query` est préféré, l’utilisateur est chargé pour spécifier les types SQL pour tous les paramètres. Le type SQL spécifié doit inclure la longueur de chaîne pour les types de chaîne et la mise à l’échelle et la précision pour les types décimaux.
  -   Pilote PDO_SQLSRV :
   -   L’attribut d’instruction `PDO::SQLSRV_ATTR_DIRECT_QUERY` n’est pas pris en charge dans une requête paramétrable.
   -   L’attribut d’instruction `PDO::ATTR_EMULATE_PREPARES` n’est pas pris en charge dans une requête paramétrable.
   
Pilote SQLSRV et [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md):
```
// insertion into encrypted columns must use a parameterized query
$query = "INSERT INTO [dbo].[Patients] ([SSN], [FirstName], [LastName], [BirthDate]) VALUES (?, ?, ?, ?)";
$ssn = "795-73-9838";
$firstName = "Catherine";
$lastName = "Abel;
$birthDate = "1996-10-19";
$params = array($ssn, $firstName, $lastName, $birthDate);
// during sqlsrv_prepare, the driver determines the SQL types for each parameter and pass them to SQL server
$stmt = sqlsrv_prepare($conn, $query, $params);
sqlsrv_execute($stmt);
```

Pilote SQLSRV et [sqlsrv_query](../../connect/php/sqlsrv-query.md):
```
// insertion into encrypted columns must use a parameterized query
$query = "INSERT INTO [dbo].[Patients] ([SSN], [FirstName], [LastName], [BirthDate]) VALUES (?, ?, ?, ?)";
$ssn = "795-73-9838";
$firstName = "Catherine";
$lastName = "Abel";
$birthDate = "1996-10-19";
// need to provide the SQL types for ALL parameters  
// note the SQL types (including the string length) have to be the same at the column definition
$params = array(array(&$ssn, null, null, SQLSRV_SQLTYPE_CHAR(11)),
                array(&$firstName, null, null, SQLSRV_SQLTYPE_NVARCHAR(50)),
                array(&$lastName, null, null, SQLSRV_SQLTYPE_NVARCHAR(50)),
                array(&$birthDate, null, null, SQLSRV_SQLTYPE_DATE));
sqlsrv_query($conn, $query, $params);
```

Pilote PDO_SQLSRV et [PDO::prepare](../../connect/php/pdo-prepare.md):
```
// insertion into encrypted columns must use a parameterized query
$query = "INSERT INTO [dbo].[Patients] ([SSN], [FirstName], [LastName], [BirthDate]) VALUES (?, ?, ?, ?)";
$ssn = "795-73-9838";
$firstName = "Catherine";
$lastName = "Able";
$birthDate = "1996-10-19";
// during PDO::prepare, the driver determines the SQL types for each parameter and pass them to SQL server
$stmt = $conn->prepare($query);
$stmt->bindParam(1, $ssn);
$stmt->bindParam(2, $firstName);
$stmt->bindParam(3, $lastName);
$stmt->bindParam(4, $birthDate);
$stmt->execute();
```

### <a name="plaintext-data-retrieval-example"></a>Exemple d’extraction de données en texte clair

Les exemples suivants montrent le filtrage des données en fonction des valeurs chiffrées et la récupération des données de texte en clair de colonnes chiffrées à l’aide les pilotes SQLSRV et PDO_SQLSRV. Notez les points suivants :
 -   La valeur utilisée dans la clause WHERE pour filtrer sur la colonne SSN doit être transmis à l’aide du paramètre de liaison, afin que le pilote peut chiffrer de manière transparente avant de les envoyer au serveur.
 -   Lorsque vous exécutez une requête avec des paramètres liés, les pilotes PHP détermine automatiquement le type SQL pour l’utilisateur, sauf si l’utilisateur spécifie explicitement le type SQL lors de l’utilisation du pilote SQLSRV.
 -   Toutes les valeurs sont imprimées par le programme sont en texte clair, étant donné que le pilote déchiffre de manière transparente les données récupérées à partir des colonnes SSN et BirthDate.
 
Remarque : Les requêtes peuvent effectuer les comparaisons d’égalité sur des colonnes chiffrées uniquement si le chiffrement est déterministe. Pour plus d’informations, consultez [Sélection d’un chiffrement déterministe ou aléatoire](../../relational-databases/security/encryption/always-encrypted-database-engine.md#selecting--deterministic-or-randomized-encryption).

SQLSRV :
```
// since SSN is an encrypted column, need to pass the value in the WHERE clause through bind parameter
$query = "SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [SSN] = ?";
$ssn = "795-73-9838";
$stmt = sqlsrv_prepare($conn, $query, array(&$ssn));
// during sqlsrv_execute, the driver encrypts the ssn value and passes it to the database
sqlsrv_execute($stmt);
// fetch like usual
$row = sqlsrv_fetch_array($stmt);
```

PDO_SQLSRV :
```
// since SSN is an encrypted column, need to pass the value in the WHERE clause through bind parameter
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [SSN] = ?";
$ssn = "795-73-9838";
$stmt = $conn->prepare($query);
$stmt->bindParam(1, $ssn);
// during PDOStatement::execute, the driver encrypts the ssn value and passes it to the database
$stmt->execute();
// fetch like usual
$row = $stmt->fetch();
```

### <a name="ciphertext-data-retrieval-example"></a>Exemple d’extraction de données de texte chiffré

Si Always Encrypted n’est pas activé, une requête peut toujours récupérer des données à partir de colonnes chiffrées, tant qu’aucun de ses paramètres ne ciblent des colonnes chiffrées.

Les exemples suivants illustrent la récupération des données chiffrées binaires à partir de colonnes chiffrées à l’aide les pilotes SQLSRV et PDO_SQLSRV. Notez les points suivants :
 -   Étant donné qu’Always Encrypted n’est pas activé dans la chaîne de connexion, la requête retourne des valeurs SSN et BirthDate chiffrées sous la forme de tableaux d’octets (le programme convertit les valeurs en chaînes).
 -   Une requête qui récupère des données à partir de colonnes chiffrées lorsqu’Always Encrypted est désactivé peut avoir des paramètres, tant qu’aucun d’eux ne cible une colonne chiffrée. La requête suivante filtre en fonction des noms (LastName), qui ne sont pas chiffrés dans la base de données. Si la requête filtre par SSN ou BirthDate, la requête échoue.
 
SQLSRV :
```
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [LastName] = ?";
$lastName = "Abel";
$stmt = sqlsrv_prepare($conn, $query, array(&$lastName));
sqlsrv_execute($stmt);
$row = sqlsrv_fetch_array($stmt);
```

PDO_SQLSRV :
```
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [LastName] = ?";
$lastName = "Abel";
$stmt = $conn->prepare($query);
$stmt->bindParam(1, $lastName);
$stmt->execute();
$row = $stmt->fetch();
```

### <a name="avoiding-common-problems-when-querying-encrypted-columns"></a>Éviter les problèmes courants lors de l’interrogation de colonnes chiffrées

Cette section décrit les catégories d’erreurs courantes liées à l’interrogation des colonnes chiffrées à partir d’applications PHP, et explique comment éviter ces erreurs.

#### <a name="unsupported-data-type-conversion-errors"></a>Erreurs liées à la conversion de types de données non pris en charge

Always Encrypted ne prend en charge que peu de conversions de types de données chiffrées. Pour obtenir la liste détaillée des conversions de types prises en charge, consultez [Always Encrypted (moteur de base de données)](../../relational-databases/security/encryption/always-encrypted-database-engine.md). Procédez comme suit pour éviter les erreurs de conversion de type de données :
 -   Lorsque vous utilisez le pilote SQLSRV avec `sqlsrv_prepare` et `sqlsrv_execute` le type SQL, ainsi que la taille de colonne et le nombre de décimales du paramètre est déterminé automatiquement.
 -   Lorsque vous utilisez le pilote PDO_SQLSRV pour exécuter une requête, le type SQL avec la taille de colonne et le nombre de décimales du paramètre est déterminé automatiquement
 -   Lorsque vous utilisez le pilote SQLSRV avec `sqlsrv_query` pour exécuter une requête :
  -   Le type SQL du paramètre est soit exactement la même que le type de la colonne cible ou la conversion du type SQL pour le type de la colonne est pris en charge.
  -   La précision et l’échelle des paramètres ciblant les colonnes des types de données SQL Server `decimal` et `numeric` sont les mêmes que celles configurées pour la colonne cible.
  -   La précision des paramètres ciblant les colonnes des types de données SQL Server `datetime2`, `datetimeoffset` ou `time` n’est pas supérieure à celle de la colonne cible dans les requêtes qui modifient les valeurs de la colonne cible.
 -   N’utilisez pas les attributs d’instruction PDO_SQLSRV `PDO::SQLSRV_ATTR_DIRECT_QUERY` ou `PDO::ATTR_EMULATE_PREPARES` dans une requête paramétrable
 
#### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>Erreurs dues au passage de texte en clair au lieu de valeurs chiffrées

Les valeurs qui ciblent une colonne chiffrée doivent être chiffré avant d’être envoyées au serveur. Une tentative d’insertion, de modifier ou de filtrer par une valeur en texte clair sur génère une colonne chiffrée une erreur. Pour éviter ces erreurs, effectuez les vérifications suivantes :
 -   Always Encrypted est activé (dans la chaîne de connexion, définissez la `ColumnEncryption` mot clé à `Enabled`).
 -   Utilisez un paramètre de liaison pour envoyer des données ciblant des colonnes chiffrées. L’exemple suivant montre une requête qui filtre incorrectement par une littéral ou d’une constante sur une colonne chiffrée (SSN) :
```
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN='795-73-9838'";
```

## <a name="controlling-performance-impact-of-always-encrypted"></a>Contrôle de l’impact d’Always Encrypted sur les performances

Étant donné qu’Always Encrypted est une technologie de chiffrement côté client, la dégradation des performances s’observe côté client, et non dans la base de données. Outre le coût des opérations de chiffrement et de déchiffrement, les autres sources de dégradation des performances côté client sont les suivantes :
 -   Allers-retours supplémentaires vers la base de données afin de récupérer des métadonnées pour les paramètres de requête.
 -   Appels au magasin de clés principales de colonne pour accéder à une clé principale de colonne.
 
### <a name="round-trips-to-retrieve-metadata-for-query-parameters"></a>Allers-retours vers la base de données en vue de la récupération des métadonnées pour les paramètres de requête.

Si Always Encrypted est activé pour une connexion, le pilote ODBC appelle par défaut [sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) pour chaque requête paramétrable, en passant l’instruction de requête (sans valeurs de paramètre) à SQL Server. Cette procédure stockée analyse l’instruction de requête afin de déterminer si tous les paramètres doivent être chiffrés et si tel est le cas, retourne les informations relatives au chiffrement pour chaque paramètre permettre au pilote de les chiffrer.

Étant donné que les pilotes PHP permettent à l’utilisateur lier un paramètre dans une instruction préparée sans fournir le code SQL, tapez, lors de la liaison d’un paramètre dans une connexion Always Encrypted est activé, les pilotes PHP appeler [SQLDescribeParam](../../odbc/reference/syntax/sqldescribeparam-function.md) sur le paramètre pour obtenir le type SQL, la taille de colonne et chiffres décimaux. Les métadonnées sont ensuite utilisées pour appeler [SQLBindParameter]( ../../odbc/reference/syntax/sqlbindparameter-function.md). Ces supplémentaire `SQLDescribeParam` appels ne requièrent pas des allers-retours supplémentaires vers la base de données, comme le pilote ODBC a déjà stocké les informations sur le côté client lorsque `sys.sp_describe_parameter_encryption` a été appelée.

Les comportements précédents garantissent un haut niveau de transparence pour l’application cliente (et le développeur d’applications) est inutile de connaître les requêtes qui accèdent à des colonnes chiffrées, tant que les valeurs ciblant des colonnes chiffrées sont passées au pilote dans paramètres.

Contrairement à ODBC Driver for SQL Server, l’activation de Always Encrypted à/requête-niveau de l’instruction n'est pas encore pris en charge dans les pilotes PHP. 

### <a name="column-encryption-key-caching"></a>Mise en cache des clés de chiffrement de colonne

Pour réduire le nombre d’appels à un magasin de clés principales de colonne pour déchiffrer les clés de chiffrement de colonne (CEK), le pilote met en cache le texte en clair clés cek en mémoire. Après avoir reçu la clé CEK chiffré (ECEK) à partir des métadonnées de la base de données, le pilote ODBC tente tout d’abord rechercher la clé CEK en texte brut correspondant à la valeur de clé chiffrée dans le cache. Le pilote appelle le magasin de clés contenant la clé CMK uniquement s’il ne trouve pas le texte en clair correspondant CEK dans le cache.

Remarque : Dans le pilote ODBC pour SQL Server, les entrées dans le cache sont supprimées après un délai d’attente de deux heures. Ce comportement signifie que, pour un ECEK donné, le pilote contacte le magasin de clés qu’une seule fois pendant la durée de vie de l’application ou de toutes les deux heures, plus petite étant retenue.

## <a name="working-with-column-master-key-stores"></a>Utilisation de magasins de clés principales de colonne

Pour chiffrer ou déchiffrer des données, le pilote doit obtenir une clé CEK qui est configurée pour la colonne cible. Clés cek est stockés sous forme chiffrée (ECEKs) dans les métadonnées de base de données. Chaque clé CEK a une clé principale de colonne correspondante qui a été utilisé pour le chiffrement. Le [les métadonnées de base de données](../../t-sql/statements/create-column-master-key-transact-sql.md) ne stocke pas de la clé CMK lui-même ; il contient uniquement le nom du magasin de clés et des informations que le magasin de clés peut utiliser pour localiser la clé CMK.

Pour obtenir la valeur de texte en clair de l’un ECEK, le pilote obtient d’abord les métadonnées relatives à la clé CEK et sa clé principale de colonne correspondantes, et il utilise ces informations pour contacter le magasin de clés contenant la clé CMK, puis la demande pour déchiffrer l’ECEK. Le pilote communique avec un magasin de clés à l’aide d’un fournisseur de magasin de clés.

Microsoft Driver 5.3.0 for PHP for SQL Server, uniquement Windows Certificate Store Provider et Azure Key Vault sont prises en charge. L’autre fournisseur de magasin de clés pris en charge par le pilote ODBC (fournisseur de magasin de clés personnalisé) n’est pas encore pris en charge.

### <a name="using-the-windows-certificate-store-provider"></a>L’utilisation du fournisseur de Store de certificat Windows

Le pilote ODBC pour SQL Server sur Windows inclut un fournisseur de magasin de clé principale de colonne intégré pour le Store de certificat Windows nommé `MSSQL_CERTIFICATE_STORE`. (Ce fournisseur n’est pas disponible sur Mac OS ou Linux). Avec ce fournisseur, la clé principale de colonne sont stockées localement sur l’ordinateur client et aucune configuration supplémentaire par l’application n’est nécessaire pour l’utiliser avec le pilote. Toutefois, l’application doit avoir accès au certificat et sa clé privée dans le magasin. Pour plus d’informations, consultez [Créer et stocker des clés principales de colonne (Always Encrypted)](../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md).

### <a name="using-azure-key-vault"></a>À l’aide d’Azure Key Vault

Azure Key Vault vous permet de stocker les clés de chiffrement, les mots de passe et autres secrets à l’aide d’Azure et peut être utilisé pour stocker les clés pour Always Encrypted. Le pilote ODBC pour SQL Server (version 17 et versions ultérieures) inclut un fournisseur de magasin intégrés clé principale pour Azure Key Vault. Les options de connexion suivantes gérer la configuration d’Azure Key Vault : `KeyStoreAuthentication`, `KeyStorePrincipalId`, et `KeyStoreSecret`. 
 -   `KeyStoreAuthentication` peut prendre une des deux valeurs de chaîne possibles : `KeyVaultPassword` et `KeyVaultClientSecret`. Ces valeurs contrôlent quelles sont les informations d’authentification sont utilisés avec les autres deux mots clés.
 -   `KeyStorePrincipalId` prend une chaîne qui représente un identificateur pour le compte qui cherchent à accéder à Azure Key Vault. 
     -   Si `KeyStoreAuthentication` a la valeur `KeyVaultPassword`, puis `KeyStorePrincipalId` doit être le nom d’un utilisateur Azure ActiveDirectory.
     -   Si `KeyStoreAuthentication` a la valeur `KeyVaultClientSecret`, puis `KeyStorePrincipalId` doit être un ID de client d’application.
 -   `KeyStoreSecret` prend une chaîne représentant un secret d’identification. 
     -   Si `KeyStoreAuthentication` a la valeur `KeyVaultPassword`, puis `KeyStoreSecret` doit être le mot de passe. 
     -   Si `KeyStoreAuthentication` a la valeur `KeyVaultClientSecret`, puis `KeyStoreSecret` doit être le secret d’application associé à l’ID de client d’application.

Les trois options doivent être présentes dans la chaîne de connexion à utiliser Azure Key Vault. En outre, `ColumnEncryption` doit être définie sur `Enabled`. Si `ColumnEncryption` a la valeur `Disabled` mais les options d’Azure Key Vault sont présentes, le script va continuer sans erreurs, mais aucun chiffrement ne sera effectuée.

Les exemples suivants montrent comment se connecter à SQL Server à l’aide d’Azure Key Vault.

SQLSRV :

À l’aide d’un compte Azure Active Directory :
```
$connectionInfo = array("Database"=>$databaseName, "UID"=>$uid, "PWD"=>$pwd, "ColumnEncryption"=>"Enabled", "KeyStoreAuthentication"=>"KeyVaultPassword", "KeyStorePrincipalId"=>$AADUsername, "KeyStoreAuthentication"=>$AADPassword);
$conn = sqlsrv_connect($server, $connectionInfo);
```
À l’aide d’un ID de client d’application Azure et la clé secrète :
```
$connectionInfo = array("Database"=>$databaseName, "UID"=>$uid, "PWD"=>$pwd, "ColumnEncryption"=>"Enabled", "KeyStoreAuthentication"=>"KeyVaultClientSecret", "KeyStorePrincipalId"=>$applicationClientID, "KeyStoreAuthentication"=>$applicationClientSecret);
$conn = sqlsrv_connect($server, $connectionInfo);
```

PDO_SQLSRV : À l’aide d’un compte Azure Active Directory :
```
$connectionInfo = "Database = $databaseName; ColumnEncryption = Enabled; KeyStoreAuthentication = KeyVaultPassword; KeyStorePrincipalId = $AADUsername; KeyStoreAuthentication = $AADPassword;";
$conn = new PDO("sqlsrv:server = $server; $connectionInfo", $uid, $pwd);
```
À l’aide d’un ID de client d’application Azure et la clé secrète :
```
$connectionInfo = "Database = $databaseName; ColumnEncryption = Enabled; KeyStoreAuthentication = KeyVaultClientSecret; KeyStorePrincipalId = $applicationClientID; KeyStoreAuthentication = $applicationClientSecret;";
$conn = new PDO("sqlsrv:server = $server; $connectionInfo", $uid, $pwd);
```

## <a name="limitations-of-the-php-drivers-when-using-always-encrypted"></a>Limitations des pilotes PHP lors de l’utilisation de Always Encrypted

SQLSRV et PDO_SQLSRV :
 -   Linux/macOS ne prennent pas en charge Windows Certificate Store Provider
 -   Forcer le chiffrement de paramètre
 -   Activation d’Always Encrypted au niveau de l’instruction 
 -   Lorsque vous utilisez les marchés de fonctionnalité et non-UTF-8 Always Encrypted sur Linux et macOS (par exemple, « fr_FR. ISO-8859-1 »), insertion de données de type null ou une chaîne vide dans une colonne de cryptée char (n) peut ne pas fonctionne, sauf si la Page de codes 1252 a été installé sur votre système
 
SQLSRV :
 -   À l’aide de `sqlsrv_query` pour le paramètre de liaison sans spécifier le type SQL
 -   À l’aide de `sqlsrv_prepare` pour la liaison de paramètres dans un lot d’instructions SQL  
 
PDO_SQLSRV :
 -   `PDO::SQLSRV_ATTR_DIRECT_QUERY` attribut d’instruction spécifiée dans une requête paramétrable
 -   `PDO::ATTR_EMULATE_PREPARE` attribut d’instruction spécifiée dans une requête paramétrable
 -   liaison de paramètres dans un lot d’instructions SQL
 
Les pilotes PHP héritent également les limitations imposées par le pilote ODBC pour SQL Server et la base de données. Consultez [Limitations du pilote ODBC lors de l’utilisation de Always Encrypted](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md) et [toujours chiffré informations sur les fonctionnalités](../../relational-databases/security/encryption/always-encrypted-database-engine.md#feature-details).  
  
## <a name="see-also"></a> Voir aussi  
[Guide de programmation pour le pilote SQL PHP](../../connect/php/programming-guide-for-php-sql-driver.md)
[Référence d’API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Référence API du pilote PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  

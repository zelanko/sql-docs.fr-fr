---
title: Utilisation d’Always Encrypted avec ODBC Driver for SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 09/01/2018
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 02e306b8-9dde-4846-8d64-c528e2ffe479
ms.author: v-chojas
manager: craigg
author: MightyPen
ms.openlocfilehash: 72ff999a4b88bff5d8b78f8e8b936da18b8a4e16
ms.sourcegitcommit: 1e28f923cda9436a4395a405ebda5149202f8204
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55044946"
---
# <a name="using-always-encrypted-with-the-odbc-driver-for-sql-server"></a>Utilisation d’Always Encrypted avec ODBC Driver for SQL Server
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

### <a name="applicable-to"></a>Applicable à

- Pilote ODBC 13.1 pour SQL Server
- Pilote ODBC 17 pour SQL Server

### <a name="introduction"></a>Introduction

Cet article fournit des informations sur la façon de développer des applications ODBC utilisant [Always Encrypted (moteur de base de données)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) et [ODBC Driver for SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md).

Always Encrypted permet aux applications clientes de chiffrer des données sensibles et de ne jamais révéler les données ou les clés de chiffrement à SQL Server ou Azure SQL Database. À cette fin, un pilote compatible avec Always Encrypted, comme ODBC Driver for SQL Server, chiffre et déchiffre de manière transparente les données sensibles dans l’application cliente. Le pilote détermine automatiquement les paramètres de requêtes qui correspondent aux colonnes de base de données sensibles (protégées avec Always Encrypted) et chiffre les valeurs de ces paramètres avant de transmettre les données à SQL Server ou Azure SQL Database. De même, il déchiffre de manière transparente les données récupérées dans les colonnes de base de données chiffrées, qui figurent dans les résultats de la requête. Pour plus d’informations, consultez [Always Encrypted (moteur de base de données)](../../relational-databases/security/encryption/always-encrypted-database-engine.md).

### <a name="prerequisites"></a>Conditions préalables requises

Configurez Always Encrypted dans votre base de données. Pour cela, vous devez mettre en service des clés Always Encrypted et configurer le chiffrement pour les colonnes de base de données sélectionnées. Si vous n’avez pas déjà une base de données dans laquelle est configuré Always Encrypted, suivez les instructions de [Prise en main d’Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md#getting-started-with-always-encrypted). En particulier, votre base de données doit contenir les définitions de métadonnées pour une clé principale de colonne (CMK), une clé de chiffrement de colonne (CEK) et une table contenant une ou plusieurs colonnes chiffrées à l’aide de cette clé CEK.

### <a name="enabling-always-encrypted-in-an-odbc-application"></a>Activer le chiffrement intégral dans une Application ODBC

Le moyen le plus simple pour activer le paramètre chiffrement et déchiffrement de colonne chiffrée un jeu de résultats est en définissant la valeur de la `ColumnEncryption` mot clé de chaîne de connexion à **activé**. Voici un exemple de chaîne de connexion activant Always Encrypted :

```
SQLWCHAR *connString = L"Driver={ODBC Driver 13 for SQL Server};Server={myServer};Trusted_Connection=yes;ColumnEncryption=Enabled;";
```

Always Encrypted peut également être activé dans la configuration de source de données, à l’aide de la même clé et valeur (qui sera remplacée par le paramètre de chaîne connexion, le cas échéant), ou par programmation avec le `SQL_COPT_SS_COLUMN_ENCRYPTION` attribut de préconnexion. Définition de cette façon substitue la valeur définie dans la chaîne de connexion ou de la source de données :

```
 SQLSetConnectAttr(hdbc, SQL_COPT_SS_COLUMN_ENCRYPTION, (SQLPOINTER)SQL_COLUMN_ENCRYPTION_ENABLE, 0);
```

Une fois activé pour la connexion, le comportement d’Always Encrypted peut être ajusté pour des requêtes individuelles. Consultez [contrôlant la Performance Impact d’Always Encrypted](#controlling-the-performance-impact-of-always-encrypted) ci-dessous pour plus d’informations.

Notez que l’activation d’Always Encrypted n’est pas suffisant pour le chiffrement ou déchiffrement réussisse. Vous devez également vous assurer que :

- L’application dispose des autorisations de base de données *VIEW ANY COLUMN MASTER KEY DEFINITION* et *VIEW ANY COLUMN ENCRYPTION KEY DEFINITION* qui sont nécessaires pour accéder aux métadonnées des clés Always Encrypted dans la base de données. Pour plus d’informations, consultez [les autorisations de base de données](../../relational-databases/security/encryption/always-encrypted-database-engine.md#database-permissions).

- L’application peut accéder à la clé principale de colonne qui protège les clés cek pour les colonnes chiffrées les interrogé. Cela dépend du fournisseur de magasin de clés qui stocke la clé CMK. Consultez [utilisation des magasins de clés principales de colonne](#working-with-column-master-key-stores) pour plus d’informations.

### <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>Récupération et modification des données dans des colonnes chiffrées

Une fois que vous activez Always Encrypted sur une connexion, vous pouvez utiliser les API ODBC standard (consultez [exemple de code ODBC](https://code.msdn.microsoft.com/windowsapps/ODBC-sample-191624ae/sourcecode?fileId=51137&pathId=1980325953) ou [de référence du programmeur ODBC](https://msdn.microsoft.com/library/ms714177(v=vs.85).aspx)) pour récupérer ou modifier des données dans les colonnes de la base de données chiffrée. En supposant que votre application a requis des autorisations de base de données et peut accéder à la clé principale de colonne, le pilote chiffre tous les paramètres de requête qui ciblent des colonnes chiffrées et déchiffrement les données extraites des colonnes chiffrées, qui se comporte de manière transparente à la application comme si les colonnes n’ont pas été chiffrés.

Si Always Encrypted n’est pas activé, les requêtes ayant des paramètres qui ciblent des colonnes chiffrées échouent. Les données peuvent toujours être récupérées à partir des colonnes chiffrées, tant que la requête n’a aucun paramètre qui cible des colonnes chiffrées. Toutefois, le pilote ne tente pas de n’importe quel déchiffrement et l’application reçoit les données chiffrées binaires (en tant que tableaux d’octets).

Le tableau ci-dessous récapitule le comportement des requêtes, selon qu’Always Encrypted est activé ou non :

|Caractéristique de la requête | Always Encrypted est activé et l’application peut accéder aux clés et à leurs métadonnées|Always Encrypted est activé et l’application ne peut pas accéder aux clés et à leurs métadonnées | Always Encrypted est désactivé|
|:---|:---|:---|:---|
| Paramètres ciblant des colonnes chiffrées. | Des valeurs de paramètres sont chiffrées en toute transparence. | Error | Error|
| Récupération des données à partir de colonnes chiffrées, sans paramètres ciblant des colonnes chiffrées.| Les résultats de colonnes chiffrées sont déchiffrés de manière transparente. L’application reçoit des valeurs de colonne en texte clair. | Error | Les résultats des colonnes chiffrées ne sont pas déchiffrés. L’application reçoit des valeurs chiffrées sous la forme de tableaux d’octets.

Les exemples suivants illustrent la récupération et la modification de données dans des colonnes chiffrées. Les exemples reposent sur une table avec le schéma suivant. Notez que les colonnes SSN et BirthDate sont chiffrées.

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
 PRIMARY KEY CLUSTERED ([PatientId] ASC) ON [PRIMARY] )
 GO
```

#### <a name="data-insertion-example"></a>Exemple d’Insertion de données

Cet exemple insère une ligne dans la table Patients. Notez les points suivants :

- L’exemple de code ne contient aucun élément spécifique au chiffrement. Le pilote détecte automatiquement et chiffre les valeurs des paramètres de date et SSN qui ciblent des colonnes chiffrées. Le chiffrement est donc transparent pour l’application.

- Les valeurs insérées dans les colonnes de base de données, y compris les colonnes chiffrées, sont transmises sous forme de paramètres liés (voir [Fonction SQLBindParameter](https://msdn.microsoft.com/library/ms710963(v=vs.85).aspx)). L’utilisation de paramètres est facultative lors de l’envoi de valeurs aux colonnes non chiffrées (même si elle est vivement recommandée, car elle contribue à empêcher l’injection SQL), mais elle est nécessaire pour les valeurs qui ciblent des colonnes chiffrées. Si les valeurs insérées dans les colonnes SSN ou BirthDate ont été passées en tant que littéraux incorporés dans l’instruction de requête, la requête échoue, car le pilote ne tente pas de chiffrer ou traiter des littéraux dans les requêtes. Par conséquent, le serveur les rejettera en les considérant comme incompatibles avec les colonnes chiffrées.

- Le type SQL du paramètre inséré dans la colonne SSN est défini à SQL_CHAR, qui mappe à la **char** type de données SQL Server (`rc = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 11, 0, (SQLPOINTER)SSN, 0, &cbSSN);`). Si le type du paramètre a été défini sur SQL_WCHAR, qui mappe à **nchar**, la requête échoue, car Always Encrypted ne prend pas en charge les conversions de côté serveur à partir de valeurs nchar chiffrées en valeurs char chiffré. Consultez [de référence du programmeur ODBC--annexe d : Types de données](https://msdn.microsoft.com/library/ms713607.aspx) pour plus d’informations sur les mappages de type de données.

```
    SQL_DATE_STRUCT date;
    SQLLEN cbdate;   // size of date structure  

    SQLCHAR SSN[12];
    strcpy_s((char*)SSN, _countof(SSN), "795-73-9838");

    SQLWCHAR* firstName = L"Catherine";
    SQLWCHAR* lastName = L"Abel";
    SQLINTEGER cbSSN = SQL_NTS, cbFirstName = SQL_NTS, cbLastName = SQL_NTS;

    // Initialize the date structure  
    date.day = 10;
    date.month = 9;
    date.year = 1996;

    // Size of structures   
    cbdate = sizeof(SQL_DATE_STRUCT);

    SQLRETURN rc = 0;

    string queryText = "INSERT INTO [dbo].[Patients] ([SSN], [FirstName], [LastName], [BirthDate]) VALUES (?, ?, ?, ?) ";

    rc = SQLPrepare(hstmt, (SQLCHAR *)queryText.c_str(), SQL_NTS);

    //SSN
    rc = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 11, 0, (SQLPOINTER)SSN, 0, &cbSSN);
    //FirstName
    rc = SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_WCHAR, SQL_WCHAR, 50, 0, (SQLPOINTER)firstName, 0, &cbFirstName);
    //LastName
    rc = SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_WCHAR, SQL_WCHAR, 50, 0, (SQLPOINTER)lastName, 0, &cbLastName);
    //BirthDate
    rc = SQLBindParameter(hstmt, 4, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 10, 0, (SQLPOINTER)&date, 0, &cbdate);

    rc = SQLExecute(hstmt);
```

#### <a name="plaintext-data-retrieval-example"></a>Exemple d’extraction de données en texte clair

L’exemple suivant montre le filtrage de données basé sur des valeurs chiffrées, ainsi que la récupération de données en texte clair à partir de colonnes chiffrées. Notez les points suivants :

- La valeur utilisée dans la clause WHERE pour filtrer la colonne SSN doit être transmise avec SQLBindParameter, afin que le pilote puisse la chiffrer de manière transparente avant de l’envoyer au serveur.

- Toutes les valeurs imprimées par le programme sont en texte clair, car le pilote déchiffre de manière transparente les données récupérées à partir des colonnes SSN et BirthDate.

> [!NOTE]
> Les requêtes peuvent effectuer des comparaisons d’égalité sur des colonnes chiffrées uniquement si le chiffrement est déterministe. Pour plus d’informations, consultez [Sélection d’un chiffrement déterministe ou aléatoire](../../relational-databases/security/encryption/always-encrypted-database-engine.md#selecting--deterministic-or-randomized-encryption).

```
SQLCHAR SSN[12];
strcpy_s((char*)SSN, _countof(SSN), "795-73-9838");

SQLWCHAR* firstName = L"Catherine";
SQLWCHAR* lastName = L"Abel";
SQLINTEGER cbSSN = SQL_NTS, cbFirstName = SQL_NTS, cbLastName = SQL_NTS;

SQLRETURN rc = 0;
string empty = "";
string queryText = "SELECT [SSN], [FirstName], [LastName], [BirthDate] " + empty +
    "FROM  [dbo].[Patients]" +
    "WHERE " +
    "[SSN] = ? ";

rc = SQLPrepare(hstmt, (SQLCHAR *)queryText.c_str(), SQL_NTS);

//SSN
rc = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, 11, 0, (SQLPOINTER)SSN, 0, &cbSSN);

rc = SQLExecute(hstmt);
HandleDiagnosticRecord(hstmt, SQL_HANDLE_STMT, rc);

SQL_DATE_STRUCT dateVal;
SQLWCHAR firstNameVal[50];
SQLWCHAR lastNameVal[50];
SQLCHAR SSNVal[12];
SQLLEN cbdate;   // size of date structure  

int rowcount = 0;
while (SQL_SUCCEEDED(SQLFetch(hstmt)))
{
    rowcount++;
    SQLGetData(hstmt, 1, SQL_C_CHAR, &SSNVal, 11, &cbSSN);
    SQLGetData(hstmt, 2, SQL_C_WCHAR, &firstNameVal, 50, &cbFirstName);
    SQLGetData(hstmt, 3, SQL_C_WCHAR, &lastNameVal, 50, &cbLastName);
    SQLGetData(hstmt, 4, SQL_C_TYPE_DATE, &dateVal, 10, &cbdate);        
}
```

#### <a name="ciphertext-data-retrieval-example"></a>Exemple d’extraction de données de texte chiffré

Si Always Encrypted n’est pas activé, une requête peut toujours récupérer des données à partir de colonnes chiffrées, tant qu’aucun de ses paramètres ne ciblent des colonnes chiffrées.

L’exemple suivant illustre la récupération de données chiffrées binaires à partir de colonnes chiffrées. Notez les points suivants :

- Étant donné qu’Always Encrypted n’est pas toujours activé dans la chaîne de connexion, la requête retourne des valeurs SSN et BirthDate chiffrées sous la forme de tableaux d’octets (le programme convertit les valeurs en chaînes).
- Une requête qui récupère des données à partir de colonnes chiffrées lorsqu’Always Encrypted est désactivé peut avoir des paramètres, tant qu’aucun d’eux ne cible une colonne chiffrée. La requête ci-dessus filtre par nom (LastName), ce qui n’est pas chiffré dans la base de données. Si la requête filtre par SSN ou BirthDate, la requête échoue.


```
SQLCHAR SSN[12];
strcpy_s((char*)SSN, _countof(SSN), "795-73-9838");

SQLWCHAR* firstName = L"Catherine";
SQLWCHAR* lastName = L"Abel";
SQLINTEGER cbSSN = SQL_NTS, cbFirstName = SQL_NTS, cbLastName = SQL_NTS;

SQLRETURN rc = 0;
string empty = "";
string queryText = "SELECT [SSN], [FirstName], [LastName], [BirthDate] " + empty +
    "FROM  [dbo].[Patients]" +
    "WHERE " +
    "[LastName] = ?";

rc = SQLPrepare(hstmt, (SQLCHAR *)queryText.c_str(), SQL_NTS);

//LastName
rc = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_WCHAR, SQL_WCHAR, 50, 0, (SQLPOINTER)lastName, 0, &cbLastName);

rc = SQLExecute(hstmt);
HandleDiagnosticRecord(hstmt, SQL_HANDLE_STMT, rc);

SQL_DATE_STRUCT dateVal;
SQLWCHAR firstNameVal[50];
SQLWCHAR lastNameVal[50];
SQLCHAR SSNVal[12];
SQLLEN cbdate;   // size of date structure  

int rowcount = 0;
while (SQL_SUCCEEDED(SQLFetch(hstmt)))
{
    rowcount++;
    SQLGetData(hstmt, 1, SQL_C_CHAR, &SSNVal, 11, &cbSSN);
    SQLGetData(hstmt, 2, SQL_C_WCHAR, &firstNameVal, 50, &cbFirstName);
    SQLGetData(hstmt, 3, SQL_C_WCHAR, &lastNameVal, 50, &cbLastName);
    SQLGetData(hstmt, 4, SQL_C_TYPE_DATE, &dateVal, 10, &cbdate);        
}
```

#### <a name="avoiding-common-problems-when-querying-encrypted-columns"></a>Éviter les problèmes courants lors de l’interrogation de colonnes chiffrées

Cette section décrit des catégories d’erreurs courantes liées à l’interrogation des colonnes chiffrées à partir d’applications ODBC et fournit des conseils sur la façon de les éviter.

##### <a name="unsupported-data-type-conversion-errors"></a>Erreurs liées à la conversion de types de données non pris en charge

Always Encrypted ne prend en charge que peu de conversions de types de données chiffrées. Pour obtenir la liste détaillée des conversions de types prises en charge, consultez [Always Encrypted (moteur de base de données)](../../relational-databases/security/encryption/always-encrypted-database-engine.md). Pour éviter les erreurs de conversion de types de données, assurez-vous que vous observez les points suivants lors de l’utilisation de SQLBindParameter avec des paramètres ciblant des colonnes chiffrées :

- Le type SQL du paramètre est soit exactement la même que le type de la colonne cible ou la conversion du type SQL pour le type de la colonne est pris en charge.

- La précision et l’échelle des paramètres ciblant les colonnes des types de données SQL Server `decimal` et `numeric` sont les mêmes que celles configurées pour la colonne cible.

- La précision des paramètres ciblant les colonnes des types de données SQL Server `datetime2`, `datetimeoffset` ou `time` n’est pas supérieure à celle de la colonne cible dans les requêtes qui modifient les valeurs de la colonne cible.  

##### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>Erreurs dues au passage de texte en clair au lieu de valeurs chiffrées

Les valeurs qui ciblent une colonne chiffrée doivent être chiffré avant d’être envoyées au serveur. Toute tentative d’insertion, de modification ou de filtrage par une valeur en texte clair dans une colonne chiffrée entraîne une erreur. Pour éviter ces erreurs, effectuez les vérifications suivantes :

- Always Encrypted est activé (dans la source de données, la chaîne de connexion avant de vous connecter en définissant le `SQL_COPT_SS_COLUMN_ENCRYPTION` attribut de connexion pour une connexion spécifique, ou le `SQL_SOPT_SS_COLUMN_ENCRYPTION` attribut d’instruction pour une instruction spécifique).

- Utilisez SQLBindParameter pour envoyer des données ciblant des colonnes chiffrées. L’exemple ci-dessous illustre une requête qui filtre incorrectement une colonne chiffrée (SSN) à l’aide d’un littéral/d’une constante, au lieu de passer le littéral comme argument à SQLBindParameter.

```
string queryText = "SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN='795-73-9838'";
```

### <a name="precautions-when-using-sqlsetpos-and-sqlmoreresults"></a>Précautions lorsque vous utilisez SQLSetPos et SQLMoreResults

#### <a name="sqlsetpos"></a>SQLSetPos

Le `SQLSetPos` API permet à une application mettre à jour des lignes dans un jeu de résultats à l’aide de mémoires tampons qui ont été lié avec SQLBindCol et dans quelle ligne les données ont été extraites précédemment. En raison du comportement de remplissage asymétrique de cryptée types de longueur fixe, il est possible de façon inattendue modifier les données de ces colonnes lors de l’exécution des mises à jour sur d’autres colonnes dans la ligne. Avec AE, les valeurs de caractères de longueur fixe de seconde seront complétées si la valeur est inférieure à la taille de mémoire tampon.

Pour éviter ce comportement, utilisez le `SQL_COLUMN_IGNORE` indicateur pour ignorer les colonnes qui ne seront pas mis à jour dans le cadre de `SQLBulkOperations` et lorsque vous utilisez `SQLSetPos` pour le curseur en fonction des mises à jour.  Toutes les colonnes qui ne sont pas être modifiées directement par l’application doivent être ignorées, à la fois pour les performances et pour éviter la troncation des colonnes qui sont liés à une mémoire tampon *plus petits* que leur taille réelle de (DB). Pour plus d’informations, consultez [référence de fonction SQLSetPos](https://msdn.microsoft.com/library/ms713507(v=vs.85).aspx).

#### <a name="sqlmoreresults--sqldescribecol"></a>SQLMoreResults & SQLDescribeCol

Programmes d’application peuvent appeler [SQLDescribeCol](https://msdn.microsoft.com/library/ms716289(v=vs.85).aspx) pour retourner des métadonnées sur les colonnes dans les instructions préparées.  Quand Always Encrypted est activé, l’appel `SQLMoreResults` *avant* appelant `SQLDescribeCol` provoque [sp_describe_first_result_set](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md) à appeler, ce qui ne retourne pas correctement le texte en clair métadonnées pour les colonnes chiffrées. Pour éviter ce problème, appelez `SQLDescribeCol` sur les instructions préparées *avant* appelant `SQLMoreResults`.

## <a name="controlling-the-performance-impact-of-always-encrypted"></a>Contrôle de l’impact d’Always Encrypted sur les performances

Étant donné qu’Always Encrypted est une technologie de chiffrement côté client, la dégradation des performances s’observe côté client, et non dans la base de données. Outre le coût des opérations de chiffrement et de déchiffrement, les autres sources de dégradation des performances côté client sont les suivantes :

- Allers-retours supplémentaires vers la base de données pour récupérer des métadonnées pour les paramètres de requête.

- Appels au magasin de clés principales de colonne pour accéder à une clé principale de colonne.

Cette section décrit les outils intégrés d’optimisation des performances dans ODBC Driver for SQL Server et comment vous pouvez contrôler l’impact des deux facteurs ci-dessus sur les performances.

### <a name="controlling-round-trips-to-retrieve-metadata-for-query-parameters"></a>Contrôle des allers-retours en vue de la récupération des métadonnées pour les paramètres de requête

Si Always Encrypted est activé pour une connexion, le pilote appelle par défaut [sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) pour chaque requête paramétrable, en passant l’instruction de requête (sans valeurs de paramètre) à SQL Server. Cette procédure stockée analyse l’instruction de requête afin de déterminer si tous les paramètres doivent être chiffrés et si tel est le cas, retourne les informations relatives au chiffrement pour chaque paramètre permettre au pilote de les chiffrer. Ce comportement garantit un haut niveau de transparence à l’application cliente : L’application et le développeur d’applications n’ont pas besoin de connaître les requêtes qui accèdent à des colonnes chiffrées, tant que les valeurs ciblant des colonnes chiffrées sont passées au pilote dans les paramètres.

### <a name="per-statement-always-encrypted-behavior"></a>Par instruction Always Encrypted comportement

Pour contrôler l’impact sur les performances de récupération des métadonnées de chiffrement pour les requêtes paramétrables, vous pouvez modifier le comportement Always Encrypted pour les requêtes s’il a été activé sur la connexion. De cette façon, vous pouvez vous assurer que `sys.sp_describe_parameter_encryption` est appelé uniquement pour les requêtes que vous connaissez ont des paramètres ciblant des colonnes chiffrées. Notez toutefois que, de cette façon, vous réduisez la transparence du chiffrement. Si vous chiffrez des colonnes supplémentaires dans votre base de données, vous devrez peut-être modifier le code de votre application pour l’aligner sur les modifications du schéma.

Pour contrôler le comportement Always Encrypted d’une instruction, Appelez SQLSetStmtAttr pour définir le `SQL_SOPT_SS_COLUMN_ENCRYPTION` attribut d’instruction à une des valeurs suivantes :

|Valeur|Description|
|-|-|
|`SQL_CE_DISABLED` (0)|Always Encrypted est désactivé pour l’instruction|
|`SQL_CE_RESULTSETONLY` (1)|Déchiffrement. Jeux de résultats et valeurs de retour sont déchiffrées et les paramètres ne sont pas chiffrés.|
|`SQL_CE_ENABLED` (3) | Always Encrypted est activé et utilisé pour les paramètres et les résultats|

Nouveaux descripteurs d’instruction créés à partir d’une connexion avec Always Encrypted est activé par défaut à SQL_CE_ENABLED. Ces créé à partir d’une connexion avec celui-ci désactivé par défaut à SQL_CE_DISABLED (et il n’est pas possible d’activer le chiffrement intégral sur ces derniers.)

Si la plupart des requêtes d’une application cliente accéder à des colonnes chiffrées, suivez les recommandations :

- Affectez au mot clé de chaîne de connexion `ColumnEncryption` la valeur `Enabled`.

- Définir le `SQL_SOPT_SS_COLUMN_ENCRYPTION` attribut `SQL_CE_DISABLED` sur les instructions qui ne peuvent pas accèdent à toutes les colonnes chiffrées. Cette opération va désactiver les deux appel `sys.sp_describe_parameter_encryption` , ainsi que les tentatives de déchiffrer les valeurs dans le résultat défini.
    
- Définir le `SQL_SOPT_SS_COLUMN_ENCRYPTION` attribut `SQL_CE_RESULTSETONLY` sur les instructions qui n’ont pas aucun paramètre exigeant un chiffrement, mais qui récupèrent des données de colonnes chiffrées. Cette opération va désactiver l’appel `sys.sp_describe_parameter_encryption` et le chiffrement de paramètre. Les résultats contenant des colonnes chiffrées continueront à être déchiffré.

## <a name="always-encrypted-security-settings"></a>Always Encrypted des paramètres de sécurité

### <a name="force-column-encryption"></a>Forcer le chiffrement de colonne

Pour appliquer le chiffrement d’un paramètre, définissez le `SQL_CA_SS_FORCE_ENCRYPT` champ de descripteur de paramètre d’implémentation (IPD) via un appel à la fonction SQLSetDescField. Une valeur différente de zéro, le pilote retourner une erreur quand aucune métadonnée de chiffrement n’est retournée pour le paramètre associé.

```
SQLHDESC ipd;
SQLGetStmtAttr(hStmt, SQL_ATTR_IMP_PARAM_DESC, &ipd, 0, 0);
SQLSetDescField(ipd, paramNum, SQL_CA_SS_FORCE_ENCRYPT, (SQLPOINTER)TRUE, SQL_IS_SMALLINT);   
```

Si SQL Server informe le pilote que le paramètre ne nécessite pas de chiffrement, les requêtes utilisant ce paramètre échouent. Cette propriété fournit une protection supplémentaire contre les attaques au niveau de la sécurité qui impliquent un serveur SQL Server compromis fournissant des métadonnées de chiffrement incorrectes au client, ce qui peut entraîner la divulgation de données.

### <a name="column-encryption-key-caching"></a>Mise en cache des clés de chiffrement de colonne

Pour réduire le nombre d’appels à un magasin de clés principales de colonne pour déchiffrer les clés de chiffrement de colonne, le pilote met en cache le texte en clair clés cek en mémoire. Le cache de la clé CEK est global pour le pilote et pas associé à une connexion. Après avoir reçu l’ECEK à partir des métadonnées de la base de données, le pilote tente de tout d’abord de trouver la clé CEK en texte brut correspondant à la valeur de clé chiffrée dans le cache. Le pilote appelle le magasin de clés contenant la clé CMK uniquement s’il ne trouve pas le texte en clair correspondant CEK dans le cache.

> [!NOTE]
> Dans le pilote ODBC pour SQL Server, les entrées dans le cache sont supprimées après un délai d’attente de deux heures. Cela signifie que pour un ECEK donné, le pilote contacte le magasin de clés qu’une seule fois pendant la durée de vie de l’application ou de toutes les deux heures, plus petite étant retenue.

À compter du 17.1 de pilote ODBC pour SQL Server, le délai d’expiration du cache de clé CEK peut être ajusté à l’aide de la `SQL_COPT_SS_CEKCACHETTL` attribut de connexion, qui spécifie le nombre de secondes pendant lesquelles une clé CEK resteront dans le cache. En raison de la nature globale du cache, cet attribut peut être ajusté à partir de n’importe quel handle de connexion valide pour le pilote. Lorsque le cache TTL est réduite, des clés cek existant qui dépasserait la nouvelle durée de vie sont également supprimés. Si la valeur est 0, aucun clés cek n’est mis en cache.

### <a name="trusted-key-paths"></a>Chemins de clés approuvés

En commençant par le 17.1 de pilote ODBC pour SQL Server, le `SQL_COPT_SS_TRUSTEDCMKPATHS` attribut de connexion permet à une application exiger que les opérations Always Encrypted utilisent uniquement une liste de clés CMK, identifiés par leurs chemins d’accès de clé spécifiée. Par défaut, cet attribut est NULL, ce qui signifie que le pilote accepte n’importe quel chemin de clé. Pour utiliser cette fonctionnalité, définissez `SQL_COPT_SS_TRUSTEDCMKPATHS` pour pointer vers une chaîne à caractères larges délimitées en null, se terminant par null qui répertorie les chemins d’accès clé autorisées. La mémoire vers lequel pointée cet attribut doit rester valide pendant les opérations de chiffrement ou déchiffrement utilisant le handle de connexion sur lequel il a la valeur---sur laquelle le pilote vérifie si le chemin d’accès de la clé principale de colonne comme spécifié par les métadonnées du serveur indépendamment de la casse dans ce liste. Si le chemin d’accès de la clé principale de colonne n’est pas dans la liste, l’opération échoue. L’application peut modifier le contenu de la mémoire de que cet attribut pointe, pour modifier sa liste de clés CMK approuvés, sans redéfinir l’attribut.

## <a name="working-with-column-master-key-stores"></a>Utilisation de magasins de clés principales de colonne

Pour chiffrer ou déchiffrer des données, le pilote doit obtenir une clé CEK qui est configurée pour la colonne cible. Clés cek est stockés sous forme chiffrée (ECEKs) dans les métadonnées de base de données. Chaque clé CEK a une clé principale de colonne correspondante qui a été utilisé pour le chiffrement. Le [les métadonnées de base de données](../../t-sql/statements/create-column-master-key-transact-sql.md) ne stocke pas de la clé CMK lui-même ; il contient uniquement le nom du magasin de clés et des informations que le magasin de clés peut utiliser pour localiser la clé CMK.

Pour obtenir la valeur de texte en clair de l’un ECEK, le pilote obtient d’abord les métadonnées relatives à la clé CEK et sa clé principale de colonne correspondantes, et il utilise ces informations pour contacter le magasin de clés contenant la clé CMK, puis la demande pour déchiffrer l’ECEK. Le pilote communique avec un magasin de clés à l’aide d’un fournisseur de magasin de clés.

### <a name="built-in-keystore-providers"></a>Fournisseurs de magasin de clés intégré

Le pilote ODBC pour SQL Server est fourni avec les fournisseurs de magasin de clés intégrés suivants :

| Créer une vue d’abonnement | Description | Nom du fournisseur (métadonnées) |Disponibilité|
|:---|:---|:---|:---|
|Coffre de clé Azure |Clés de magasins CMK dans un coffre de clés Azure | `AZURE_KEY_VAULT` |Windows, macOS, Linux|
|Magasin de certificats Windows|Stocke les clés CMK localement dans le magasin de clés de Windows| `MSSQL_CERTIFICATE_STORE`|Windows|

- Vous (ou votre administrateur de base de données) devez vérifier que le nom du fournisseur (configuré dans les métadonnées de clé principale de colonne) est correct et que le chemin de la clé principale de colonne est conforme au format du chemin de clé pour le fournisseur donné. Il est recommandé de configurer les clés à l’aide d’outils tels que SQL Server Management Studio, qui génère automatiquement des noms de fournisseurs et des chemins de clés valides lors de l’émission de l’instruction [CREATE COLUMN MASTER KEY (Transact-SQL)](../../t-sql/statements/create-column-master-key-transact-sql.md) .

- Vous devez vérifier que votre application peut accéder à la clé dans le magasin de clés. Pour cela, vous devrez peut-être accorder à votre application l’accès à la clé et/ou au magasin de clés (selon le magasin de clés) ou effectuer d’autres étapes de configuration spécifiques au magasin de clés. Par exemple, pour accéder à un coffre de clés Azure, vous devez fournir les informations d’identification correctes pour le magasin de clés.

### <a name="using-the-azure-key-vault-provider"></a>Utilisation d’Azure Key Vault Provider

Azure Key Vault est un outil est très pratique qui permet de stocker et de gérer des clés principales de colonne Always Encrypted, en particulier si vos applications sont hébergées dans Azure. Le pilote ODBC pour SQL Server sur Linux, macOS et Windows inclut un fournisseur de magasin de clés principales de colonne intégré pour Azure Key Vault. Consultez [Azure Key Vault – étape par étape](https://blogs.technet.microsoft.com/kv/2015/06/02/azure-key-vault-step-by-step/), [bien démarrer avec Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-get-started/), et [création des clés de principales de colonne dans Azure Key Vault](https://msdn.microsoft.com/library/mt723359.aspx#Anchor_2) pour plus d’informations sur la configuration d’une clé Azure Coffre pour Always Encrypted.

> [!NOTE]
> Sur Linux et macOS, pour la version du pilote 17.2 et ultérieure, `libcurl` est nécessaire pour utiliser ce fournisseur, mais n’est pas une dépendance explicite dans la mesure où les autres opérations avec le pilote n’en avez pas besoin. Si vous rencontrez une erreur concernant `libcurl`, vérifiez qu’il est installé.

Le pilote prend en charge l’authentification auprès d’Azure Key Vault avec les types d’informations d’identification suivants :

- Nom d’utilisateur/mot de passe - avec cette méthode, les informations d’identification sont le nom d’un utilisateur Azure Active Directory et son mot de passe.

- ID de client/Secret - avec cette méthode, les informations d’identification sont un ID de client d’application et un secret d’application.

Pour autoriser le pilote à utiliser des clés CMK stockée dans AKV pour le chiffrement de colonne, utilisez les mots clés de chaîne de connexion uniquement suivants :

|Type d'informations d'identification| `KeyStoreAuthentication` |`KeyStorePrincipalId`| `KeyStoreSecret` |
|-|-|-|-|
|Nom d’utilisateur/mot de passe| `KeyVaultPassword`|Nom d’utilisateur principal|Mot de passe|
|ID de client/secret| `KeyVaultClientSecret`|ID client|Secret|

#### <a name="example-connection-strings"></a>Exemples de chaîne de connexion

Les chaînes de connexion suivantes montrent comment s’authentifier sur Azure Key Vault avec les deux types d’informations d’identification :

**ID de client/Secret**:

```
DRIVER=ODBC Driver 13 for SQL Server;SERVER=myServer;Trusted_Connection=Yes;DATABASE=myDB;ColumnEncryption=Enabled;KeyStoreAuthentication=KeyVaultClientSecret;KeyStorePrincipalId=<clientId>;KeyStoreSecret=<secret>
```

**Nom d’utilisateur/mot de passe**

```
DRIVER=ODBC Driver 13 for SQL Server;SERVER=myServer;Trusted_Connection=Yes;DATABASE=myDB;ColumnEncryption=Enabled;KeyStoreAuthentication=KeyVaultPassword;KeyStorePrincipalId=<username>;KeyStoreSecret=<password>
```

Aucune autre modification d’application ODBC n’est requis pour utiliser Azure Key VAULT pour le stockage de clés principales de colonne.

### <a name="using-the-windows-certificate-store-provider"></a>Avec le fournisseur du magasin de certificats Windows

Le pilote ODBC pour SQL Server sur Windows inclut un fournisseur de magasin de clé principale de colonne intégré pour le Store de certificat Windows nommé `MSSQL_CERTIFICATE_STORE`. (Ce fournisseur n’est pas disponible sur Mac OS ou Linux). Avec ce fournisseur, la clé principale de colonne sont stockées localement sur l’ordinateur client et aucune configuration supplémentaire par l’application n’est nécessaire pour l’utiliser avec le pilote. Toutefois, l’application doit avoir accès au certificat et sa clé privée dans le magasin. Pour plus d’informations, consultez [Créer et stocker des clés principales de colonne (Always Encrypted)](https://docs.microsoft.com/sql/relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted).

### <a name="using-custom-keystore-providers"></a>Utilisation de fournisseurs de magasins de clés personnalisés

Le pilote ODBC pour SQL Server prend également en charge les fournisseurs de magasin de clés tiers personnalisé à l’aide de l’interface CEKeystoreProvider. Cela permet à une application charger, requête et configurer les fournisseurs de magasin de clés afin qu’elles peuvent être utilisées par le pilote pour accéder aux colonnes chiffrées. Les applications peuvent également directement interagir avec un fournisseur de magasin de clés afin de chiffrer les clés cek pour le stockage dans SQL Server et effectuer des tâches au-delà de l’accès à des colonnes chiffrées avec ODBC ; Pour plus d’informations, consultez [fournisseurs de magasin de clés personnalisés](../../connect/odbc/custom-keystore-providers.md).

Deux attributs de connexion sont utilisés pour interagir avec les fournisseurs de magasin de clés personnalisé. Celles-ci sont les suivantes :

- `SQL_COPT_SS_CEKEYSTOREPROVIDER`

- `SQL_COPT_SS_CEKEYSTOREDATA`

Le premier est utilisé pour charger et d’énumérer les fournisseurs de magasin de clés chargé, tandis que ce dernier permet des communications de fournisseur de l’application. Ces attributs de connexion peuvent être utilisés à tout moment, avant ou après avoir établi une connexion, étant donné que l’interaction de fournisseurs d’application n’implique pas la communication avec SQL Server. Toutefois, étant donné que le pilote n’a pas encore été chargé, définition et obtention de ces attributs avant de se connecter entraînent à traiter par le Gestionnaire de pilotes et peut ne pas fournir les résultats attendus.

#### <a name="loading-a-keystore-provider"></a>Chargement d’un fournisseur de magasin de clés

Définition de la `SQL_COPT_SS_CEKEYSTOREPROVIDER` attribut de connexion permet à une application cliente pour charger une bibliothèque de fournisseur, mise à disposition à utiliser les fournisseurs de magasin de clés contenues dans celui-ci.

```
SQLRETURN SQLSetConnectAttr( SQLHDBC ConnectionHandle, SQLINTEGER Attribute, SQLPOINTER ValuePtr, SQLINTEGER StringLength);
```

| Argument | Description |
|:---|:---|
|`ConnectionHandle`|[Entrée] Handle de connexion. Doit être un handle de connexion valide, mais les fournisseurs chargés via un handle d’une seule connexion sont accessibles à partir de n’importe quel autre dans le même processus.|
|`Attribute`|[Entrée] Attribut à définir : le `SQL_COPT_SS_CEKEYSTOREPROVIDER` constante.|
|`ValuePtr`|[Entrée] Pointeur vers une chaîne de caractères se terminant par null spécifiant le nom de fichier de la bibliothèque du fournisseur. Pour SQLSetConnectAttrA, il s’agit d’une chaîne (multioctet) ANSI. Pour SQLSetConnectAttrW, il s’agit d’une chaîne Unicode (wchar_t).|
|`StringLength`|[Entrée] La longueur de la chaîne de ValuePtr, ou SQL_NTS.|

Le pilote tente de charger la bibliothèque identifiée par le paramètre ValuePtr à l’aide de la bibliothèque dynamique définie par la plateforme, mécanisme de chargement (`dlopen()` sur Linux et macOS, `LoadLibrary()` sur Windows), et ajoute tous les fournisseurs qui y sont définis à la liste des fournisseurs connus pour le pilote. Les erreurs suivantes peuvent se produire :

| Error | Description |
|:--|:--|
|`CE203`|La bibliothèque dynamique n’a pas pu être chargée.|
|`CE203`|Le symbole « CEKeyStoreProvider » exporté est introuvable dans la bibliothèque.|
|`CE203`|Un ou plusieurs fournisseurs dans la bibliothèque sont déjà chargés.|

`SQLSetConnectAttr` Renvoie l’erreur habituel ou valeurs de succès et des informations supplémentaires est disponible pour toutes les erreurs qui se sont produits par le biais du mécanisme de diagnostic ODBC standard.

> [!NOTE]
> Les programmeurs d’applications doivent garantir que des fournisseurs personnalisés sont chargés avant toute requête qui en a besoin est envoyé via une connexion. L’échec de cette opération entraîne l’erreur :

| Error | Description |
|:--|:--|
|`CE200`|Fournisseur keystore %1 est introuvable. Assurez-vous que la bibliothèque de fournisseur de magasin de clés appropriée a été chargée.|

> [!NOTE]
> Les implémenteurs de fournisseur de magasin de clés doivent éviter l’utilisation de `MSSQL` le nom de leurs fournisseurs personnalisés. Ce terme est réservé exclusivement à des fins de Microsoft et peut-être provoquer des conflits avec des fournisseurs intégrés futures. L’utilisation de ce terme dans le nom d’un fournisseur personnalisé peut entraîner un avertissement de ODBC.

#### <a name="getting-the-list-of-loaded-providers"></a>Obtention de la liste des fournisseurs chargés

Obtention de cet attribut de connexion permet à une application de client déterminer les fournisseurs de magasin de clés actuellement chargés dans le pilote (y compris celles créées.) Cela peut uniquement être effectuée après la connexion.

```
SQLRETURN SQLGetConnectAttr( SQLHDBC ConnectionHandle, SQLINTEGER Attribute, SQLPOINTER ValuePtr, SQLINTEGER BufferLength, SQLINTEGER * StringLengthPtr);
```

| Argument | Description |
|:---|:---|
|`ConnectionHandle`|[Entrée] Handle de connexion. Doit être un handle de connexion valide, mais les fournisseurs chargés via un handle d’une seule connexion sont accessibles à partir de n’importe quel autre dans le même processus.|
|`Attribute`|[Entrée] Attribut à récupérer : le `SQL_COPT_SS_CEKEYSTOREPROVIDER` constante.|
|`ValuePtr`|[Sortie] Pointeur vers la mémoire dans lequel retourner le nom du fournisseur chargé suivant.|
|`BufferLength`|[Entrée] La longueur de la mémoire tampon ValuePtr.|
|`StringLengthPtr`|[Sortie] Un pointeur vers une mémoire tampon dans lequel retourner le nombre total d’octets (sans le caractère de fin de la valeur null) disponibles à renvoyer dans \*ValuePtr. Si ValuePtr est un pointeur null, aucune longueur n’est retournée. Si la valeur d’attribut est une chaîne de caractères et le nombre d’octets à retourner est supérieur à BufferLength moins la longueur de l’arrêt de valeur null, les données caractères dans \*ValuePtr est tronqué à BufferLength moins la longueur de la caractère de fin de la valeur null et est terminée par le pilote.|

Pour permettre la récupération de la liste complète, chaque opération Get retourne le nom du fournisseur actuel et incrémente un compteur interne à la suivante. Une fois que ce compteur atteint la fin de la liste, une chaîne vide (" ») est retournée, et le compteur est réinitialisé ; les opérations Get successives passez ensuite à nouveau à partir du début de la liste.

### <a name="communicating-with-keystore-providers"></a>Communication avec les fournisseurs de magasin de clés

Le `SQL_COPT_SS_CEKEYSTOREDATA` attribut de connexion permet à une application client communiquer avec les fournisseurs de magasin de clés chargé pour la configuration des paramètres supplémentaires, etc. de génération de clés. La communication entre une application cliente et un fournisseur suit un protocole de demande-réponse simple, basé sur Get et Set demande à l’aide de cet attribut de connexion. La communication est établie uniquement par l’application cliente.

> [!NOTE]
> En raison de la nature de ODBC appelle répondre de CEKeyStoreProvider à (SQLGet/SetConnectAttr), le ODBC interface prend uniquement en charge la définition de données à la résolution du contexte de connexion.

L’application communique avec les fournisseurs de magasin de clés via le pilote par le biais de la structure CEKeystoreData :

```
typedef struct CEKeystoreData {
wchar_t *name;
unsigned int dataSize;
char data[];
} CEKEYSTOREDATA;
```

| Argument | Description |
|:---|:---|
|`name`|[Entrée] Fonction Set, le nom du fournisseur pour lequel les données sont envoyées. Ignoré sur Get. Chaîne se terminant par null, les caractères larges.|
|`dataSize`|[Entrée] La taille du tableau de données suivant de la structure.|
|`data`|[InOut] Lors de l’ensemble, les données à envoyer au fournisseur. Il peut s’agir des données arbitraires ; le pilote n’effectue aucune tentative de l’interpréter. Fonction Get, la mémoire tampon pour recevoir les données lire à partir du fournisseur.|

#### <a name="writing-data-to-a-provider"></a>Écriture de données à un fournisseur

Un `SQLSetConnectAttr` appeler à l’aide de la `SQL_COPT_SS_CEKEYSTOREDATA` attribut écrit un « paquet » de données dans le fournisseur de magasin de clés spécifié.
```
SQLRETURN SQLSetConnectAttr( SQLHDBC ConnectionHandle, SQLINTEGER Attribute, SQLPOINTER ValuePtr, SQLINTEGER StringLength);
```

| Argument | Description |
|:---|:---|
|`ConnectionHandle`| [Entrée] Handle de connexion. Doit être un handle de connexion valide, mais les fournisseurs chargés via un handle d’une seule connexion sont accessibles à partir de n’importe quel autre dans le même processus.|
|`Attribute`|[Entrée] Attribut à définir : le `SQL_COPT_SS_CEKEYSTOREDATA` constante.|
|`ValuePtr`|[Entrée] Pointeur vers une structure CEKeystoreData. Le champ nom de la structure identifie le fournisseur pour lequel les données sont prévues.|
|`StringLength`|[Entrée] Constante SQL_IS_POINTER|

Informations d’erreur détaillées supplémentaires peuvent être obtenues [SQLGetDiacRec](https://msdn.microsoft.com/library/ms710921(v=vs.85).aspx).

> [!NOTE]
> Le fournisseur peut utiliser le handle de connexion pour associer les données écrites pour une connexion spécifique, si cela est souhaitable. Cela est utile pour implémenter la configuration de chaque connexion. Il peut également ignorer le contexte de connexion et de traiter les données de façon identique quel que soit la connexion utilisée pour envoyer les données. Consultez [Association de contexte](../../connect/odbc/custom-keystore-providers.md#context-association) pour plus d’informations.

#### <a name="reading-data-from-a-provider"></a>Lecture des données à partir d’un fournisseur

Un appel à `SQLGetConnectAttr` à l’aide de la `SQL_COPT_SS_CEKEYSTOREDATA` attribut lit un « paquet » de données à partir de *le dernier-écrites-to* fournisseur. S’il en existait aucun, une erreur de séquence de fonction se produit. Les implémenteurs de fournisseur de magasin de clés sont encouragés à prendre en charge « dummy écrit » de 0 octet comme un moyen de la sélection du fournisseur pour les opérations de lecture sans provoquer d’autres effets secondaires, si cela est pertinent pour ce faire.

```
SQLRETURN SQLGetConnectAttr( SQLHDBC ConnectionHandle, SQLINTEGER Attribute, SQLPOINTER ValuePtr, SQLINTEGER BufferLength, SQLINTEGER * StringLengthPtr);
```

| Argument | Description |
|:---|:---|
|`ConnectionHandle`|[Entrée] Handle de connexion. Doit être un handle de connexion valide, mais les fournisseurs chargés via un handle d’une seule connexion sont accessibles à partir de n’importe quel autre dans le même processus.|
|`Attribute`|[Entrée] Attribut à récupérer : le `SQL_COPT_SS_CEKEYSTOREDATA` constante.|
|`ValuePtr`|[Sortie] Pointeur vers une structure CEKeystoreData dans lequel les données lues à partir du fournisseur sont placées.|
|`BufferLength`|[Entrée] Constante SQL_IS_POINTER|
|`StringLengthPtr`|[Sortie] Un pointeur vers une mémoire tampon dans lequel retourner BufferLength. Si * ValuePtr est un pointeur null, aucune longueur n’est retournée.|

L’appelant doit garantir qu’une mémoire tampon de longueur suffisante suivant la structure CEKEYSTOREDATA est allouée pour le fournisseur à écrire dans. Au retour, son champ dataSize est mis à jour avec la longueur réelle des données lues à partir du fournisseur. Informations d’erreur détaillées supplémentaires peuvent être obtenues [SQLGetDiacRec](https://msdn.microsoft.com/library/ms710921(v=vs.85).aspx).

Cette interface ne place aucune exigence supplémentaire sur le format des données transférées entre une application et un fournisseur de magasin de clés. Chaque fournisseur peut définir son propre format de protocole/data, en fonction de ses besoins.

Pour obtenir un exemple d’implémentation de votre propre fournisseur de magasin de clés, consultez [fournisseurs de magasin de clés personnalisés](../../connect/odbc/custom-keystore-providers.md)

## <a name="limitations-of-the-odbc-driver-when-using-always-encrypted"></a>Limitations du pilote ODBC lors de l’utilisation de Always Encrypted

### <a name="asynchronous-operations"></a>Opérations asynchrones
Bien que le pilote ODBC autorise l’utilisation de [opérations asynchrones](../../relational-databases/native-client/odbc/creating-a-driver-application-asynchronous-mode-and-sqlcancel.md) avec Always Encrypted, a un impact sur les performances lors des opérations d’Always Encrypted est activé. L’appel à `sys.sp_describe_parameter_encryption` pour déterminer les métadonnées de chiffrement pour l’instruction bloque et entraîne le pilote d’attente pour le serveur retourner les métadonnées avant de retourner `SQL_STILL_EXECUTING`.

### <a name="retrieve-data-in-parts-with-sqlgetdata"></a>Récupérer une partie des données avec SQLGetData
Avant la version 17 du pilote ODBC pour SQL Server, il n’est pas possible de récupérer une partie des colonnes binaires et des caractères chiffrés avec SQLGetData. Un seul appel de SQLGetData est possible, avec une mémoire tampon de taille suffisante pour contenir la totalité des données de la colonne.

### <a name="send-data-in-parts-with-sqlputdata"></a>Envoyer une partie des données avec SQLPutData
Il n’est pas possible d’envoyer une partie des données à des fins de comparaison ou d’insertion avec SQLPutData. Un seul appel à SQLPutData est possible, avec une mémoire tampon contenant la totalité des données. Pour insérer des données de type long dans des colonnes chiffrées, utilisez l’API de copie en bloc, décrite dans la section suivante, avec un fichier de données d’entrée.

### <a name="encrypted-money-and-smallmoney"></a>Colonnes money et smallmoney chiffrées
Les paramètres ne peuvent pas cibler les colonnes **money** et **smallmoney**, car il n’existe aucun type de données ODBC correspondant spécifiquement à ces types, ce qui provoque des erreurs de conflit de type opérande.

## <a name="bulk-copy-of-encrypted-columns"></a>Copie en bloc de colonnes chiffrées

Les [fonctions de copie en bloc SQL](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md) et l’utilitaire **bcp** sont pris en charge avec Always Encrypted depuis la version 17 du pilote ODBC pour SQL Server. Le texte en clair (chiffré lors de l’insertion et déchiffré lors de la récupération) et le texte chiffré (transféré textuellement) peuvent être insérés et récupérés à l’aide des API de copie en bloc (bcp_&#42;) et de l’utilitaire **bcp**.

- Pour récupérer du texte chiffré au format varbinary(max) (par exemple, pour le chargement en masse dans une autre base de données), connectez-vous sans l’option `ColumnEncryption` (ou en lui donnant la valeur `Disabled`) et effectuez une opération BCP OUT.

- Pour insérer et récupérer du texte clair et laisser le pilote effectuer en toute transparence le chiffrement et le déchiffrement, il suffit de donner la valeur `Enabled` à `ColumnEncryption`. Les fonctionnalités de l’API BCP restent inchangées par ailleurs.

- Pour insérer du texte chiffré au format varbinary(max) (tel qu’il a été récupéré ci-dessus, par exemple), donnez la valeur TRUE à l’option `BCPMODIFYENCRYPTED` et effectuez une opération BCP IN. Pour que les données résultantes soient déchiffrables, la clé CEK de la colonne de destination doit être la même que celle avec laquelle le texte chiffré a été obtenu à l’origine.

Lorsque vous utilisez le **bcp** utilitaire : Pour contrôler la `ColumnEncryption` configuration, utilisez l’option -D et spécifier une source de données contenant la valeur souhaitée. Pour insérer du texte chiffré, vérifiez le `ALLOW_ENCRYPTED_VALUE_MODIFICATIONS` de l’utilisateur est activée.

Le tableau suivant fournit un résumé des actions lorsqu’il fonctionne sur une colonne chiffrée :

|`ColumnEncryption`|Direction BCP|Description|
|----------------|-------------|-----------|
|`Disabled`|OUT (au client)|Récupère le texte chiffré. Le type de données observée est **varbinary (max)**.|
|`Enabled`|OUT (au client)|Récupère le texte en clair. Le pilote déchiffre les données de colonne.|
|`Disabled`|IN (sur le serveur)|Insère le texte chiffré. Cela vise de manière opaque déplacement des données chiffrées sans l’exiger pour être déchiffrée. L’opération échoue si le `ALLOW_ENCRYPTED_VALUE_MODIFICATIONS` option n’est pas définie sur l’utilisateur ou BCPMODIFYENCRYPTED n’est pas définie sur le handle de connexion. Pour plus d’informations, voir ci-dessous.|
|`Enabled`|IN (sur le serveur)|Insère le texte en clair. Le pilote chiffre les données de colonne.|

### <a name="the-bcpmodifyencrypted-option"></a>L’option BCPMODIFYENCRYPTED

Pour empêcher la corruption de données, le serveur normalement n’autorise pas l’insertion de texte chiffré directement dans une colonne chiffrée, et par conséquent, toute tentative de modification échoue ; Toutefois, pour le chargement en bloc des données chiffrées à l’aide de l’API BCP, en définissant le `BCPMODIFYENCRYPTED` [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) option sur TRUE permettra de texte chiffré à insérer directement et réduit le risque d’endommager les données chiffrées sur un paramètre de la `ALLOW_ENCRYPTED_VALUE_MODIFICATIONS` option sur le compte d’utilisateur. Néanmoins, les clés doivent correspondre aux données et il est judicieux d’effectuer des vérifications en lecture seule des données insérées après l’insertion en bloc et avant une utilisation ultérieure.

Pour plus d’informations, consultez [Migrer des données sensibles protégées par Always Encrypted](../../relational-databases/security/encryption/migrate-sensitive-data-protected-by-always-encrypted.md).

## <a name="always-encrypted-api-summary"></a>Résumé de l’API Always Encrypted

### <a name="connection-string-keywords"></a>Mots clés de chaîne de connexion

|Créer une vue d’abonnement|Description|  
|----------|-----------------|  
|`ColumnEncryption`|Valeurs acceptées sont `Enabled` / `Disabled`.<br>`Enabled` : active la fonctionnalité Always Encrypted pour la connexion.<br>`Disabled` : désactive la fonctionnalité Always Encrypted pour la connexion. <br><br>La valeur par défaut est `Disabled`.|  
|`KeyStoreAuthentication` | Valeurs valides : `KeyVaultPassword`, `KeyVaultClientSecret` |
|`KeyStorePrincipalId` | Lorsque `KeyStoreAuthentication`  =  `KeyVaultPassword`, définissez cette valeur sur un nom Principal d’utilisateur Active Directory de Azure valide. <br>Lorsque `KeyStoreAuthetication`  =  `KeyVaultClientSecret` définir cette valeur sur un Azure Active Directory Application ID Client valide |
|`KeyStoreSecret` | Lorsque `KeyStoreAuthentication`  =  `KeyVaultPassword` définir cette valeur au mot de passe pour le nom d’utilisateur correspondant. <br>Lorsque `KeyStoreAuthentication`  =  `KeyVaultClientSecret` définir cette valeur sur le Secret d’Application associé à un Azure Active Directory Application ID Client valide|

### <a name="connection-attributes"></a>Attributs de connexion

|Créer une vue d’abonnement|Type|Description|  
|----------|-------|----------|  
|`SQL_COPT_SS_COLUMN_ENCRYPTION`|Précédant la connexion|`SQL_COLUMN_ENCRYPTION_DISABLE` (0)--désactiver Always Encrypted <br>`SQL_COLUMN_ENCRYPTION_ENABLE` (1)--activer le chiffrement intégral|
|`SQL_COPT_SS_CEKEYSTOREPROVIDER`|Post-connexion|[Valeur] Tentative de chargement CEKeystoreProvider<br>[Get] Retourner un nom CEKeystoreProvider|
|`SQL_COPT_SS_CEKEYSTOREDATA`|Post-connexion|[Valeur] Écrire des données dans CEKeystoreProvider<br>[Get] Lire les données à partir de CEKeystoreProvider|
|`SQL_COPT_SS_CEKCACHETTL`|Post-connexion|[Valeur] Définir la durée de vie du cache CEK<br>[Get] Récupérer le cache actuel de la clé CEK TTL|
|`SQL_COPT_SS_TRUSTEDCMKPATHS`|Post-connexion|[Valeur] Définir le pointeur de chemins d’accès CMK approuvé<br>[Get] Obtenir le pointeur de chemins d’accès CMK approuvé en cours|

### <a name="statement-attributes"></a>Attributs d'instruction

|Créer une vue d’abonnement|Description|  
|----------|-----------------|  
|`SQL_SOPT_SS_COLUMN_ENCRYPTION`|`SQL_CE_DISABLED` (0)--always Encrypted est désactivé pour l’instruction <br>`SQL_CE_RESULTSETONLY` (1)--uniquement le déchiffrement. Jeux de résultats et valeurs de retour sont déchiffrées et les paramètres ne sont pas chiffrés. <br>`SQL_CE_ENABLED` (3)--always Encrypted est activé et utilisé pour les paramètres et les résultats|

### <a name="descriptor-fields"></a>Champs de descripteur

|Champ IPD|Taille et le Type|Valeur par défaut|Description|
|-|-|-|-|  
|`SQL_CA_SS_FORCE_ENCRYPT` (1236)|WORD (2 octets)|0|Lorsque 0 (valeur par défaut) : la décision pour chiffrer ce paramètre est déterminée par la disponibilité des métadonnées de chiffrement.<br><br>Lorsqu’elle est différente de zéro : si les métadonnées de chiffrement sont disponible pour ce paramètre, il est chiffré. Sinon, la demande échoue avec l’erreur [CE300] chiffrement obligatoire [Microsoft] [ODBC Driver 13 pour SQL Server] a été spécifié pour un paramètre, mais aucune métadonnée de chiffrement a été fournie par le serveur.|

### <a name="bcpcontrol-options"></a>Options de bcp_control

|Nom d’option|Valeur par défaut|Description|
|-|-|-|
|`BCPMODIFYENCRYPTED` (21)|FALSE|Lorsque la valeur est TRUE, autorise les valeurs varbinary (max) à insérer dans une colonne chiffrée. Si la valeur est FALSE, empêche l’insertion, sauf si les métadonnées correctes de type et le chiffrement sont fournie.|

## <a name="see-also"></a> Voir aussi

- [Always Encrypted (moteur de base de données)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Blog sur Always Encrypted](https://blogs.msdn.com/b/sqlsecurity/archive/tags/always-encrypted/)


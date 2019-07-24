---
title: Azure Active Directory | Microsoft Docs
ms.date: 02/25/2019
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- azure active directory, authentication, access token
author: david-puglielli
ms.author: v-dapugl
manager: v-mabarw
ms.openlocfilehash: 8712681a244e969d230b0b7099acd4aa56334f11
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265178"
---
# <a name="connect-using-azure-active-directory-authentication"></a>Se connecter à l’aide de l’authentification Azure Active Directory
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-whatis) (Azure AD) est une technologie de gestion des ID d’utilisateur centrale qui fonctionne comme alternative à [l’authentification SQL Server](../../connect/php/how-to-connect-using-sql-server-authentication.md). Azure AD permet les connexions à Microsoft Azure SQL Database et SQL Data Warehouse avec des identités fédérées dans Azure AD à l’aide d’un nom d’utilisateur et d’un mot de passe, de l’authentification intégrée de Windows ou d’un jeton d’accès Azure AD. Les pilotes PHP pour SQL Server offrent une prise en charge partielle de ces fonctionnalités.

Pour utiliser Azure ad, utilisez les **mots** clés **Authentication ou AccessToken** (ils s’excluent mutuellement), comme indiqué dans le tableau suivant. Pour plus d’informations techniques, reportez-vous à [la rubrique utilisation de Azure Active Directory avec le pilote ODBC](../../connect/odbc/using-azure-active-directory.md).

|Mot clé|Valeurs|Description|
|-|-|-|
|**AccessToken**|Non défini (valeur par défaut)|Mode d’authentification déterminé par les autres mots clés. Pour plus d’informations, consultez [Connection Options](../../connect/php/connection-options.md). |
||Chaîne d’octets|Le jeton d’accès Azure AD extrait d’une réponse JSON OAuth. La chaîne de connexion ne doit pas contenir l’ID d’utilisateur, le mot de passe ou le mot clé d’authentification (requiert le pilote ODBC version 17 ou ultérieure dans Linux ou macOS). |
|**Authentification**|Non défini (valeur par défaut)|Mode d’authentification déterminé par les autres mots clés. Pour plus d’informations, consultez [Connection Options](../../connect/php/connection-options.md). |
||`SqlPassword`|S’authentifier directement auprès d’une instance de SQL Server (qui peut être une instance Azure) à l’aide d’un nom d’utilisateur et d’un mot de passe. Le nom d’utilisateur et le mot de passe doivent être transmis à la chaîne de connexion à l’aide des mots clés **UID** et **PWD** . |
||`ActiveDirectoryPassword`|S’authentifier avec une identité Azure Active Directory à l’aide d’un nom d’utilisateur et d’un mot de passe. Le nom d’utilisateur et le mot de passe doivent être transmis à la chaîne de connexion à l’aide des mots clés **UID** et **PWD** . |
||`ActiveDirectoryMsi`|Authentifiez-vous à l’aide d’une identité gérée affectée par le système ou d’une identité gérée affectée par l’utilisateur (nécessite le pilote ODBC version 17.3.1.1 ou ultérieure). Pour obtenir une vue d’ensemble et des didacticiels, consultez [qu’est-ce que les identités gérées pour les ressources Azure?](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview).|

Le **mot** clé Authentication affecte les paramètres de sécurité de la connexion. S’il est défini dans la chaîne de connexion, par défaut, le mot clé **Encrypt** est défini sur true, ce qui signifie que le client demande un chiffrement. En outre, le certificat de serveur sera validé, quel que soit le paramètre de chiffrement, sauf si **TrustServerCertificate** a la valeur true (**false** par défaut). Cette fonctionnalité est distinguée de l’ancienne méthode de connexion moins sécurisée, dans laquelle le certificat de serveur est validé uniquement lorsque le chiffrement est spécifiquement demandé dans la chaîne de connexion.

Lorsque vous utilisez Azure AD avec les pilotes PHP pour SQL Server sur Windows, vous pouvez être invité à installer l' [Assistant de connexion Microsoft Online Services](https://www.microsoft.com/download/details.aspx?id=41950) (non requis pour ODBC 17 +).

#### <a name="limitations"></a>Limitations

Sur Windows, le pilote ODBC sous-jacent prend en charge une  valeur supplémentaire pour le mot clé **Authentication**, **ActiveDirectoryIntegrated**, mais les pilotes php ne prennent pas en charge cette valeur sur n’importe quelle plateforme.

## <a name="example---connect-using-sqlpassword-and-activedirectorypassword"></a>Exemple: connexion à l’aide de SqlPassword et ActiveDirectoryPassword

```php
<?php
// First connect to a local SQL Server instance by setting Authentication to SqlPassword
$serverName = "myserver.mydomain";

$connectionInfo = array("UID"=>$myusername, "PWD"=>$mypassword, "Authentication"=>'SqlPassword');

$conn = sqlsrv_connect($serverName, $connectionInfo);
if ($conn === false) {
    echo "Could not connect with Authentication=SqlPassword.\n";
    print_r(sqlsrv_errors());
} else {
    echo "Connected successfully with Authentication=SqlPassword.\n";
    sqlsrv_close($conn);
}

// Now connect to an Azure SQL database by setting Authentication to ActiveDirectoryPassword
$azureServer = "myazureserver.database.windows.net";
$azureDatabase = "myazuredatabase";
$azureUsername = "myuid";
$azurePassword = "mypassword";
$connectionInfo = array("Database"=>$azureDatabase,
                        "UID"=>$azureUsername,
                        "PWD"=>$azurePassword,
                        "Authentication"=>'ActiveDirectoryPassword');

$conn = sqlsrv_connect($azureServer, $connectionInfo);
if ($conn === false) {
    echo "Could not connect with Authentication=ActiveDirectoryPassword.\n";
    print_r(sqlsrv_errors());
} else {
    echo "Connected successfully with Authentication=ActiveDirectoryPassword.\n";
    sqlsrv_close($conn);
}

?>
```

## <a name="example---connect-using-the-pdosqlsrv-driver"></a>Exemple-se connecter à l’aide du pilote PDO_SQLSRV

```php
<?php
// First connect to a local SQL Server instance by setting Authentication to SqlPassword
$serverName = "myserver.mydomain";

$connectionInfo = "Database = $databaseName; Authentication = SqlPassword;";

try {
    $conn = new PDO("sqlsrv:server = $serverName ; $connectionInfo", $myusername, $mypassword);
    echo "Connected successfully with Authentication=SqlPassword.\n";
    $conn = null;
} catch (PDOException $e) {
    echo "Could not connect with Authentication=SqlPassword.\n";
    print_r($e->getMessage());
    echo "\n";
}

// Now connect to an Azure SQL database by setting Authentication to ActiveDirectoryPassword
$azureServer = "myazureserver.database.windows.net";
$azureDatabase = "myazuredatabase";
$azureUsername = "myuid";
$azurePassword = "mypassword";
$connectionInfo = "Database = $azureDatabase; Authentication = ActiveDirectoryPassword;";

try {
    $conn = new PDO("sqlsrv:server = $azureServer ; $connectionInfo", $azureUsername, $azurePassword);
    echo "Connected successfully with Authentication=ActiveDirectoryPassword.\n";
    unset($conn);
} catch (PDOException $e) {
    echo "Could not connect with Authentication=ActiveDirectoryPassword.\n";
    print_r($e->getMessage());
    echo "\n";
}
?>
```

## <a name="example---connect-using-azure-ad-access-token"></a>Exemple: connexion à l’aide d’un jeton d’accès Azure AD

### <a name="sqlsrv-driver"></a>Pilote SQLSRV

```php
<?php
// Using an access token to connect: do not use UID or PWD connection options
// Assume $accToken is the valid byte string extracted from an OAuth JSON response
$connectionInfo = array("Database"=>$azureAdDatabase, "AccessToken"=>$accToken);
$conn = sqlsrv_connect($azureAdServer, $connectionInfo);
if ($conn === false) {
    echo "Could not connect with Azure AD Access Token.\n";
    print_r(sqlsrv_errors());
} else {
    echo "Connected successfully with Azure AD Access Token.\n";
    sqlsrv_close($conn);
}
?>
```

### <a name="pdosqlsrv-driver"></a>Pilote PDO_SQLSRV

```php
<?php
try {
    // Using an access token to connect: do not pass in $uid or $pwd
    // Assume $accToken is the valid byte string extracted from an OAuth JSON response
    $connectionInfo = "Database = $azureAdDatabase; AccessToken = $accToken;";
    $conn = new PDO("sqlsrv:server = $azureAdServer; $connectionInfo");
    echo "Connected successfully with Azure AD Access Token\n";
    unset($conn);
} catch (PDOException $e) {
    echo "Could not connect with Azure AD Access Token.\n";
    print_r($e->getMessage());
    echo "\n";
}
?>
```

## <a name="example---connect-using-managed-identities-for-azure-resources"></a>Exemple: connexion à l’aide d’identités gérées pour les ressources Azure

### <a name="using-the-system-assigned-managed-identity-with-sqlsrv-driver"></a>Utilisation de l’identité gérée assignée par le système avec le pilote SQLSRV

Quand vous vous connectez à l’aide de l’identité gérée affectée par le système, n’utilisez pas les options UID ou PWD.

```php
<?php

$azureServer = 'myazureserver.database.windows.net';
$azureDatabase = 'myazuredatabase';
$connectionInfo = array('Database'=>$azureDatabase,
                        'Authentication'=>'ActiveDirectoryMsi');
$conn = sqlsrv_connect($azureServer, $connectionInfo);

if ($conn === false) {
    echo "Could not connect with Authentication=ActiveDirectoryMsi (system-assigned).\n";
    print_r(sqlsrv_errors());
} else {
    echo "Connected successfully with Authentication=ActiveDirectoryMsi (system-assigned).\n";
    
    $tsql = "SELECT @@Version AS SQL_VERSION";
    $stmt = sqlsrv_query($conn, $tsql);
    if ($stmt === false) {
        echo "Failed to run the simple query (system-assigned).\n";
        print_r(sqlsrv_errors());
    } else {
        while ($row = sqlsrv_fetch_array($stmt, SQLSRV_FETCH_ASSOC)) {
            echo $row['SQL_VERSION'] . PHP_EOL;
        }

        sqlsrv_free_stmt($stmt);
    }
    
    sqlsrv_close($conn);
}
?>
```

### <a name="using-the-user-assigned-managed-identity-with-pdosqlsrv-driver"></a>Utilisation de l’identité gérée affectée par l’utilisateur avec le pilote PDO_SQLSRV

Une identité gérée affectée par l’utilisateur est créée en tant que ressource Azure autonome. Azure crée une identité dans le locataire Azure AD qui est approuvé par l’abonnement en cours d’utilisation. Une fois l’identité créée, l’identité peut être affectée à une ou plusieurs instances de service Azure. Copiez `Object ID` le de cette identité et définissez-le en tant que nom d’utilisateur dans la chaîne de connexion. 

Par conséquent, lors de la connexion à l’aide de l’identité gérée affectée par l’utilisateur, fournissez l’ID d’objet comme nom d’utilisateur, mais omettez le mot de passe.

```php
<?php

$azureServer = 'myazureserver.database.windows.net';
$azureDatabase = 'myazuredatabase';
$azureUser = '2d68f56e-9547-4dae-aee8-f3g28ab9674x';    // Object ID of the identity
$connectionInfo = "Database = $azureDatabase; Authentication = ActiveDirectoryMsi;";

try {
    $conn = new PDO("sqlsrv:server = $azureServer; $connectionInfo", $azureUser);
    echo "Connected successfully with Authentication=ActiveDirectoryMsi (user-assigned).\n";
    
    $tsql = "SELECT @@Version AS SQL_VERSION";
    
    try {
        $stmt = $conn->query($tsql);
        $result = $stmt->fetchall(PDO::FETCH_ASSOC);
        print_r($result);

        unset($stmt);
    } catch (PDOException $e) {
        echo "Failed to run the simple query (user-assigned).\n";
    }
    unset($conn);
} catch (PDOException $e) {
    echo "Could not connect with Authentication=ActiveDirectoryMsi (user-assigned).\n";
    print_r($e->getMessage());
    echo "\n";
}
?>
```

## <a name="see-also"></a>Voir aussi
[Utilisation d’Azure Active Directory avec ODBC Driver](https://docs.microsoft.com/sql/connect/odbc/using-azure-active-directory)

[Qu’est-ce que les identités gérées pour les ressources Azure?](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview)

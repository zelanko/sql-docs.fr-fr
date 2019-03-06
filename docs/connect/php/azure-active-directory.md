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
manager: mbarwin
ms.openlocfilehash: 30423cd7c15a920d99fad4c0ea08e074beaece0b
ms.sourcegitcommit: 8664c2452a650e1ce572651afeece2a4ab7ca4ca
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56828049"
---
# <a name="connect-using-azure-active-directory-authentication"></a>Se connecter à l’aide de l’authentification Azure Active Directory
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-whatis) (Azure AD) est une technologie de gestion d’ID utilisateur central qui fonctionne comme une alternative à [l’authentification SQL Server](../../connect/php/how-to-connect-using-sql-server-authentication.md). Azure AD autorise les connexions à Microsoft Azure SQL Database et SQL Data Warehouse avec des identités fédérées dans Azure AD à l’aide d’un nom d’utilisateur et mot de passe, l’authentification intégrée Windows ou un jeton d’accès Azure AD. Les pilotes PHP pour SQL Server offrent une prise en charge partielle de ces fonctionnalités.

Pour utiliser Azure AD, utilisez le **authentification** ou **AccessToken** mots clés (ils sont mutuellement exclusifs), comme indiqué dans le tableau suivant. Pour plus de détails techniques, reportez-vous à [à l’aide de Azure Active Directory avec le pilote ODBC](../../connect/odbc/using-azure-active-directory.md).

|Mot clé|Valeurs|Description|
|-|-|-|
|**AccessToken**|Pas définie (valeur par défaut)|Mode d’authentification déterminé par les autres mots clés. Pour plus d’informations, consultez [Connection Options](../../connect/php/connection-options.md). |
||Une chaîne d’octets|Azure AD Access Token extraites à partir d’une réponse OAuth JSON. La chaîne de connexion ne doit pas contenir les ID utilisateur, mot de passe ou le mot clé d’authentification (nécessite le pilote ODBC version 17 ou version ultérieure dans Linux ou macOS). |
|**Authentification**|Pas définie (valeur par défaut)|Mode d’authentification déterminé par les autres mots clés. Pour plus d’informations, consultez [Connection Options](../../connect/php/connection-options.md). |
||`SqlPassword`|S’authentifier directement à une instance de SQL Server (qui peut être une instance Azure) à l’aide d’un nom d’utilisateur et le mot de passe. Le nom d’utilisateur et le mot de passe doivent être passés dans la chaîne de connexion en utilisant le **UID** et **PWD** mots clés. |
||`ActiveDirectoryPassword`|S’authentifier avec une identité Azure Active Directory à l’aide d’un nom d’utilisateur et le mot de passe. Le nom d’utilisateur et le mot de passe doivent être passés dans la chaîne de connexion en utilisant le **UID** et **PWD** mots clés. |
||`ActiveDirectoryMsi`|S’authentifier à l’aide d’une identité gérée attribué par le système ou une identité gérée affectée à l’utilisateur (nécessite le pilote ODBC version 17.3.1.1 ou version ultérieure). Pour une vue d’ensemble et didacticiels, reportez-vous à [What ' s des identités gérées pour les ressources Azure ?](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview).|

Le **authentification** mot clé affecte les paramètres de sécurité de connexion. Si elle est définie dans la chaîne de connexion, puis par défaut le **Encrypt** mot clé est définie sur true, ce qui signifie que le client demande le chiffrement. En outre, le certificat de serveur sera validé, quel que soit le paramètre de chiffrement, sauf si **TrustServerCertificate** est définie sur true (**false** par défaut). Cette fonctionnalité se distingue de l’ancienne, moins la méthode de connexion sécurisée, dans lequel le certificat de serveur est validé uniquement lorsque le chiffrement est spécifiquement demandé dans la chaîne de connexion.

Lorsque vous utilisez Azure AD avec les pilotes PHP pour SQL Server sur Windows, vous pouvez être invité à installer le [Assistant Microsoft Online Services Sign-In](https://www.microsoft.com/download/details.aspx?id=41950) (non requis pour ODBC 17 +).

#### <a name="limitations"></a>Limitations

Sur Windows, le pilote ODBC sous-jacent prend en charge davantage de valeur pour le **authentification** mot clé, **ActiveDirectoryIntegrated**, mais les pilotes PHP ne prennent pas en charge cette valeur sur n’importe quelle plateforme.

## <a name="example---connect-using-sqlpassword-and-activedirectorypassword"></a>Exemple - se connecter à l’aide de SqlPassword et ActiveDirectoryPassword

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

## <a name="example---connect-using-the-pdosqlsrv-driver"></a>Exemple - se connecter en utilisant le pilote PDO_SQLSRV

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

## <a name="example---connect-using-azure-ad-access-token"></a>Exemple - se connecter à l’aide du jeton d’accès Azure AD

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

## <a name="example---connect-using-managed-identities-for-azure-resources"></a>Exemple - se connecter à l’aide d’identités gérées pour les ressources Azure

### <a name="using-the-system-assigned-managed-identity-with-sqlsrv-driver"></a>À l’aide de l’identité gérée attribué par le système avec le pilote SQLSRV

Lors de la connexion à l’aide de l’objet affecté par le système géré identité, n’utilisez pas les options UID et PWD.

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

### <a name="using-the-user-assigned-managed-identity-with-pdosqlsrv-driver"></a>À l’aide de l’identité gérée affectée à l’utilisateur avec le pilote PDO_SQLSRV

Une identité gérée affectée à l’utilisateur est créée comme une ressource Azure autonome. Azure crée une identité dans le locataire Azure AD qui est approuvé par l’abonnement en cours d’utilisation. Une fois que l’identité est créée, l’identité peut avoir pour une ou plusieurs instances de service Azure. Copie le `Object ID` de cette identité et d’un ensemble en tant que l’utilisateur nom dans la chaîne de connexion. 

Par conséquent, lors de la connexion à l’aide de l’utilisateur affecté, identité gérée, fournissez l’ID d’objet en tant que le nom d’utilisateur, mais omettez le mot de passe.

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

## <a name="see-also"></a> Voir aussi
[Utilisation d’Azure Active Directory avec ODBC Driver](https://docs.microsoft.com/sql/connect/odbc/using-azure-active-directory)

[Nouveautés d’identités gérées pour les ressources Azure ?](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview)

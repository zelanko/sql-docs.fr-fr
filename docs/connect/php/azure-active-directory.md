---
title: Azure Active Directory | Microsoft Docs
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: david-puglielli
ms.author: v-dapugl
manager: v-hakaka
ms.openlocfilehash: 67f32c2c48188b3bcff50e22ca66bf2f563b1704
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47814827"
---
# <a name="connect-using-azure-active-directory-authentication"></a>Se connecter à l’aide de l’authentification Azure Active Directory
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-whatis) (Azure AD) est une technologie de gestion d’ID utilisateur central qui fonctionne comme une alternative à [l’authentification SQL Server](../../connect/php/how-to-connect-using-sql-server-authentication.md). Azure AD autorise les connexions à Microsoft Azure SQL Database et SQL Data Warehouse avec des identités fédérées dans Azure AD à l’aide d’un nom d’utilisateur et mot de passe, l’authentification intégrée Windows ou un jeton d’accès Azure AD ; les pilotes PHP pour SQL Server offrent une prise en charge partielle de ces fonctionnalités.

Pour utiliser Azure AD, utilisez le **authentification** mot clé. Les valeurs qui **authentification** peut prendre en sont expliquées dans le tableau suivant.

|Mot clé|Valeurs|Description|
|-|-|-|
|**Authentification**|Pas définie (valeur par défaut)|Mode d’authentification déterminé par les autres mots clés. Pour plus d’informations, consultez [Connection Options](../../connect/php/connection-options.md). |
||`SqlPassword`|S’authentifier directement à une instance de SQL Server (qui peut être une instance Azure) à l’aide d’un nom d’utilisateur et le mot de passe. Le nom d’utilisateur et le mot de passe doivent être passés dans la chaîne de connexion en utilisant le **UID** et **PWD** mots clés. |
||`ActiveDirectoryPassword`|S’authentifier avec une identité Azure Active Directory à l’aide d’un nom d’utilisateur et le mot de passe. Le nom d’utilisateur et le mot de passe doivent être passés dans la chaîne de connexion en utilisant le **UID** et **PWD** mots clés. |

Le **authentification** mot clé affecte les paramètres de sécurité de connexion. Si elle est définie dans la chaîne de connexion, puis par défaut le **Encrypt** mot clé est défini sur true, le client demande le chiffrement. En outre, le certificat de serveur sera validé, quel que soit le paramètre de chiffrement, sauf si **TrustServerCertificate** est définie sur true. Elle se distingue de l’ancien et moins sécurisée, méthode de connexion, dans lequel le certificat de serveur n’est pas validé, sauf si le chiffrement est spécifiquement demandé dans la chaîne de connexion.

Avant d’utiliser Azure AD avec les pilotes PHP pour SQL Server sur Windows, assurez-vous que vous avez installé le [Assistant Microsoft Online Services Sign-In](https://www.microsoft.com/download/details.aspx?id=41950) (non requis pour Linux et MacOS).

#### <a name="limitations"></a>Limitations

Sur Windows, le pilote ODBC sous-jacent prend en charge davantage de valeur pour le **authentification** mot clé, **ActiveDirectoryIntegrated**, mais les pilotes PHP ne prennent pas en charge cette valeur sur n’importe quelle plateforme et donc également ne prennent pas en charge l’authentification par jeton Azure AD.

## <a name="example"></a> Exemple

L’exemple suivant montre comment se connecter à l’aide de **SqlPassword** et **ActiveDirectoryPassword**.

```php
    <?php
    // First connect to a local SQL Server instance by setting Authentication to SqlPassword
    $serverName = "myserver.mydomain";

    $connectionInfo = array( "UID"=>$myusername, "PWD"=>$mypassword, "Authentication"=>'SqlPassword' );

    $conn = sqlsrv_connect( $serverName, $connectionInfo );
    if( $conn === false )
    {
        echo "Could not connect with Authentication=SqlPassword.\n";
        print_r( sqlsrv_errors() );
    }
    else
    {
        echo "Connected successfully with Authentication=SqlPassword.\n";
        sqlsrv_close( $conn );
    }

    // Now connect to an Azure SQL database by setting Authentication to ActiveDirectoryPassword
    $azureServer = "myazureserver.database.windows.net";
    $azureDatabase = "myazuredatabase";
    $azureUsername = "myuid";
    $azurePassword = "mypassword";
    $connectionInfo = array( "Database"=>$azureDatabase, "UID"=>$azureUsername, "PWD"=>$azurePassword,
                             "Authentication"=>'ActiveDirectoryPassword' );

    $conn = sqlsrv_connect( $azureServer, $connectionInfo );
    if( $conn === false )
    {
        echo "Could not connect with Authentication=ActiveDirectoryPassword.\n";
        print_r( sqlsrv_errors() );
    }
    else
    {
        echo "Connected successfully with Authentication=ActiveDirectoryPassword.\n";
        sqlsrv_close( $conn );
    }

    ?>
```

L’exemple suivant fait la même chose que ci-dessus avec le pilote PDO_SQLSRV.

```php
    <?php
    // First connect to a local SQL Server instance by setting Authentication to SqlPassword
    $serverName = "myserver.mydomain";

    $connectionInfo = "Database = $databaseName; Authentication = SqlPassword;";

    try
    {
        $conn = new PDO( "sqlsrv:server = $serverName ; $connectionInfo", $myusername, $mypassword );
        echo "Connected successfully with Authentication=SqlPassword.\n";
        $conn = null;
    }
    catch( PDOException $e )
    {
        echo "Could not connect with Authentication=SqlPassword.\n";
        print_r( $e->getMessage() );
        echo "\n";
    }

    // Now connect to an Azure SQL database by setting Authentication to ActiveDirectoryPassword
    $azureServer = "myazureserver.database.windows.net";
    $azureDatabase = "myazuredatabase";
    $azureUsername = "myuid";
    $azurePassword = "mypassword";
    $connectionInfo = "Database = $azureDatabase; Authentication = ActiveDirectoryPassword;";

    try
    {
        $conn = new PDO( "sqlsrv:server = $azureServer ; $connectionInfo", $azureUsername, $azurePassword );
        echo "Connected successfully with Authentication=ActiveDirectoryPassword.\n";
        $conn = null;
    }
    catch( PDOException $e )
    {
        echo "Could not connect with Authentication=ActiveDirectoryPassword.\n";
        print_r( $e->getMessage() );
        echo "\n";
    }

    ?>
```
## <a name="see-also"></a> Voir aussi  
[Utilisation d’Azure Active Directory avec ODBC Driver](https://docs.microsoft.com/sql/connect/odbc/using-azure-active-directory)

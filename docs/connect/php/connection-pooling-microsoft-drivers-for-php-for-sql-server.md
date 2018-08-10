---
title: Regroupement de connexions (Microsoft Drivers for PHP for SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 08/01/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connection pooling support
ms.assetid: 4d9a83d4-08de-43a1-975c-0a94005edc94
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 02db1d891f02dce9912d4cdcf78ca0166eab9c32
ms.sourcegitcommit: ef7f2540ba731cc6a648005f2773d759df5c6405
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39415478"
---
# <a name="connection-pooling-microsoft-drivers-for-php-for-sql-server"></a>Regroupement de connexions (Microsoft Drivers for PHP for SQL Server)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Voici des points importants à noter sur le regroupement de connexions dans [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]:  
  
-   [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] utilise le regroupement de connexions ODBC.  
  
-   Par défaut, le regroupement de connexions est activé dans Windows. Dans Linux et macOS, les connexions sont regroupées uniquement si le regroupement de connexions est activé pour ODBC (voir [le regroupement de connexions de l’activation/désactivation de la](#enablingdisabling-connection-pooling)). Lorsque le regroupement de connexions est activé et que vous vous connectez à un serveur, le pilote tente d’utiliser une connexion regroupée avant d’en créer un nouveau. Si une connexion équivalente est introuvable dans le regroupement, une nouvelle connexion est créée et ajoutée à ce regroupement. Le pilote détermine si les connexions sont équivalentes, par comparaison avec des chaînes de connexion.  
  
-   Quand une connexion du regroupement est utilisée, l’état de la connexion est réinitialisé.  
  
-   La fermeture de la connexion retourne la connexion au regroupement.  
  
Pour plus d’informations sur le regroupement de connexions, consultez [Regroupement de connexions du Gestionnaire de pilotes](../../odbc/reference/develop-app/driver-manager-connection-pooling.md).  
  
## <a name="enablingdisabling-connection-pooling"></a>Le regroupement de connexions de l’activation/désactivation de la
### <a name="windows"></a>Windows
Vous pouvez forcer le pilote à créer une connexion (au lieu de rechercher une connexion équivalente dans le pool de connexions) en affectant à l’attribut *ConnectionPooling* de la chaîne de connexion la valeur **false** (ou 0).  
  
Si l’attribut *ConnectionPooling* est omis de la chaîne de connexion ou si sa valeur est **true** (ou 1), le pilote crée uniquement une connexion si aucune connexion équivalente n’existe dans le pool de connexions.  
  
Pour plus d’informations sur les autres attributs de connexion, consultez [Connection Options](../../connect/php/connection-options.md).  
### <a name="linux-and-macos"></a>Linux et macOS
Le *ConnectionPooling* attribut ne peut pas être utilisé pour activer/désactiver le regroupement de connexions. 

Le regroupement de connexions peut être activé ou désactivé en modifiant le fichier de configuration du fichier odbcinst.ini. Le pilote doit être rechargé pour que les modifications entrent en vigueur.

Paramètre `Pooling` à `Yes` et un nombre positif `CPTimeout` valeur dans le fichier odbcinst.ini permet le regroupement de connexions. 
```
[ODBC]
Pooling=Yes

[ODBC Driver 13 for SQL Server]
CPTimeout=<int value>
```
  
Au minimum, le fichier odbcinst.ini doit ressembler à cet exemple :

```
[ODBC]
Pooling=Yes

[ODBC Driver 13 for SQL Server]
Description=Microsoft ODBC Driver 13 for SQL Server
Driver=/opt/microsoft/msodbcsql/lib64/libmsodbcsql-13.1.so.3.0
UsageCount=1
CPTimeout=120
```

Paramètre `Pooling` à `No` dans le fichier odbcinst.ini fichier force le pilote pour créer une nouvelle connexion.
```
[ODBC]
Pooling=No
```

## <a name="remarks"></a>Notes 
- Dans Linux ou macOS, toutes les connexions sont regroupées si le regroupement est activé dans le fichier odbcinst.ini. Cela signifie que l’option de connexion ConnectionPooling n’a aucun effet. Pour désactiver le regroupement, définissez le regroupement = No dans le fichier odbcinst.ini et recharger les pilotes.
  - unixODBC < = 2.3.4 (Linux et macOS) peuvent ne pas retourner des informations de diagnostic appropriées, tels que les messages d’erreur, les avertissements et messages d’information
  - pour cette raison, les pilotes SQLSRV et PDO_SQLSRV n’est peut-être pas en mesure d’extraire correctement les données de type long (par exemple, xml, binaire) en tant que chaînes. Données de type long peuvent être extraites en tant que flux de données comme une solution de contournement. Consultez l’exemple ci-dessous pour SQLSRV.

```
<?php
$connectionInfo = array("Database"=>"test", "UID"=>"username", "PWD"=>"password");

$conn1 = sqlsrv_connect("servername", $connectionInfo);

$longSample = str_repeat("a", 8500);
$xml1 = 
'<ParentXMLTag>
  <ChildTag01>'.$longSample.'</ChildTag01>
</ParentXMLTag>';

// Create table and insert xml string into it
sqlsrv_query($conn1, "CREATE TABLE xml_table (field xml)");
sqlsrv_query($conn1, "INSERT into xml_table values ('$xml1')");

// retrieve the inserted xml
$column1 = getColumn($conn1);

// return the connection to the pool
sqlsrv_close($conn1);

// This connection is from the pool
$conn2 = sqlsrv_connect("servername", $connectionInfo);
$column2 = getColumn($conn2);

sqlsrv_query($conn2, "DROP TABLE xml_table");
sqlsrv_close($conn2);

function getColumn($conn)
{
    $tsql = "SELECT * from xml_table";
    $stmt = sqlsrv_query($conn, $tsql);
    sqlsrv_fetch($stmt);
    // This might fail in Linux and macOS
    // $column = sqlsrv_get_field($stmt, 0, SQLSRV_PHPTYPE_STRING(SQLSRV_ENC_CHAR));
    // The workaround is to fetch it as a stream
    $column = sqlsrv_get_field($stmt, 0, SQLSRV_PHPTYPE_STREAM(SQLSRV_ENC_CHAR));
    sqlsrv_free_stmt($stmt);
    return ($column);
}
?>
```


## <a name="see-also"></a> Voir aussi  
[Guide pratique pour se connecter à l’aide de l’authentification Windows](../../connect/php/how-to-connect-using-windows-authentication.md)

[Guide pratique pour se connecter à l’aide de l’authentification SQL Server](../../connect/php/how-to-connect-using-sql-server-authentication.md)  
  

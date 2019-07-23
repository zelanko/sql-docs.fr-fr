---
title: Résilience des connexions inactives
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: david-puglielli
ms.author: v-dapugl
manager: v-mabarw
ms.openlocfilehash: 3edba0cde94d8661eed053319142ce7f84a70613
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265166"
---
# <a name="idle-connection-resiliency"></a>Résilience des connexions inactives
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

La résilience des [connexions](../odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md) est le principe selon lequel une connexion inactive interrompue peut être rétablie, dans certaines limites. Si une connexion à Microsoft SQL Server échoue, la résilience des connexions permet au client de tenter automatiquement de rétablir la connexion. La résilience de connexion est une propriété de la source de données; Seuls les SQL Server 2014 et versions ultérieures et Azure SQL Database prennent en charge la résilience des connexions.

La résilience des connexions est implémentée avec deux mots clés de connexion qui peuvent être ajoutés aux chaînes de connexion: **ConnectRetryCount** et **ConnectRetryInterval**.

|Mot clé|Valeurs|Valeur par défaut|Description|
|-|-|-|-|
|**ConnectRetryCount**| Entier compris entre 0 et 255 (inclus)|1|Nombre maximal de tentatives de rétablissement d’une connexion interrompue avant abandon. Par défaut, une seule tentative est effectuée pour rétablir une connexion en cas de rupture. La valeur 0 signifie qu’aucune reconnexion n’est tentée.|
|**ConnectRetryInterval**| Entier compris entre 1 et 60 (inclus)|1| Durée, en secondes, entre les tentatives de rétablissement d’une connexion. L’application tentera de se reconnecter immédiatement lors de la détection d’une connexion interrompue, puis patienterez **ConnectRetryInterval** secondes avant de réessayer. Ce mot clé est ignoré si **ConnectRetryCount** est égal à 0.

Si le produit de **ConnectRetryCount** multiplié par **ConnectRetryInterval** est supérieur à **LoginTimeout**, le client cesse d’essayer de se connecter une fois que **LoginTimeout** est atteint. dans le cas contraire, il continuera à tenter de se reconnecter jusqu’à ce que **ConnectRetryCount** soit atteint.

#### <a name="remarks"></a>Notes

La résilience de la connexion s’applique lorsque la connexion est inactive. Les défaillances qui se produisent lors de l’exécution d’une transaction, par exemple, ne déclenchent pas de tentatives de reconnexion. elles échoueront normalement. Les situations suivantes, appelées États de session non récupérables, ne déclenchent pas de tentatives de reconnexion:

* tables temporaires ;
* Curseurs globaux et locaux
* Verrous de transaction au niveau du contexte de transaction et de la session
* Verrous d’applications
* EXÉCUTER en tant que/rétablir le contexte de sécurité
* Handles OLE Automation
* Handles XML préparés
* Indicateurs de trace

## <a name="example"></a>Exemple

Le code suivant se connecte à une base de données et exécute une requête. La connexion est interrompue en arrêtant la session et une nouvelle requête est tentée à l’aide de la connexion rompue. Cet exemple utilise l’exemple de base de données [AdventureWorks](https://msdn.microsoft.com/library/ms124501%28v=sql.100%29.aspx).

Dans cet exemple, nous spécifions un curseur mis en mémoire tampon avant de rompre la connexion. Si nous ne spécifions pas de curseur mis en mémoire tampon, la connexion n’est pas rétablie, car il y a un curseur côté serveur actif et la connexion n’est donc pas inactive en cas de rupture. Toutefois, dans ce cas, nous pourrions appeler sqlsrv_free_stmt () avant de rompre la connexion pour libéré le curseur, et la connexion sera correctement rétablie.

```php
<?php
// This function breaks the connection by determining its session ID and killing it.
// A separate connection is used to break the main connection because a session
// cannot kill itself. The sleep() function ensures enough time has passed for KILL
// to finish ending the session.
function BreakConnection( $conn, $conn_break )
{
    $stmt1 = sqlsrv_query( $conn, "SELECT @@SPID" );
    if ( sqlsrv_fetch( $stmt1 ) )
    {
        $spid=sqlsrv_get_field( $stmt1, 0 );
    }

    $stmt2 = sqlsrv_prepare( $conn_break, "KILL ".$spid );
    sqlsrv_execute( $stmt2 );
    sleep(1);
}

// Connect to the local server using Windows authentication and specify
// AdventureWorks as the database in use. Specify values for
// ConnectRetryCount and ConnectRetryInterval as well.
$databaseName = 'AdventureWorks2014';
$serverName = '(local)';
$connectionInfo = array( "Database"=>$databaseName, "ConnectRetryCount"=>10, "ConnectRetryInterval"=>10 );

$conn = sqlsrv_connect( $serverName, $connectionInfo );
if( $conn === false)  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}

// A separate connection that will be used to break the main connection $conn
$conn_break = sqlsrv_connect( $serverName, array( "Database"=>$databaseName) );

// Create a statement to retrieve the contents of a table
$stmt1 = sqlsrv_query( $conn, "SELECT * FROM HumanResources.Employee",
                       array(), array( "Scrollable"=>"buffered" ) );
if( $stmt1 === false )
{
     echo "Error in statement 1.\n";
     die( print_r( sqlsrv_errors(), true ));
}
else
{
    echo "Statement 1 successful.\n";
    $rowcount = sqlsrv_num_rows( $stmt1 );
    echo $rowcount." rows in result set.\n";
}

// Now break the connection $conn
BreakConnection( $conn, $conn_break );

// Create another statement. The connection will be reestablished.
$stmt2 = sqlsrv_query( $conn, "SELECT * FROM HumanResources.Department",
                       array(), array( "Scrollable"=>"buffered" ) );
if( $stmt2 === false )
{
     echo "Error in statement 2.\n";
     die( print_r( sqlsrv_errors(), true ));
}
else
{
    echo "Statement 2 successful.\n";
    $rowcount = sqlsrv_num_rows( $stmt2 );
    echo $rowcount." rows in result set.\n";
}

sqlsrv_close( $conn );
sqlsrv_close( $conn_break );
?>
```
Sortie attendue:
```
Statement 1 successful.
290 rows in result set.
Statement 2 successful.
16 rows in result set.
```

## <a name="see-also"></a>Voir aussi
[Résilience de connexion du pilote ODBC Windows](../odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md)

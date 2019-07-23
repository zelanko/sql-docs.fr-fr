---
title: Types de curseurs (pilote SQLSRV) | Microsoft Docs
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8472d839-8124-4a62-a83c-7e771b0d4962
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ac090ad8831397bf31c0911ab8a8db21486528db
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015116"
---
# <a name="cursor-types-sqlsrv-driver"></a>Types de curseurs (pilote SQLSRV)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Le pilote SQLSRV vous permet de créer un jeu de résultats avec des lignes auxquelles vous pouvez accéder dans n’importe quel ordre, selon le type de curseur.  Cette rubrique aborde les curseurs côté client (mis en mémoire tampon) et côté serveur (non mis en mémoire tampon).  
  
## <a name="cursor-types"></a>Types de curseurs  
Lorsque vous créez un jeu de résultats avec [sqlsrv_query](../../connect/php/sqlsrv-query.md) ou à l’aide de [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md), vous pouvez spécifier le type de curseur. Par défaut, un curseur avant uniquement est utilisé, ce qui vous permet de déplacer une ligne à la fois à partir de la première ligne du jeu de résultats jusqu’à ce que vous atteigniez la fin du jeu de résultats.  
  
Vous pouvez créer un jeu de résultats avec un curseur de défilement, ce qui vous permet d’accéder à n’importe quelle ligne du jeu de résultats, dans n’importe quel ordre. Le tableau suivant répertorie les valeurs qui peuvent être passées à l’option de **défilement** dans sqlsrv_query ou sqlsrv_prepare.  
  
|Option|Description|  
|----------|---------------|  
|SQLSRV_CURSOR_FORWARD|Vous permet de déplacer une ligne à la fois à partir de la première ligne du jeu de résultats jusqu’à ce que vous atteigniez la fin du jeu de résultats.<br /><br />Il s’agit du type de curseur par défaut.<br /><br />[sqlsrv_num_rows](../../connect/php/sqlsrv-num-rows.md) retourne une erreur pour les jeux de résultats créés avec ce type de curseur.<br /><br />**Forward** est la forme abrégée de SQLSRV_CURSOR_FORWARD.|  
|SQLSRV_CURSOR_STATIC|Vous permet d’accéder aux lignes dans n’importe quel ordre, mais ne reflète pas les modifications apportées à la base de données.<br /><br />**static** est la forme abrégée de SQLSRV_CURSOR_STATIC.|  
|SQLSRV_CURSOR_DYNAMIC|Vous permet d’accéder aux lignes dans n’importe quel ordre et reflète les modifications apportées à la base de données.<br /><br />[sqlsrv_num_rows](../../connect/php/sqlsrv-num-rows.md) retourne une erreur pour les jeux de résultats créés avec ce type de curseur.<br /><br />**Dynamic** est la forme abrégée de SQLSRV_CURSOR_DYNAMIC.|  
|SQLSRV_CURSOR_KEYSET|Vous permet d’accéder aux lignes dans n’importe quel ordre. Toutefois, un curseur de jeu de clés ne met pas à jour le nombre de lignes si une ligne est supprimée de la table (une ligne supprimée est retournée sans valeur).<br /><br />**keyset** est la forme abrégée de SQLSRV_CURSOR_KEYSET.|  
|SQLSRV_CURSOR_CLIENT_BUFFERED|Vous permet d’accéder aux lignes dans n’importe quel ordre. Crée une requête de curseur côté client.<br /><br />la **mise en mémoire tampon** est la forme abrégée de SQLSRV_CURSOR_CLIENT_BUFFERED.|  
  
Si une requête génère plusieurs jeux de résultats, l’option de **défilement** s’applique à tous les jeux de résultats.  
  
## <a name="selecting-rows-in-a-result-set"></a>Sélection de lignes dans un jeu de résultats  
Après avoir créé un jeu de résultats, vous pouvez utiliser [sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md), [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md)ou [sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md) pour spécifier une ligne.  
  
Le tableau suivant décrit les valeurs que vous pouvez spécifier dans le paramètre *Row* .  
  
|Paramètre|Description|  
|-------------|---------------|  
|SQLSRV_SCROLL_NEXT|Spécifie la ligne suivante. Il s’agit de la valeur par défaut, si vous ne spécifiez pas le paramètre de *ligne* d’un jeu de résultats avec défilement.|  
|SQLSRV_SCROLL_PRIOR|Spécifie la ligne avant la ligne actuelle.|  
|SQLSRV_SCROLL_FIRST|Spécifie la première ligne du jeu de résultats.|  
|SQLSRV_SCROLL_LAST|Spécifie la dernière ligne du jeu de résultats.|  
|SQLSRV_SCROLL_ABSOLUTE|Spécifie la ligne spécifiée avec le paramètre *offset* .|  
|SQLSRV_SCROLL_RELATIVE|Spécifie la ligne spécifiée avec le paramètre *offset* de la ligne actuelle.|  
  
## <a name="server-side-cursors-and-the-sqlsrv-driver"></a>Curseurs côté serveur et pilote SQLSRV  
L’exemple suivant montre l’effet des différents curseurs. Sur la ligne 33 de l’exemple, vous voyez la première des trois instructions de requête qui spécifient des curseurs différents.  Deux des instructions de requête sont commentées. Chaque fois que vous exécutez le programme, utilisez un autre type de curseur pour voir l’effet de la mise à jour de la base de données sur la ligne 47.  
  
```  
<?php  
$server = "server_name";  
$conn = sqlsrv_connect( $server, array( 'Database' => 'test' ));  
if ( $conn === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$stmt = sqlsrv_query( $conn, "DROP TABLE dbo.ScrollTest" );  
if ( $stmt !== false ) {   
   sqlsrv_free_stmt( $stmt );   
}  
  
$stmt = sqlsrv_query( $conn, "CREATE TABLE ScrollTest (id int, value char(10))" );  
if ( $stmt === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$stmt = sqlsrv_query( $conn, "INSERT INTO ScrollTest (id, value) VALUES(?,?)", array( 1, "Row 1" ));  
if ( $stmt === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$stmt = sqlsrv_query( $conn, "INSERT INTO ScrollTest (id, value) VALUES(?,?)", array( 2, "Row 2" ));  
if ( $stmt === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$stmt = sqlsrv_query( $conn, "INSERT INTO ScrollTest (id, value) VALUES(?,?)", array( 3, "Row 3" ));  
if ( $stmt === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$stmt = sqlsrv_query( $conn, "SELECT * FROM ScrollTest", array(), array( "Scrollable" => 'keyset' ));  
// $stmt = sqlsrv_query( $conn, "SELECT * FROM ScrollTest", array(), array( "Scrollable" => 'dynamic' ));  
// $stmt = sqlsrv_query( $conn, "SELECT * FROM ScrollTest", array(), array( "Scrollable" => 'static' ));  
  
$rows = sqlsrv_has_rows( $stmt );  
if ( $rows != true ) {  
   die( "Should have rows" );  
}  
  
$result = sqlsrv_fetch( $stmt, SQLSRV_SCROLL_LAST );  
$field1 = sqlsrv_get_field( $stmt, 0 );  
$field2 = sqlsrv_get_field( $stmt, 1 );  
echo "\n$field1 $field2\n";  
  
$stmt2 = sqlsrv_query( $conn, "delete from ScrollTest where id = 3" );  
// or  
// $stmt2 = sqlsrv_query( $conn, "UPDATE ScrollTest SET id = 4 WHERE id = 3" );  
if ( $stmt2 !== false ) {   
   sqlsrv_free_stmt( $stmt2 );   
}  
  
$result = sqlsrv_fetch( $stmt, SQLSRV_SCROLL_LAST );  
$field1 = sqlsrv_get_field( $stmt, 0 );  
$field2 = sqlsrv_get_field( $stmt, 1 );  
echo "\n$field1 $field2\n";  
  
sqlsrv_free_stmt( $stmt );  
sqlsrv_close( $conn );  
?>  
```  
  
## <a name="client-side-cursors-and-the-sqlsrv-driver"></a>Curseurs côté client et pilote SQLSRV  
Les curseurs côté client sont une fonctionnalité ajoutée à la [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] version 3,0 de qui vous permet de mettre en cache un jeu de résultats entier en mémoire. Le nombre de lignes est disponible après l’exécution de la requête lors de l’utilisation d’un curseur côté client.  
  
Les curseurs côté client doivent être utilisés pour les jeux de résultats petits à moyens. Utilisez des curseurs côté serveur pour les grands jeux de résultats.  
  
Une requête retourne la valeur false si la mémoire tampon n’est pas assez grande pour contenir l’intégralité du jeu de résultats. Vous pouvez augmenter la taille de la mémoire tampon jusqu’à la limite de mémoire PHP.  
  
À l’aide du pilote SQLSRV, vous pouvez configurer la taille de la mémoire tampon qui contient le jeu de résultats avec le paramètre ClientBufferMaxKBSize pour [sqlsrv_configure](../../connect/php/sqlsrv-configure.md). [sqlsrv_get_config](../../connect/php/sqlsrv-get-config.md) retourne la valeur de ClientBufferMaxKBSize. Vous pouvez également définir la taille maximale de la mémoire tampon dans le fichier php. ini avec SQLSRV. ClientBufferMaxKBSize (par exemple, SQLSRV. ClientBufferMaxKBSize = 1024).  
  
L’exemple suivant illustre:  
  
-   Le nombre de lignes est toujours disponible avec un curseur côté client.  
  
-   Utilisation des curseurs côté client et des instructions batch.  
  
```  
<?php  
$serverName = "(local)";  
$connectionInfo = array("Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
  
if ( $conn === false ) {  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$tsql = "select * from HumanResources.Department";  
  
// Execute the query with client-side cursor.  
$stmt = sqlsrv_query($conn, $tsql, array(), array("Scrollable"=>"buffered"));  
if (! $stmt) {  
   echo "Error in statement execution.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
// row count is always available with a client-side cursor  
$row_count = sqlsrv_num_rows( $stmt );  
echo "\nRow count = $row_count\n";  
  
// Move to a specific row in the result set.  
$row = sqlsrv_fetch($stmt, SQLSRV_SCROLL_FIRST);  
$EmployeeID = sqlsrv_get_field( $stmt, 0);  
echo "Employee ID = $EmployeeID \n";  
  
// Client-side cursor and batch statements  
$tsql = "select top 2 * from HumanResources.Employee;Select top 3 * from HumanResources.EmployeeAddress";  
  
$stmt = sqlsrv_query($conn, $tsql, array(), array("Scrollable"=>"buffered"));  
if (! $stmt) {  
   echo "Error in statement execution.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$row_count = sqlsrv_num_rows( $stmt );  
echo "\nRow count for first result set = $row_count\n";  
  
$row = sqlsrv_fetch($stmt, SQLSRV_SCROLL_FIRST);  
$EmployeeID = sqlsrv_get_field( $stmt, 0);  
echo "Employee ID = $EmployeeID \n";  
  
sqlsrv_next_result($stmt);  
  
$row_count = sqlsrv_num_rows( $stmt );  
echo "\nRow count for second result set = $row_count\n";  
  
$row = sqlsrv_fetch($stmt, SQLSRV_SCROLL_LAST);  
$EmployeeID = sqlsrv_get_field( $stmt, 0);  
echo "Employee ID = $EmployeeID \n";  
?>  
```  
  
L’exemple suivant illustre un curseur côté client utilisant [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md) et une autre taille de mémoire tampon du client.
  
```  
<?php  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
  
if ( $conn === false ) {  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$tsql = "select * from HumanResources.Employee";  
$stmt = sqlsrv_prepare( $conn, $tsql, array(), array("Scrollable" => SQLSRV_CURSOR_CLIENT_BUFFERED, "ClientBufferMaxKBSize" => 51200));
  
if (! $stmt ) {  
   echo "Statement could not be prepared.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_execute( $stmt);  
  
$row_count = sqlsrv_num_rows( $stmt );  
if ($row_count)  
   echo "\nRow count = $row_count\n";  
  
$row = sqlsrv_fetch($stmt, SQLSRV_SCROLL_FIRST);  
if ($row ) {  
   $EmployeeID = sqlsrv_get_field( $stmt, 0);  
   echo "Employee ID = $EmployeeID \n";  
}  
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[Spécification d’un type de curseur et sélection de lignes](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md)  
  

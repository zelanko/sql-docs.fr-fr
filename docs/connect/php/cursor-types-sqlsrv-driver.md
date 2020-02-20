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
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "68015116"
---
# <a name="cursor-types-sqlsrv-driver"></a>Types de curseurs (pilote SQLSRV)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Le pilote SQLSRV vous permet de créer un jeu de résultats avec des lignes auxquelles vous pouvez accéder dans n’importe quel ordre, selon le type de curseur.  Cette rubrique aborde les curseurs côté client (mis en mémoire tampon) et côté serveur (non mis en mémoire tampon).  
  
## <a name="cursor-types"></a>Types de curseurs  
Lorsque vous créez un jeu de résultats avec [sqlsrv_query](../../connect/php/sqlsrv-query.md) ou [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md), vous pouvez spécifier le type de curseur. Le curseur utilisé par défaut est un curseur avant uniquement, qui permet de se déplacer ligne par ligne à partir de la première ligne du jeu de résultats jusqu’à atteindre la fin du jeu de résultats.  
  
Vous pouvez créer un jeu de résultats avec un curseur de défilement, qui permet d’accéder à n’importe quelle ligne du jeu de résultats, dans n’importe quel ordre. Le tableau suivant présente les valeurs qui peuvent être transmises à l’option **Scrollable** de sqlsrv_query ou de sqlsrv_prepare.  
  
|Option|Description|  
|----------|---------------|  
|SQLSRV_CURSOR_FORWARD|Permet de se déplacer ligne par ligne à partir de la première ligne du jeu de résultats jusqu’à atteindre la fin du jeu de résultats.<br /><br />Il s’agit du type de curseur par défaut.<br /><br />[sqlsrv_num_rows](../../connect/php/sqlsrv-num-rows.md) retourne une erreur pour les jeux de résultats créés avec ce type de curseur.<br /><br />**forward** est la forme abrégée de SQLSRV_CURSOR_FORWARD.|  
|SQLSRV_CURSOR_STATIC|Permet d’accéder aux lignes dans n’importe quel ordre mais ne reflète pas les modifications dans la base de données.<br /><br />**static** est la forme abrégée de SQLSRV_CURSOR_STATIC.|  
|SQLSRV_CURSOR_DYNAMIC|Permet d’accéder aux lignes dans n’importe quel ordre et reflète les modifications dans la base de données.<br /><br />[sqlsrv_num_rows](../../connect/php/sqlsrv-num-rows.md) retourne une erreur pour les jeux de résultats créés avec ce type de curseur.<br /><br />**dynamic** est la forme abrégée de SQLSRV_CURSOR_DYNAMIC.|  
|SQLSRV_CURSOR_KEYSET|Permet d’accéder aux lignes dans n’importe quel ordre. Toutefois, un curseur de jeu de clés ne met pas à jour le nombre de lignes si une ligne est supprimée de la table (une ligne supprimée est retournée sans valeur).<br /><br />**keyset** est la forme abrégée de SQLSRV_CURSOR_KEYSET.|  
|SQLSRV_CURSOR_CLIENT_BUFFERED|Permet d’accéder aux lignes dans n’importe quel ordre. Crée une requête de curseur côté client.<br /><br />**buffered** est la forme abrégée de SQLSRV_CURSOR_CLIENT_BUFFERED.|  
  
Si une requête génère plusieurs jeux de résultats, l’option **Scrollable** s’applique à tous les jeux de résultats.  
  
## <a name="selecting-rows-in-a-result-set"></a>Sélectionner des lignes dans un jeu de résultats  
Après avoir créé un jeu de résultats, vous pouvez utiliser [sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md), [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md)ou [sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md) pour spécifier une ligne.  
  
Le tableau suivant décrit les valeurs possibles du paramètre *row*.  
  
|Paramètre|Description|  
|-------------|---------------|  
|SQLSRV_SCROLL_NEXT|Spécifie la ligne suivante. Il s’agit de la valeur par défaut, si vous ne spécifiez pas le paramètre *row* pour un jeu de résultats de défilement.|  
|SQLSRV_SCROLL_PRIOR|Spécifie la ligne précédant la ligne actuelle.|  
|SQLSRV_SCROLL_FIRST|Spécifie la première ligne du jeu de résultats.|  
|SQLSRV_SCROLL_LAST|Spécifie la dernière ligne du jeu de résultats.|  
|SQLSRV_SCROLL_ABSOLUTE|Spécifie la ligne spécifiée avec le paramètre *offset*.|  
|SQLSRV_SCROLL_RELATIVE|Spécifie la ligne spécifiée avec le paramètre *offset* à partir de la ligne actuelle.|  
  
## <a name="server-side-cursors-and-the-sqlsrv-driver"></a>Curseurs côté serveur et pilote SQLSRV  
L’exemple suivant montre l’effet des différents curseurs. La ligne 33 de l’exemple montre la première des trois instructions de requête qui spécifient des curseurs différents.  Deux des instructions de requête sont commentées. Chaque fois que vous exécutez le programme, utilisez un autre type de curseur pour voir l’effet de la mise à jour de la base de données sur la ligne 47.  
  
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
La fonctionnalité de curseurs côté client, ajoutée dans la version 3.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], permettent de mettre en cache tout un jeu de résultats en mémoire. Le nombre de lignes est disponible après l’exécution de la requête si le curseur utilisé est un curseur côté client.  
  
Les curseurs côté client doivent être utilisés pour les jeux de résultats petits à moyens. Utilisez des curseurs côté serveur pour les gros jeux de résultats.  
  
La requête retourne false si la mémoire tampon n’est pas assez grande pour contenir la totalité du jeu de résultats. Vous pouvez augmenter la taille de la mémoire tampon jusqu’à la limite de mémoire PHP.  
  
À l’aide du pilote SQLSRV, vous pouvez configurer la taille de la mémoire tampon contenant le jeu de résultats avec le paramètre ClientBufferMaxKBSize pour [sqlsrv_configure](../../connect/php/sqlsrv-configure.md). [sqlsrv_get_config](../../connect/php/sqlsrv-get-config.md) retourne la valeur de ClientBufferMaxKBSize. Vous pouvez également définir la taille maximale de la mémoire tampon dans le fichier php.ini avec sqlsrv.ClientBufferMaxKBSize (par exemple, ClientBufferMaxKBSize = 1024).  
  
L’exemple suivant montre :  
  
-   Le nombre de lignes toujours disponible avec un curseur côté client.  
  
-   L’utilisation de curseurs côté client et d’instructions batch.  
  
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
  
L’exemple suivant montre un curseur côté client utilisant [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md) et une autre taille de mémoire tampon du client.
  
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
  

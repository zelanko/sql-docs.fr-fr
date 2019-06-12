---
title: 'Comment : envoyer des données sous un Stream | Microsoft Docs'
ms.custom: ''
ms.date: 02/28/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data
- streaming data
ms.assetid: ab6b95d6-b6e6-4bd7-a18c-50f2918f7532
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 73b30ff0ed4f4173f13fff518b6578e3d041f3b1
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66780731"
---
# <a name="how-to-send-data-as-a-stream"></a>Procédure : envoyer des données sous forme de flux
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Le [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] tire parti des flux PHP pour envoyer des objets volumineux au serveur. Les exemples de cette rubrique montrent comment envoyer des données sous forme de flux. Le premier exemple utilise le pilote SQLSRV pour illustrer le comportement par défaut, qui consiste à envoyer toutes les données de flux au moment de l’exécution de la requête. Le deuxième exemple utilise le pilote SQLSRV pour illustrer comment envoyer au serveur jusqu’à huit kilo-octets (8 Ko) de données de flux en une seule fois.  
  
Le troisième exemple montre comment envoyer des données de flux au serveur à l’aide du pilote PDO_SQLSRV.  
  
## <a name="example-sending-stream-data-at-execution"></a>Exemple : Envoi de données de Stream lors de l’exécution
L’exemple suivant insère une ligne dans la table *Production.ProductReview* de la base de données AdventureWorks. Les commentaires du client ( *$comments*) sont ouverts en tant que flux avec la fonction PHP [fopen](https://php.net/manual/en/function.fopen.php), puis transmis au serveur à l’exécution de la requête.  
  
L’exemple part du principe que SQL Server et la base de données [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) sont installés sur l’ordinateur local. Toute la sortie est écrite dans la console.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if ($conn === false) {
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up the Transact-SQL query. */  
$tsql = "INSERT INTO Production.ProductReview (ProductID,   
                                               ReviewerName,  
                                               ReviewDate,  
                                               EmailAddress,  
                                               Rating,  
                                               Comments)  
         VALUES (?, ?, ?, ?, ?, ?)";  
  
/* Set the parameter values and put them in an array.  
Note that $comments is opened as a stream. */  
$productID = '709';  
$name = 'Customer Name';  
$date = date("Y-m-d");  
$email = 'customer@name.com';  
$rating = 3;  
$data = 'Insert any lengthy comment here.';
$comments = fopen('data:text/plain,'.urlencode($data), 'r');
$params = array($productID, $name, $date, $email, $rating, $comments);
  
/* Execute the query. All stream data is sent upon execution.*/  
$stmt = sqlsrv_query($conn, $tsql, $params);  
if ($stmt === false) {
     echo "Error in statement execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
} else {
     echo "The query was successfully executed.";  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example-sending-stream-data-using-sqlsrvsendstreamdata"></a>Exemple : Envoi sqlsrv_send_stream_data Stream à l’aide de données
L’exemple suivant est identique au précédent, sauf que le comportement par défaut qui consiste à envoyer toutes les données de flux lors de l’exécution est désactivé. L’exemple utilise [sqlsrv_send_stream_data](../../connect/php/sqlsrv-send-stream-data.md) pour envoyer des données de flux au serveur. Jusqu’à huit kilo-octets (8 Ko) de données sont envoyés lors de chaque appel à **sqlsrv_send_stream_data**. Le script compte le nombre d’appels effectués par **sqlsrv_send_stream_data** et affiche le résultat dans la console.  
  
L’exemple part du principe que SQL Server et la base de données [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) sont installés sur l’ordinateur local. Toute la sortie est écrite dans la console.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if ($conn === false) {
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up the Transact-SQL query. */  
$tsql = "INSERT INTO Production.ProductReview (ProductID,   
                                               ReviewerName,  
                                               ReviewDate,  
                                               EmailAddress,  
                                               Rating,  
                                               Comments)  
         VALUES (?, ?, ?, ?, ?, ?)";  
  
/* Set the parameter values and put them in an array.  
Note that $comments is opened as a stream. */  
$productID = '709';  
$name = 'Customer Name';  
$date = date("Y-m-d");  
$email = 'customer@name.com';  
$rating = 3;  
$data = 'Insert any lengthy comment here.';
$comments = fopen('data:text/plain,'.urlencode($data), 'r');
$params = array($productID, $name, $date, $email, $rating, $comments);  
  
/* Turn off the default behavior of sending all stream data at  
execution. */  
$options = array("SendStreamParamsAtExec" => 0);  
  
/* Execute the query. */  
$stmt = sqlsrv_query($conn, $tsql, $params, $options);  
if ($stmt === false) {
     echo "Error in statement execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Send up to 8K of parameter data to the server with each call to  
sqlsrv_send_stream_data. Count the calls. */  
$i = 1;  
while (sqlsrv_send_stream_data($stmt)) {
     echo "$i call(s) made.\n";  
     $i++;  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
Même si les exemples de cette rubrique envoient des données de type caractère au serveur, vous pouvez envoyer des données dans n’importe quel format sous forme de flux. Vous pouvez par exemple utiliser les techniques présentées dans cette rubrique pour envoyer des images au format binaire sous forme de flux.  
  
## <a name="example-sending-an-image-as-a-stream"></a>Exemple : Envoi d’une Image comme un Stream 
  
```  
<?php  
   $server = "(local)";   
   $database = "Test";  
   $conn = new PDO( "sqlsrv:server=$server;Database = $database", "", "");  
  
   $binary_source = fopen( "data://text/plain,", "r");  
  
   $stmt = $conn->prepare("insert into binaries (imagedata) values (?)");  
   $stmt->bindParam(1, $binary_source, PDO::PARAM_LOB);   
  
   $conn->beginTransaction();  
   $stmt->execute();  
   $conn->commit();  
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[Mise à jour des données &#40;pilotes Microsoft SQL Server pour PHP&#41;](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)

[Récupération des données sous la forme d’un flux à l’aide du pilote SQLSRV](../../connect/php/retrieving-data-as-a-stream-using-the-sqlsrv-driver.md)

[À propos des exemples de code dans la documentation](../../connect/php/about-code-examples-in-the-documentation.md)  
  

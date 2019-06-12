---
title: Guide pratique pour envoyer et récupérer des données UTF-8 avec la prise en charge UTF-8 intégrée | Microsoft Docs
ms.custom: ''
ms.date: 03/23/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- retrieving data, UTF-8 encoded data
- converting data types
- updating data
ms.assetid: 366c57cf-352f-4202-8074-6ddce44880d1
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9c472f5c15be78a35291487e433e0f81a5d7aa60
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797129"
---
# <a name="how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support"></a>Procédure : envoyer et récupérer des données UTF-8 à l’aide de la prise en charge UTF-8 intégrée
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Si vous utilisez le pilote PDO_SQLSRV, vous pouvez spécifier l’encodage avec l’attribut PDO::SQLSRV_ATTR_ENCODING. Pour plus d’informations, consultez [Constantes &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).  
  
Le reste de cette rubrique décrit l’encodage avec le pilote SQLSRV.  
  
Pour envoyer ou récupérer des données encodées en UTF-8 sur le serveur :  
  
1.  Assurez-vous que la colonne source ou de destination est de type **nchar** ou **nvarchar**.  
  
2.  Spécifiez le type PHP `SQLSRV_PHPTYPE_STRING('UTF-8')` dans le tableau de paramètres. Ou bien, spécifiez `"CharacterSet" => "UTF-8"` en tant qu’option de connexion.  
  
    Quand vous spécifiez un jeu de caractères dans le cadre des options de connexion, le pilote part du principe que les autres chaînes de connexion utilisent ce même jeu de caractères. Les chaînes de nom de serveur et de requête sont également supposées utiliser le même jeu de caractères.  
  
Vous pouvez transmettre UTF-8 ou SQLSRV_ENC_CHAR à **CharacterSet**, mais pas transmettre SQLSRV_ENC_BINARY. L’encodage par défaut est SQLSRV_ENC_CHAR.  
  
## <a name="example"></a>Exemple  
L’exemple suivant montre comment envoyer et récupérer des données encodées en UTF-8 en spécifiant le jeu de caractères UTF-8 au moment de l’établissement de la connexion. L’exemple met à jour la colonne Comments de la table Production.ProductReview pour un ID d’évaluation spécifié. L’exemple récupère également les données qui viennent d’être mises à jour et les affiche. Notez que la colonne Comments est de type **nvarchar(3850)** . Notez également que, avant d’être envoyées au serveur, les données sont encodées en UTF-8 avec la fonction **utf8_encode** PHP. Cette opération est effectuée à des fins de démonstration uniquement. Dans un scénario d’application réelle, vous débuteriez avec des données encodées en UTF-8.  
  
L’exemple part du principe que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et la base de données [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) sont installés sur l’ordinateur local. Toute la sortie est écrite dans le navigateur quand l’exemple est exécuté à partir du navigateur.  
  
```  
<?php  
  
// Connect to the local server using Windows Authentication and  
// specify the AdventureWorks database as the database in use.   
//   
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks", "CharacterSet" => "UTF-8");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
  
if ( $conn === false ) {  
   echo "Could not connect.<br>";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
// Set up the Transact-SQL query.  
//   
$tsql1 = "UPDATE Production.ProductReview  
          SET Comments = ?  
          WHERE ProductReviewID = ?";  
  
// Set the parameter values and put them in an array. Note that  
// $comments is converted to UTF-8 encoding with the PHP function  
// utf8_encode to simulate an application that uses UTF-8 encoded data.   
//   
$reviewID = 3;  
$comments = utf8_encode("testing 1, 2, 3, 4.  Testing.");  
$params1 = array(  
                  array( $comments, null ),  
                  array( $reviewID, null )  
                );  
  
// Execute the query.  
//   
$stmt1 = sqlsrv_query($conn, $tsql1, $params1);  
  
if ( $stmt1 === false ) {  
   echo "Error in statement execution.<br>";  
   die( print_r( sqlsrv_errors(), true));  
}  
else {  
   echo "The update was successfully executed.<br>";  
}  
  
// Retrieve the newly updated data.  
//   
$tsql2 = "SELECT Comments   
          FROM Production.ProductReview   
          WHERE ProductReviewID = ?";  
  
// Set up the parameter array.  
//   
$params2 = array($reviewID);  
  
// Execute the query.  
//   
$stmt2 = sqlsrv_query($conn, $tsql2, $params2);  
if ( $stmt2 === false ) {  
   echo "Error in statement execution.<br>";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
// Retrieve and display the data.   
//   
if ( sqlsrv_fetch($stmt2) ) {  
   echo "Comments: ";  
   $data = sqlsrv_get_field( $stmt2, 0 );  
   echo $data."<br>";  
}  
else {  
   echo "Error in fetching data.<br>";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
// Free statement and connection resources.  
//   
sqlsrv_free_stmt( $stmt1 );  
sqlsrv_free_stmt( $stmt2 );  
sqlsrv_close( $conn);  
?>  
```  
  
Pour plus d’informations sur le stockage des données Unicode, voir [Utiliser des données Unicode](https://msdn.microsoft.com/library/ms175180.aspx).  
  
## <a name="example"></a>Exemple  
L’exemple suivant est similaire au premier exemple, mais au lieu de spécifier le jeu de caractères UTF-8 sur la connexion, il montre comment spécifier le jeu de caractères UTF-8 sur la colonne.  
  
```  
<?php  
  
// Connect to the local server using Windows Authentication and  
// specify the AdventureWorks database as the database in use.   
//   
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
  
if ( $conn === false ) {  
   echo "Could not connect.<br>";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
// Set up the Transact-SQL query.  
//   
$tsql1 = "UPDATE Production.ProductReview  
          SET Comments = ?  
          WHERE ProductReviewID = ?";  
  
// Set the parameter values and put them in an array. Note that  
// $comments is converted to UTF-8 encoding with the PHP function  
// utf8_encode to simulate an application that uses UTF-8 encoded data.   
//   
$reviewID = 3;  
$comments = utf8_encode("testing");  
$params1 = array(  
                  array($comments,  
                        SQLSRV_PARAM_IN,  
                        SQLSRV_PHPTYPE_STRING('UTF-8')  
                  ),  
                  array($reviewID)  
                );  
  
// Execute the query.  
//   
$stmt1 = sqlsrv_query($conn, $tsql1, $params1);  
  
if ( $stmt1 === false ) {  
   echo "Error in statement execution.<br>";  
   die( print_r( sqlsrv_errors(), true));  
}  
else {  
   echo "The update was successfully executed.<br>";  
}  
  
// Retrieve the newly updated data.  
//   
$tsql2 = "SELECT Comments   
          FROM Production.ProductReview   
          WHERE ProductReviewID = ?";  
  
// Set up the parameter array.  
//   
$params2 = array($reviewID);  
  
// Execute the query.  
//   
$stmt2 = sqlsrv_query($conn, $tsql2, $params2);  
if ( $stmt2 === false ) {  
   echo "Error in statement execution.<br>";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
// Retrieve and display the data.   
//   
if ( sqlsrv_fetch($stmt2) ) {  
   echo "Comments: ";  
   $data = sqlsrv_get_field($stmt2,   
                            0,   
                            SQLSRV_PHPTYPE_STRING('UTF-8')  
                           );  
   echo $data."<br>";  
}  
else {  
   echo "Error in fetching data.<br>";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
// Free statement and connection resources.  
//   
sqlsrv_free_stmt( $stmt1 );  
sqlsrv_free_stmt( $stmt2 );  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[Récupération de données](../../connect/php/retrieving-data.md)

[Utilisation de données ASCII dans non Windows](../../connect/php/how-to-send-and-retrieve-ascii-data-in-linux-mac.md)

[Mise à jour des données &#40;pilotes Microsoft SQL Server pour PHP&#41;](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)

[référence d’API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Constantes &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[Exemple d’application &#40;pilote SQLSRV&#41;](../../connect/php/example-application-sqlsrv-driver.md)  
  

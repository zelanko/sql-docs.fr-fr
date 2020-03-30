---
title: Guide pratique pour récupérer des données binaires sous la forme d’un flux à l’aide du pilote SQLSRV | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- retrieving data, as a binary stream
- streaming data
ms.assetid: cd8d6382-abe6-48ee-9d10-4e6c52c0cb9a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3f77439f2369d7fbf4e27603bcbf8c8a2f8d8399
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67993477"
---
# <a name="how-to-retrieve-binary-data-as-a-stream-using-the-sqlsrv-driver"></a>Procédure : récupérer des données binaires sous la forme d’un flux à l’aide du pilote SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

La récupération de données sous forme de flux est disponible uniquement dans le pilote SQLSRV du [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], et non dans le pilote PDO_SQLSRV.  
  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] tire parti des flux PHP pour récupérer de grandes quantités de données binaires à partir du serveur. Cette rubrique montre comment récupérer des données binaires sous forme de flux.  
  
L’utilisation de flux pour récupérer des données binaires, comme des images, permet d’éviter l’utilisation de grandes quantités de mémoire de script en récupérant des blocs de données au lieu de charger l’objet entier dans la mémoire de script.  
  
## <a name="example"></a>Exemple  
L’exemple suivant récupère des données binaires, à savoir une image dans ce cas, à partir de la table *Production.ProductPhoto* de la base de données AdventureWorks. L’image est récupérée sous forme de flux et affichée dans le navigateur.  
  
La récupération de données d’image sous forme de flux s’effectue à l’aide de [sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md) et [sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md) avec le type de retour spécifié en tant que flux binaire. Le type de retour est spécifié à l’aide de la constante **SQLSRV_PHPTYPE_STREAM**. Pour plus d’informations sur les constantes **sqlsrv**, consultez [Constantes &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).  
  
L’exemple part du principe que SQL Server et la base de données [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) sont installés sur l’ordinateur local. Toute la sortie est écrite dans le navigateur quand l’exemple est exécuté à partir du navigateur.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up the Transact-SQL query. */  
$tsql = "SELECT LargePhoto   
         FROM Production.ProductPhoto   
         WHERE ProductPhotoID = ?";  
  
/* Set the parameter values and put them in an array. */  
$productPhotoID = 70;  
$params = array( $productPhotoID);  
  
/* Execute the query. */  
$stmt = sqlsrv_query($conn, $tsql, $params);  
if( $stmt === false )  
{  
     echo "Error in statement execution.</br>";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve and display the data.  
The return data is retrieved as a binary stream. */  
if ( sqlsrv_fetch( $stmt ) )  
{  
   $image = sqlsrv_get_field( $stmt, 0,   
                      SQLSRV_PHPTYPE_STREAM(SQLSRV_ENC_BINARY));  
   header("Content-Type: image/jpg");  
   fpassthru($image);  
}  
else  
{  
     echo "Error in retrieving data.</br>";  
     die(print_r( sqlsrv_errors(), true));  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
La spécification du type de retour dans l’exemple montre comment spécifier le type de retour PHP en tant que flux binaire. Techniquement, cela n’est pas obligatoire dans l’exemple, car le champ *LargePhoto* est de type SQL Server varbinary(max), et il est donc retourné en tant que flux binaire par défaut. Pour plus d’informations sur les types de données PHP par défaut, consultez [Default PHP Data Types](../../connect/php/default-php-data-types.md). Pour plus d’informations sur la spécification des types de retour PHP, consultez [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).  
  
## <a name="see-also"></a>Voir aussi  
[Récupération de données](../../connect/php/retrieving-data.md)

[Récupération des données sous la forme d’un flux à l’aide du pilote SQLSRV](../../connect/php/retrieving-data-as-a-stream-using-the-sqlsrv-driver.md)

[À propos des exemples de code dans la documentation](../../connect/php/about-code-examples-in-the-documentation.md)  
  

---
title: "Comment : récupérer des paramètres de sortie à l’aide du pilote SQLSRV | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stored procedure support
ms.assetid: 1157bab7-6ad1-4bdb-a81c-662eea3e7fcd
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 91401b79d504a140147572c5f2c1f7abc439d221
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="how-to-retrieve-output-parameters-using-the-sqlsrv-driver"></a>Procédure : récupérer des paramètres de sortie à l’aide du pilote SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cette rubrique montre comment appeler une procédure stockée dans laquelle un seul paramètre a été défini en tant que paramètre de sortie. Notez que, quand vous récupérez un paramètre de sortie ou d’entrée/sortie, tous les résultats retournés par la procédure stockée doivent être consommés pour que la valeur de paramètre retournée soit accessible.  
  
> [!NOTE]  
> Les variables initialisées ou mises à jour avec la valeur **null**, **DateTime**ou des types de flux ne peuvent pas être utilisées comme paramètres de sortie.  
  
Une troncation de données peut se produire quand des types de flux comme SQLSRV_SQLTYPE_VARCHAR('max') sont utilisés comme paramètres de sortie. Les types de flux ne sont pas pris en charge comme paramètres de sortie. Pour les types autres que types de flux, une troncation de données peut se produire si la longueur du paramètre de sortie n’est pas spécifiée ou si la longueur spécifiée n’est pas assez élevée pour le paramètre de sortie.  
  
## <a name="example"></a>Exemple  
L’exemple suivant appelle une procédure stockée qui retourne les ventes de l’année jusqu’à ce jour effectuées par un employé spécifique. La variable PHP *$lastName* est un paramètre d’entrée et *$salesYTD* est un paramètre de sortie.  
  
> [!NOTE]  
> L’initialisation de *$salesYTD* à 0.0 définit le PHPTYPE retourné sur **float**. Pour garantir l’intégrité du type de données, les paramètres de sortie doivent être initialisés avant d’appeler la procédure stockée, ou bien le PHPTYPE souhaité doit être spécifié. Pour plus d’informations sur la spécification du PHPTYPE, consultez [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).  
  
Étant donné qu’un seul résultat est retourné par la procédure stockée, *$salesYTD* contient la valeur retournée du paramètre de sortie immédiatement après l’exécution de la procédure stockée.  
  
> [!NOTE]  
> Appeler les procédures stockées à l’aide de la syntaxe canonique est la pratique recommandée. Pour plus d’informations sur la syntaxe canonique, consultez [Appel d’une procédure stockée](http://go.microsoft.com/fwlink/?linkid=119517).  
  
L’exemple suppose que SQL Server et la base de données [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) sont installés sur l’ordinateur local. Toute la sortie est écrite dans la console quand l’exemple est exécuté à partir de la ligne de commande.  
  
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
  
/* Drop the stored procedure if it already exists. */  
$tsql_dropSP = "IF OBJECT_ID('GetEmployeeSalesYTD', 'P') IS NOT NULL  
                DROP PROCEDURE GetEmployeeSalesYTD";  
$stmt1 = sqlsrv_query( $conn, $tsql_dropSP);  
if( $stmt1 === false )  
{  
     echo "Error in executing statement 1.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Create the stored procedure. */  
$tsql_createSP = " CREATE PROCEDURE GetEmployeeSalesYTD  
                   @SalesPerson nvarchar(50),  
                   @SalesYTD money OUTPUT  
                   AS  
                   SELECT @SalesYTD = SalesYTD  
                   FROM Sales.SalesPerson AS sp  
                   JOIN HumanResources.vEmployee AS e   
                   ON e.EmployeeID = sp.SalesPersonID  
                   WHERE LastName = @SalesPerson";  
$stmt2 = sqlsrv_query( $conn, $tsql_createSP);  
if( $stmt2 === false )  
{  
     echo "Error in executing statement 2.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/*--------- The next few steps call the stored procedure. ---------*/  
  
/* Define the Transact-SQL query. Use question marks (?) in place of  
 the parameters to be passed to the stored procedure */  
$tsql_callSP = "{call GetEmployeeSalesYTD( ?, ? )}";  
  
/* Define the parameter array. By default, the first parameter is an  
INPUT parameter. The second parameter is specified as an OUTPUT  
parameter. Initializing $salesYTD to 0.0 sets the returned PHPTYPE to  
float. To ensure data type integrity, output parameters should be  
initialized before calling the stored procedure, or the desired  
PHPTYPE should be specified in the $params array.*/  
$lastName = "Blythe";  
$salesYTD = 0.0;  
$params = array(   
                 array($lastName, SQLSRV_PARAM_IN),  
                 array($salesYTD, SQLSRV_PARAM_OUT)  
               );  
  
/* Execute the query. */  
$stmt3 = sqlsrv_query( $conn, $tsql_callSP, $params);  
if( $stmt3 === false )  
{  
     echo "Error in executing statement 3.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Display the value of the output parameter $salesYTD. */  
echo "YTD sales for ".$lastName." are ". $salesYTD. ".";  
  
/*Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt1);  
sqlsrv_free_stmt( $stmt2);  
sqlsrv_free_stmt( $stmt3);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[Procédure : spécifier la direction du paramètre à l’aide du pilote SQLSRV](../../connect/php/how-to-specify-parameter-direction-using-the-sqlsrv-driver.md)  
[How to: Retrieve Input and Output Parameters Using the SQLSRV Driver](../../connect/php/how-to-retrieve-input-and-output-parameters-using-the-sqlsrv-driver.md)  
[Récupération de données](../../connect/php/retrieving-data.md)  
  


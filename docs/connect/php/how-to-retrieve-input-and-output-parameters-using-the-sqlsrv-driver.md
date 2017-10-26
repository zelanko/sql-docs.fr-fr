---
title: "Comment : récupérer des paramètres d’e/s à l’aide du pilote SQLSRV | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stored procedure support
ms.assetid: 9a7c5f60-67f9-4968-a3a8-c256ee481da2
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9278465398b033d198ec5b3304f9c601f5cb677b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="how-to-retrieve-input-and-output-parameters-using-the-sqlsrv-driver"></a>How to: Retrieve Input and Output Parameters Using the SQLSRV Driver
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cette rubrique montre comment utiliser le pilote SQLSRV pour appeler une procédure stockée dans laquelle un paramètre a été défini comme paramètre d’entrée/sortie, et comment récupérer les résultats. Notez que, quand vous récupérez un paramètre de sortie ou d’entrée/sortie, tous les résultats retournés par la procédure stockée doivent être consommés pour que la valeur de paramètre retournée soit accessible.  
  
> [!NOTE]  
> Les variables initialisées ou mises à jour avec la valeur **null**, **DateTime**ou des types de flux ne peuvent pas être utilisées comme paramètres de sortie.  
  
## <a name="example"></a>Exemple  
L’exemple suivant appelle une procédure stockée qui soustrait des heures de congé utilisées des heures de congé disponibles d’un employé spécifié. La variable qui représente les heures de congé utilisées, *$vacationHrs*, est passée à la procédure stockée comme paramètre d’entrée. Après la mise à jour des heures de congé disponibles, la procédure stockée utilise le même paramètre pour retourner le nombre d’heures de congé restantes.  
  
> [!NOTE]  
> L’initialisation de *$vacationHrs* avec la valeur 4 définit le PHPTYPE retourné sur “entier”. Pour garantir l’intégrité du type de données, les paramètres d’entrée/sortie doivent être initialisés avant d’appeler la procédure stockée, ou bien le PHPTYPE souhaité doit être spécifié. Pour plus d’informations sur la spécification du PHPTYPE, consultez [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).  
  
Étant donné que la procédure stockée retourne deux résultats, [sqlsrv_next_result](../../connect/php/sqlsrv-next-result.md) doit être appelée après l’exécution de la procédure stockée pour rendre disponible la valeur du paramètre de sortie. Après avoir appelé **sqlsrv_next_result**, *$vacationHrs* contient la valeur du paramètre de sortie retourné par la procédure stockée.  
  
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
$tsql_dropSP = "IF OBJECT_ID('SubtractVacationHours', 'P') IS NOT NULL  
                DROP PROCEDURE SubtractVacationHours";  
$stmt1 = sqlsrv_query( $conn, $tsql_dropSP);  
if( $stmt1 === false )  
{  
     echo "Error in executing statement 1.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Create the stored procedure. */  
$tsql_createSP = "CREATE PROCEDURE SubtractVacationHours  
                        @EmployeeID int,  
                        @VacationHrs smallint OUTPUT  
                  AS  
                  UPDATE HumanResources.Employee  
                  SET VacationHours = VacationHours - @VacationHrs  
                  WHERE EmployeeID = @EmployeeID;  
                  SET @VacationHrs = (SELECT VacationHours  
                                      FROM HumanResources.Employee  
                                      WHERE EmployeeID = @EmployeeID)";  
  
$stmt2 = sqlsrv_query( $conn, $tsql_createSP);  
if( $stmt2 === false )  
{  
     echo "Error in executing statement 2.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/*--------- The next few steps call the stored procedure. ---------*/  
  
/* Define the Transact-SQL query. Use question marks (?) in place of  
the parameters to be passed to the stored procedure */  
$tsql_callSP = "{call SubtractVacationHours( ?, ?)}";  
  
/* Define the parameter array. By default, the first parameter is an  
INPUT parameter. The second parameter is specified as an INOUT  
parameter. Initializing $vacationHrs to 8 sets the returned PHPTYPE to  
integer. To ensure data type integrity, output parameters should be  
initialized before calling the stored procedure, or the desired  
PHPTYPE should be specified in the $params array.*/  
  
$employeeId = 4;  
$vacationHrs = 8;  
$params = array(   
                 array($employeeId, SQLSRV_PARAM_IN),  
                 array($vacationHrs, SQLSRV_PARAM_INOUT)  
               );  
  
/* Execute the query. */  
$stmt3 = sqlsrv_query( $conn, $tsql_callSP, $params);  
if( $stmt3 === false )  
{  
     echo "Error in executing statement 3.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Display the value of the output parameter $vacationHrs. */  
sqlsrv_next_result($stmt3);  
echo "Remaining vacation hours: ".$vacationHrs;  
  
/*Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt1);  
sqlsrv_free_stmt( $stmt2);  
sqlsrv_free_stmt( $stmt3);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[Procédure : spécifier la direction du paramètre à l’aide du pilote SQLSRV](../../connect/php/how-to-specify-parameter-direction-using-the-sqlsrv-driver.md)  
[Procédure : récupérer des paramètres de sortie à l’aide du pilote SQLSRV](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md)  
[Récupération de données](../../connect/php/retrieving-data.md)  
  


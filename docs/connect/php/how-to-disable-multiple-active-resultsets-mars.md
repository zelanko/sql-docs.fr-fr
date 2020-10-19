---
title: 'Procédure : désactiver MARS (Multiple Active Result Set)'
description: Découvrez comment désactiver le support MARS (Multiple Active Result Set) lors de l’utilisation des pilotes Microsoft pour PHP pour SQL Server
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- multiple active result sets, disabling
- MARS, disabling
ms.assetid: 1912ad05-d0a4-40ff-8888-0d85bb36a807
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 11ca08618f0b8d7675e8ec74ec259d4225d44aba
ms.sourcegitcommit: 7eb80038c86acfef1d8e7bfd5f4e30e94aed3a75
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2020
ms.locfileid: "92080618"
---
# <a name="how-to-disable-multiple-active-resultsets-mars"></a>Procédure : Désactiver MARS (Multiple Active Result Set)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Si vous avez besoin de vous connecter à une source de données SQL Server qui n’active pas MARS (Multiple Active Result Sets), vous pouvez utiliser l’option de connexion MultipleActiveResultSets pour désactiver ou activer MARS.  
  
## <a name="procedure"></a>Procédure  
  
#### <a name="to-disable-mars-support"></a>Pour désactiver la prise en charge de MARS  
  
-   Utilisez l’option de connexion suivante :  
  
    ```  
    'MultipleActiveResultSets'=>false  
    ```  
  
    Si votre application tente d’exécuter une requête sur une connexion qui a un jeu de résultats actif ouvert, la deuxième tentative de requête retourne les informations d’erreur suivantes :  
  
    La connexion ne peut pas traiter cette opération, car il existe une instruction avec des résultats en attente.  Pour rendre la connexion disponible pour d’autres requêtes, extrayez tous les résultats, annulez l’instruction ou libérez-la. Pour plus d’informations sur l’option de connexion MultipleActiveResultSets, consultez [Connection Options](../../connect/php/connection-options.md).  
  
## <a name="sqlsrv-example"></a>Exemple SQLSRV  
L’exemple suivant montre comment désactiver la prise en charge de MARS, à l’aide du pilote SQLSRV de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks", 'MultipleActiveResultSets'=> false);  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="pdo_sqlsrv-example"></a>Exemple PDO_SQLSRV  
L’exemple suivant montre comment désactiver la prise en charge de MARS, à l’aide du pilote PDO_SQLSRV de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
```  
<?php  
// Connect to the local server using Windows Authentication and AdventureWorks database  
$serverName = "(local)";   
$database = "AdventureWorks";  
  
try {  
   $conn = new PDO(" sqlsrv:server=$serverName ; Database=$database ; MultipleActiveResultSets=false ", NULL, NULL);   
   $conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );   
}  
  
catch( PDOException $e ) {  
   die( "Error connecting to SQL Server" );   
}  
  
$conn = null;   
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[Connexion au serveur](../../connect/php/connecting-to-the-server.md)  
  

---
title: Guide pratique pour désactiver MARS (Multiple Active Result Set) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- multiple active result sets, disabling
- MARS, disabling
ms.assetid: 1912ad05-d0a4-40ff-8888-0d85bb36a807
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fc5e138bbd9e293076b0f05173d9d4a8d1747fde
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37985601"
---
# <a name="how-to-disable-multiple-active-resultsets-mars"></a>Procédure : désactiver MARS (Multiple Active Result Set)
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
  
## <a name="example"></a> Exemple  
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
  
## <a name="example"></a> Exemple  
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
  
## <a name="see-also"></a> Voir aussi  
[Connexion au serveur](../../connect/php/connecting-to-the-server.md)  
  

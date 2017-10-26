---
title: "Comment : se connecter sur un Port spécifié | Documents Microsoft"
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
- connecting to the server, specifying a port
ms.assetid: 65a154d1-375c-439b-a653-7815c9d70ff3
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 88115d77c56cafed731aa2a9cf6c39afcd191618
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="how-to-connect-on-a-specified-port"></a>Procédure : se connecter sur un port spécifié
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cette rubrique explique comment se connecter à SQL Server sur un port spécifié avec le [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
### <a name="to-connect-on-a-specified-port"></a>Pour se connecter sur un port spécifié  
  
1.  Vérifiez le port sur lequel le serveur est configuré pour accepter les connexions. Pour plus d’informations sur la configuration d’un serveur pour accepter les connexions sur un port spécifié, consultez [Comment : configurer un serveur pour écouter un port de TCP spécifique (Gestionnaire de Configuration SQL Server)](http://go.microsoft.com/fwlink/?LinkId=121865).  
  
2.  Ajoutez le port souhaité pour le *$serverName* paramètre de la [sqlsrv_connect](../../connect/php/sqlsrv-connect.md) (fonction). Séparez le nom du serveur et le port avec une virgule. Par exemple, les lignes de code suivantes utilisent le pilote SQLSRV pour illustrer comment se connecter à un serveur nommé *myServer* sur le port 1521 :  
  
    ```  
    $serverName = "myServer, 1521";  
    sqlsrv_connect( $serverName );  
    ```  
  
    Les lignes de code suivantes utilisent le pilote PDO_SQLSRV pour illustrer comment se connecter à un serveur nommé *myServer* sur le port 1521 :  
  
    ```  
    $serverName = "(local), 1521";  
    $database = "AdventureWorks";  
    $conn = new PDO( "sqlsrv:server=$serverName;Database=$database", "", "");  
    ```  
  
## <a name="see-also"></a>Voir aussi  
[Connexion au serveur](../../connect/php/connecting-to-the-server.md)  
[Guide de programmation pour le pilote SQL PHP](../../connect/php/programming-guide-for-php-sql-driver.md)
[Prise en main du pilote SQL PHP](../../connect/php/getting-started-with-the-php-sql-driver.md) 
[Référence d’API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Référence de pilote PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  


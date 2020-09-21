---
title: 'Procédure : Se connecter sur un port spécifié'
description: Découvrez comment se connecter à une base de données configurée sur un port spécifique à l’aide des Pilotes Microsoft SQLSRV et PDO_SQLSRV pour PHP pour SQL Server.
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to the server, specifying a port
ms.assetid: 65a154d1-375c-439b-a653-7815c9d70ff3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b55f12bbfe4bbe255af2d62c2ed0c5ab3f968e98
ms.sourcegitcommit: 129f8574eba201eb6ade1f1620c6b80dfe63b331
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2020
ms.locfileid: "87435235"
---
# <a name="how-to-connect-on-a-specified-port"></a>Procédure : Se connecter sur un port spécifié
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cette rubrique explique comment se connecter à SQL Server sur un port spécifié avec le [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
### <a name="to-connect-on-a-specified-port"></a>Pour se connecter sur un port spécifié  
  
1.  Vérifiez le port sur lequel le serveur est configuré pour accepter les connexions. Pour savoir comment configurer un serveur de façon à ce qu’il accepte les connexions sur un port spécifié, consultez [Guide pratique pour configurer un serveur de sorte qu’il écoute un port TCP spécifique (Gestionnaire de configuration SQL Server)](../../database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port.md).  
  
2.  Ajoutez le port souhaité au paramètre *$serverName* de la fonction [sqlsrv_connect](../../connect/php/sqlsrv-connect.md). Séparez le nom du serveur et le port avec une virgule. Par exemple, les lignes de code suivantes utilisent le pilote SQLSRV pour illustrer comment se connecter à un serveur nommé *myServer* sur le port 1521 :  
  
    ```  
    $serverName = "myServer, 1521";  
    sqlsrv_connect( $serverName );  
    ```  
  
    Les lignes de code suivantes utilisent le pilote PDOSQL_SRV pour montrer comment se connecter à un serveur nommé *myServer* sur le port 1521 :  
  
    ```  
    $serverName = "(local), 1521";  
    $database = "AdventureWorks";  
    $conn = new PDO( "sqlsrv:server=$serverName;Database=$database", "", "");  
    ```  
  
## <a name="see-also"></a>Voir aussi  
[Connexion au serveur](../../connect/php/connecting-to-the-server.md)

[Guide de programmation pour les pilotes Microsoft pour PHP pour SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Bien démarrer avec les pilotes Microsoft pour PHP pour SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Informations de référence sur l’API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Référence de pilote PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  

---
description: sqlsrv_server_info
title: sqlsrv_server_info | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_server_info
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_server_info
- sqlsrv_server_info
ms.assetid: ef6fe2b7-d267-4379-b948-5626c4684367
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7eaf032b121dc3e93cb13f001cbebd3eaa75b796
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466687"
---
# <a name="sqlsrv_server_info"></a>sqlsrv_server_info
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Retourne des informations sur le serveur. Une connexion doit être établie avant d’appeler cette fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sqlsrv_server_info( resource $conn)  
```  
  
#### <a name="parameters"></a>Paramètres  
*$conn*: ressource de connexion par laquelle le client et le serveur sont connectés.  
  
## <a name="return-value"></a>Valeur de retour  
Tableau associatif avec les clés suivantes :  
  
|Clé|Description|  
|-------|---------------|  
|CurrentDatabase|Base de données actuellement ciblée.|  
|SQLServerVersion|Version de SQL Server.|  
|SQLServerName|Le nom du serveur|  
  
## <a name="example"></a> Exemple  
L’exemple suivant écrit des informations de serveur dans la console quand l’exemple est exécuté à partir de la ligne de commande.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication. */  
$serverName = "(local)";  
$conn = sqlsrv_connect( $serverName);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
$server_info = sqlsrv_server_info( $conn);  
if( $server_info )  
{  
      foreach( $server_info as $key => $value)  
      {  
             echo $key.": ".$value."\n";  
      }  
}  
else  
{  
      echo "Error in retrieving server info.\n";  
      die( print_r( sqlsrv_errors(), true));  
}  
  
/* Free connection resources. */  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[Informations de référence sur l’API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  

[À propos des exemples de code dans la documentation](../../connect/php/about-code-examples-in-the-documentation.md)  
  

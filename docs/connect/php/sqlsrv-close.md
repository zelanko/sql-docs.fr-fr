---
title: sqlsrv_close | Documents Microsoft
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
apiname:
- sqlsrv_close
apitype: NA
helpviewer_keywords:
- sqlsrv_close
- API Reference, sqlsrv_close
ms.assetid: 6ac6209c-a134-4f8f-b88b-8eefaa1cbc7f
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ab9135195867a02dccf3885b551ab2a1f4f5ebb1
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsrvclose"></a>sqlsrv_close
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Ferme la connexion spécifiée et libère les ressources associées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sqlsrv_close( resource $conn )  
```  
  
#### <a name="parameters"></a>Paramètres  
*$conn*: connexion à fermer.  
  
## <a name="return-value"></a>Valeur retournée  
Valeur booléenne **true** sauf si la fonction est appelée avec un paramètre non valide. Si la fonction est appelée avec un paramètre non valide, **false** est retourné.  
  
> [!NOTE]  
> **Null** est un paramètre valide pour cette fonction. Ainsi, la fonction peut être appelée plusieurs fois dans un script. Par exemple, si vous fermez une connexion dans une condition d’erreur et refermez à la fin du script, le deuxième appel à **sqlsrv_close** retournera **true** , car le premier appel à **sqlsrv_ Fermez** (dans la condition d’erreur) définit la ressource de connexion à **null**.  
  
## <a name="example"></a>Exemple  
L’exemple suivant ferme une connexion. L’exemple part du principe que SQL Server est installé sur l’ordinateur local. Toute la sortie est écrite dans la console quand l’exemple est exécuté à partir de la ligne de commande.  
  
```  
<?php  
/*Connect to the local server using Windows Authentication and   
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$conn = sqlsrv_connect( $serverName);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
//-----------------------------------------------  
// Perform operations with connection here.  
//-----------------------------------------------  
  
/* Close the connection. */  
sqlsrv_close( $conn);  
echo "Connection closed.\n";  
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[référence d’API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[À propos des exemples de code dans la documentation](../../connect/php/about-code-examples-in-the-documentation.md)  
  


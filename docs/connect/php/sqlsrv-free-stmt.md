---
title: sqlsrv_free_stmt | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_free_stmt
apitype: NA
helpviewer_keywords:
- sqlsrv_free_stmt
- API Reference, sqlsrv_free_stmt
ms.assetid: 3c71f432-36ad-41e1-8ac7-587c82539448
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a6f062d1237cfc92c5697fa005b3f78268aa48f6
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67992717"
---
# <a name="sqlsrv_free_stmt"></a>sqlsrv_free_stmt
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Libère toutes les ressources associées à l’instruction spécifiée. L’instruction ne peut pas être réutilisée une fois que cette fonction a été appelée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sqlsrv_free_stmt( resource $stmt)  
```  
  
#### <a name="parameters"></a>Paramètres  
*$stmt*: instruction à fermer.  
  
## <a name="return-value"></a>Valeur de retour  
Valeur booléenne **true** sauf si la fonction est appelée avec un paramètre non valide. Si la fonction est appelée avec un paramètre non valide, **false** est retourné.  
  
> [!NOTE]  
> **Null** est un paramètre valide pour cette fonction. Ainsi, la fonction peut être appelée plusieurs fois dans un script. Par exemple, si vous libérez une instruction dans une condition d’erreur et que vous la libérez à nouveau à la fin du script, le deuxième appel à **sqlsrv_free_stmt** retourne **true** car le premier appel à **sqlsrv_free_stmt** (dans la condition d’erreur) affecte la valeur **null** à la ressource d’instruction.  
  
## <a name="example"></a>Exemple  
L’exemple suivant crée une ressource d’instruction, exécute une requête simple et appelle **sqlsrv_free_stmt** pour libérer toutes les ressources associées à l’instruction. L’exemple part du principe que SQL Server et la base de données [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) sont installés sur l’ordinateur local. Toute la sortie est écrite dans la console quand l’exemple est exécuté à partir de la ligne de commande.  
  
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
  
$stmt = sqlsrv_query( $conn, "SELECT * FROM Person.Contact");  
if( $stmt )  
{  
     echo "Statement executed.\n";  
}  
else  
{  
     echo "Query could not be executed.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/*-------------------------------  
     Process query results here.  
-------------------------------*/  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[Informations de référence sur l’API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  

[À propos des exemples de code dans la documentation](../../connect/php/about-code-examples-in-the-documentation.md)  

[sqlsrv_cancel](../../connect/php/sqlsrv-cancel.md)  
  

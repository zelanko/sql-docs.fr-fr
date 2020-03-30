---
title: sqlsrv_connect | Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_connect
apitype: NA
helpviewer_keywords:
- connecting to the server
- API Reference, sqlsrv_connect
- connection pooling support
- sqlsrv_connect
ms.assetid: 37836b49-258e-45ce-9549-b8bd85d6952d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 11da2b4eca130eafe93a01315aaa1f6d9919632c
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "68015037"
---
# <a name="sqlsrv_connect"></a>sqlsrv_connect
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Crée une ressource de connexion et ouvre une connexion. Par défaut, la connexion est tentée en utilisant l’authentification Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sqlsrv_connect( string $serverName [, array $connectionInfo])  
```  
  
#### <a name="parameters"></a>Paramètres  
*$serverName*: chaîne spécifiant le nom du serveur auquel une connexion est établie. Un nom d’instance (par exemple, « monServeur\nomInstance ») ou un numéro de port (par exemple, « monServeur, 1521 ») peuvent être inclus dans cette chaîne. Pour obtenir la description complète des options disponibles pour ce paramètre, consultez le mot clé Server dans la section Mots clés de chaîne de connexion du pilote ODBC dans [Utilisation de mots clés de chaîne de connexion avec SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
À compter de la version 3.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], vous pouvez aussi spécifier une instance LocalDB avec `"(localdb)\instancename"`. Pour plus d’informations, consultez [Prise en charge de LocalDB](../../connect/php/php-driver-for-sql-server-support-for-localdb.md).  
  
Également depuis la version 3.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], vous pouvez spécifier un nom de réseau virtuel, pour établir une connexion à un groupe de disponibilité AlwaysOn. Pour plus d’informations sur la prise en charge de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] pour [!INCLUDE[ssHADR](../../includes/sshadr_md.md)], consultez [Prise en charge de la haute disponibilité et de la récupération d'urgence](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).  
  
*$connectionInfo* [FACULTATIF]: **tableau** associatif qui contient des attributs de connexion (par exemple, **array**("Database" => "AdventureWorks")). Consultez [Connection Options](../../connect/php/connection-options.md) pour obtenir la liste des clés prises en charge pour le tableau.  
  
## <a name="return-value"></a>Valeur de retour  
Ressource de connexion PHP. Si aucune connexion ne peut être créée et ouverte correctement, **false** est retourné.  
  
## <a name="remarks"></a>Notes  
Si les valeurs des clés *UID* et *PWD* ne sont pas spécifiées dans le paramètre facultatif *$connectionInfo* , la connexion est tentée en utilisant l’authentification Windows. Pour plus d’informations sur la connexion au serveur, consultez [How to: Connect Using Windows Authentication](../../connect/php/how-to-connect-using-windows-authentication.md) et [How to: Connect Using SQL Server Authentication](../../connect/php/how-to-connect-using-sql-server-authentication.md).  
  
## <a name="example"></a>Exemple  
L’exemple suivant crée et ouvre une connexion en utilisant l’authentification Windows. L’exemple part du principe que SQL Server et la base de données [AdventureWorks](https://www.codeplex.com/SqlServerSamples) sont installés sur l’ordinateur local. Toute la sortie est écrite dans la console quand l’exemple est exécuté à partir de la ligne de commande.  
  
```  
<?php  
/*  
Connect to the local server using Windows Authentication and specify  
the AdventureWorks database as the database in use. To connect using  
SQL Server Authentication, set values for the "UID" and "PWD"  
 attributes in the $connectionInfo parameter. For example:  
$connectionInfo = array("UID" => $uid, "PWD" => $pwd, "Database"=>"AdventureWorks");  
*/  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
  
if( $conn )  
{  
     echo "Connection established.\n";  
}  
else  
{  
     echo "Connection could not be established.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
//-----------------------------------------------  
// Perform operations with connection.  
//-----------------------------------------------  
  
/* Close the connection. */  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[Informations de référence sur l’API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Connexion au serveur](../../connect/php/connecting-to-the-server.md)

[À propos des exemples de code dans la documentation](../../connect/php/about-code-examples-in-the-documentation.md)  
  

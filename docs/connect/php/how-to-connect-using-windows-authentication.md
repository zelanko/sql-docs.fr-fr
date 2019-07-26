---
title: 'Procédure: se connecter à l’aide de l’authentification Windows | Microsoft Docs'
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to the server, Windows Authentication
ms.assetid: f403a4e0-b0a8-4939-9dc1-e1209626367e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 84707c67491d4f02be41e6506fb233ee7afef9fe
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67936505"
---
# <a name="how-to-connect-using-windows-authentication"></a>Procédure : se connecter avec l’authentification Windows
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Par défaut, [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] utilise l’authentification Windows pour se connecter à SQL Server. Il est important de noter que, dans la plupart des scénarios, cela signifie que l’identité du processus ou du thread du serveur web (si ce dernier utilise l’emprunt d’identité) est utilisée pour la connexion au serveur, au lieu de l’identité d’un utilisateur final.  
  
Prenez en considération les points suivants quand vous utilisez l’authentification Windows pour la connexion à SQL Server :  
  
-   Les informations d’identification sous lesquelles le processus (ou thread) du serveur web est en cours d’exécution doivent correspondre à une connexion SQL Server valide pour pouvoir établir une connexion.  
  
-   Si SQL Server et le serveur web se trouvent sur des ordinateurs différents, configurez SQL Server de sorte à autoriser les connexions à distance.  
  
> [!NOTE]  
> Vous pouvez définir les attributs de connexion comme *Database* et *ConnectionPooling* quand vous établissez une connexion. Pour obtenir la liste complète des attributs de connexion pris en charge, consultez [Connection Options](../../connect/php/connection-options.md).  
  
Préférez l’authentification Windows pour la connexion à SQL Server dès lors que possible pour les raisons suivantes :  
  
-   Aucune information d’identification n’est transmise sur le réseau au cours de l’authentification  ; les noms d’utilisateur et mots de passe ne sont pas incorporés dans la chaîne de connexion de la base de données. Cela signifie qu’aucun utilisateur malveillant ne peut obtenir des informations d’identification en surveillant le réseau ou en consultant des chaînes de connexion dans des fichiers de configuration.  
  
-   Les utilisateurs sont soumis à une gestion centralisée des comptes ; des stratégies de sécurité sont appliquées comme des délais d’expiration des mots de passe, des longueurs minimales des mots de passe et un verrouillage des comptes à l’issue de plusieurs tentatives de connexion non valides.  
  
Si l’authentification Windows n’est pas possible d’un point de vue pratique, consultez [How to: Connect Using SQL Server Authentication](../../connect/php/how-to-connect-using-sql-server-authentication.md).  
  
## <a name="example"></a>Exemple  
En utilisant le pilote SQLSRV de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], l’exemple suivant a recours à l’authentification Windows pour établir une connexion à une instance locale de SQL Server. Une fois la connexion établie, le serveur est interrogé pour déterminer la connexion de l’utilisateur qui accède à la base de données.  
  
L’exemple part du principe que SQL Server et la base de données [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) sont installés sur l’ordinateur local. Toute la sortie est écrite dans le navigateur quand l’exemple est exécuté à partir du navigateur.  
  
```  
<?php  
/* Specify the server and connection string attributes. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
  
/* Connect using Windows Authentication. */  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Unable to connect.</br>";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Query SQL Server for the login of the user accessing the  
database. */  
$tsql = "SELECT CONVERT(varchar(32), SUSER_SNAME())";  
$stmt = sqlsrv_query( $conn, $tsql);  
if( $stmt === false )  
{  
     echo "Error in executing query.</br>";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve and display the results of the query. */  
$row = sqlsrv_fetch_array($stmt);  
echo "User login: ".$row[0]."</br>";  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>Exemple  
L’exemple suivant utilise le pilote PDO_SQLSRV pour accomplir la même tâche que l’exemple précédent.  
  
```  
<?php  
try {  
   $conn = new PDO( "sqlsrv:Server=(local);Database=AdventureWorks", NULL, NULL);   
   $conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );  
}  
  
catch( PDOException $e ) {  
   die( "Error connecting to SQL Server" );   
}  
  
echo "Connected to SQL Server\n";  
  
$query = 'select * from Person.ContactType';   
$stmt = $conn->query( $query );   
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){   
   print_r( $row );   
}  
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[Guide pratique pour se connecter à l’aide de l’authentification SQL Server](../../connect/php/how-to-connect-using-sql-server-authentication.md)

[Guide de programmation pour les pilotes Microsoft pour PHP pour SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[À propos des exemples de code dans la documentation](../../connect/php/about-code-examples-in-the-documentation.md)

[Guide pratique pour créer un compte de connexion SQL Server](../../relational-databases/security/authentication-access/create-a-login.md)

[Procédure : créer un utilisateur de base de données](../../relational-databases/security/authentication-access/create-a-database-user.md)

[Gestion des utilisateurs, rôles et connexions](../../relational-databases/server-management-objects-smo/tasks/managing-users-roles-and-logins.md)

[Séparation du schéma et de l’utilisateur](../../relational-databases/server-management-objects-smo/tasks/managing-users-roles-and-logins.md)

[Accorder des autorisations d’objet (Transact-SQL)](../../t-sql/statements/grant-object-permissions-transact-sql.md)  
  

---
title: "Comment : se connecter à l’aide de l’authentification SQL Server | Documents Microsoft"
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
- connecting to the server, SQL Server Authentication
ms.assetid: 8d298830-3186-47e7-aef6-586b457901c1
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8d4305d3b6dd25f3a06cda56db8e69fcd5d09972
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="how-to-connect-using-sql-server-authentication"></a>Procédure : se connecter à l’aide de l’authentification SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Le [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] prend en charge l’authentification SQL Server quand vous vous connectez à SQL Server.  
  
Vous devez utiliser l’authentification SQL Server uniquement quand l’authentification Windows n’est pas possible. Pour plus d’informations sur la connexion avec l’authentification Windows, consultez [How to: Connect Using Windows Authentication](../../connect/php/how-to-connect-using-windows-authentication.md).  
  
Prenez en considération les points suivants quand vous utilisez l’authentification SQL Server pour la connexion à SQL Server :  
  
-   L’authentification en mode mixte SQL Server doit être activée sur le serveur.  
  
-   L’ID utilisateur et un mot de passe (*UID* et *PWD* les attributs de connexion dans le pilote SQLSRV) doit être définie lorsque vous essayez d’établir une connexion. L’ID utilisateur et le mot de passe doivent être mappés à un utilisateur et un mot de passe SQL Server valides.  
  
> [!NOTE]  
> Les mots de passe qui contiennent une accolade fermante (}) doivent être précédés d’une deuxième accolade fermante. Par exemple, si le mot de passe SQL Server est “mot}depasse”, la valeur de l’attribut de connexion *PWD* doit être “mot}}depasse”.  
  
Appliquez les précautions suivantes quand vous utilisez l’authentification SQL Server pour vous connecter à SQL Server :  
  
-   Protégez (chiffrez) les informations d’identification transmises sur le réseau à partir du serveur web vers la base de données. Les informations d’identification sont chiffrées par défaut à compter de SQL Server 2005. Pour renforcer la sécurité, affectez la valeur “on” à l’attribut de connexion Encrypt pour chiffrer toutes les données envoyées au serveur.  
  
> [!NOTE]  
> L’affectation de la valeur “on” à l’attribut de connexion Encrypt peut diminuer les performances, car le chiffrement des données peut nécessiter beaucoup de ressources de calcul.  
  
-   N’incluez pas de valeurs pour les attributs de connexion *UID* et *PWD* en texte brut dans des scripts PHP. Vous devez stocker ces valeurs dans un répertoire propre à l’application avec des autorisations d’accès appropriées.  
  
-   Évitez d’utiliser le compte *sa* . Mappez l’application à un utilisateur de base de données qui possède les privilèges souhaités et utilisez un mot de passe fort.  
  
> [!NOTE]  
> Vous pouvez définir des attributs de connexion autres que l’ID utilisateur et le mot de passe quand vous établissez une connexion. Pour obtenir la liste complète des attributs de connexion pris en charge, consultez [Connection Options](../../connect/php/connection-options.md).  
  
## <a name="example"></a>Exemple  
L’exemple suivant utilise le pilote SQLSRV avec l’authentification SQL Server pour établir une connexion à une instance locale de SQL Server. Les valeurs des *UID* et *PWD* attributs de connexion sont extraites des fichiers de texte spécifique à l’application, *uid.txt* et *pwd.txt*, dans le *C:\AppData* active. Une fois la connexion établie, le serveur est interrogé pour vérifier la connexion de l’utilisateur.  
  
L’exemple part du principe que SQL Server et la base de données [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) sont installés sur l’ordinateur local. Toute la sortie est écrite dans le navigateur quand l’exemple est exécuté à partir du navigateur.  
  
```  
<?php  
/* Specify the server and connection string attributes. */  
$serverName = "(local)";  
  
/* Get UID and PWD from application-specific files.  */  
$uid = file_get_contents("C:\AppData\uid.txt");  
$pwd = file_get_contents("C:\AppData\pwd.txt");  
$connectionInfo = array( "UID"=>$uid,  
                         "PWD"=>$pwd,  
                         "Database"=>"AdventureWorks");  
  
/* Connect using SQL Server Authentication. */  
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
Cet exemple utilise le pilote PDO_SQLSRV pour illustrer comment se connecter avec l’authentification SQL Server.  
  
```  
<?php  
   $serverName = "(local)";   
   $database = "AdventureWorks";  
  
   // Get UID and PWD from application-specific files.   
   $uid = file_get_contents("C:\AppData\uid.txt");  
   $pwd = file_get_contents("C:\AppData\pwd.txt");  
  
   try {  
      $conn = new PDO( "sqlsrv:server=$serverName;Database = $database", $uid, $pwd);   
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
  
   // Free statement and connection resources.   
   $stmt = null;   
   $conn = null;   
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[How to: Connect Using SQL Server Authentication](../../connect/php/how-to-connect-using-sql-server-authentication.md)  
[Guide de programmation pour le pilote SQL PHP](../../connect/php/programming-guide-for-php-sql-driver.md)
[À propos des exemples de code dans la documentation](../../connect/php/about-code-examples-in-the-documentation.md)  
[SUSER_SNAME (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=106382)  
[Procédure : créer un compte de connexion SQL Server](http://go.microsoft.com/fwlink/?LinkId=106325)  
[Procédure : créer un utilisateur de base de données](http://go.microsoft.com/fwlink/?LinkId=106327)  
[Gestion des utilisateurs, rôles et connexions](http://go.microsoft.com/fwlink/?LinkId=106329)  
[Séparation utilisateur-schéma](http://go.microsoft.com/fwlink/?LinkId=106330)  
[Accorder des autorisations d’objet (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=106332)  
  


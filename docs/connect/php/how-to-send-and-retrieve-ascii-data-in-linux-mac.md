---
title: 'Comment : envoyer et récupérer des données ASCII dans Linux et macOS (SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 01/16/2018
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- retrieving data, ASCII data
- sending data
- linux
- macOS
author: yitam
ms.author: v-yitam
manager: mbarwin
ms.openlocfilehash: 2fe78cc80cd7ca77f09465fb7d3e92482da7d008
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63181157"
---
# <a name="how-to-send-and-retrieve-ascii-data-in-linux-and-macos"></a>Guide pratique pour envoyer et récupérer des données ASCII dans Linux et macOS 
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cet article suppose que les paramètres régionaux ASCII (UTF-8) ont été générés ou installés dans vos systèmes Linux ou macOS. 

Pour envoyer ou récupérer des jeux de caractères ASCII pour le serveur :  

1.  Si les paramètres régionaux de votre choix ne sont pas la valeur par défaut dans votre environnement de système, assurez-vous que vous appelez `setlocale(LC_ALL, $locale)` avant d’effectuer la première connexion. La fonction de setlocale() PHP modifie les paramètres régionaux uniquement pour le script en cours, et si elle est appelée après avoir établi la première connexion, il peut être ignoré.
 
2.  Lorsque vous utilisez le pilote SQLSRV, vous pouvez spécifier `'CharacterSet' => SQLSRV_ENC_CHAR` en tant que connexion option, mais cette étape est facultative car il s’agit de la valeur par défaut de codage.

3.  Lorsque vous utilisez le pilote PDO_SQLSRV, il existe deux façons. Tout d’abord, lors de la connexion, définissez `PDO::SQLSRV_ATTR_ENCODING` à `PDO::SQLSRV_ENCODING_SYSTEM` (pour obtenir un exemple de définition d’une option de connexion, consultez [PDO::__construct](../../connect/php/pdo-construct.md)). Vous pouvez également, une fois connecté, ajoutez cette ligne `$conn->setAttribute(PDO::SQLSRV_ATTR_ENCODING, PDO::SQLSRV_ENCODING_SYSTEM);` 
  
Lorsque vous spécifiez le codage d’une ressource de connexion (en SQLSRV) ou un objet de connexion (PDO_SQLSRV), le pilote part du principe que les autres chaînes de connexion utilisent ce même encodage. Les chaînes de nom de serveur et de requête sont également supposées utiliser le même jeu de caractères.  
  
L’encodage pour le pilote PDO_SQLSRV par défaut est UTF-8 (PDO::SQLSRV_ENCODING_UTF8), à la différence du pilote SQLSRV. Pour plus d’informations sur ces constantes, consultez [Constantes &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md). 
  
## <a name="example"></a>Exemple  
Les exemples suivants montrent comment envoyer et récupérer des données ASCII utilisant les pilotes PHP pour SQL Server en spécifiant des paramètres régionaux spécifiques avant d’établir la connexion. Les paramètres régionaux dans les différentes plateformes Linux peuvent être nommés différemment à partir des mêmes paramètres régionaux dans macOS. Par exemple, les paramètres régionaux nous ISO-8859-1 (Latin 1) sont `en_US.ISO-8859-1` dans Linux, alors que dans macOS est le nom `en_US.ISO8859-1`.
  
Les exemples supposent que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé sur un serveur. Toutes les sorties sont écrites dans le navigateur quand les exemples sont exécutés à partir du navigateur.  
  
```  
<?php  
  
// SQLSRV Example
//
// Setting locale for the script is only necessary if Latin 1 is not the default 
// in the environment
$locale = strtoupper(PHP_OS) === 'LINUX' ? 'en_US.ISO-8859-1' : 'en_US.ISO8859-1';
setlocale(LC_ALL, $locale);
        
$serverName = 'MyServer';
$database = 'Test';
$connectionInfo = array('Database'=>'Test', 'UID'=>$uid, 'PWD'=>$pwd);
$conn = sqlsrv_connect($serverName, $connectionInfo);
  
if ($conn === false) {
    echo "Could not connect.<br>";  
    die(print_r(sqlsrv_errors(), true));
}  
  
// Set up the Transact-SQL query to create a test table
//   
$stmt = sqlsrv_query($conn, "CREATE TABLE [Table1] ([c1_int] int, [c2_varchar] varchar(512))");

// Insert data using a parameter array 
//
$tsql = "INSERT INTO [Table1] (c1_int, c2_varchar) VALUES (?, ?)";
  
// Execute the query, $value being some ASCII string
//   
$stmt = sqlsrv_query($conn, $tsql, array(1, array($value, SQLSRV_PARAM_IN, SQLSRV_PHPTYPE_STRING(SQLSRV_ENC_CHAR))));
  
if ($stmt === false) {
    echo "Error in statement execution.<br>";  
    die(print_r(sqlsrv_errors(), true));  
}  
else {  
    echo "The insertion was successfully executed.<br>";  
}  
  
// Retrieve the newly inserted data
//   
$stmt = sqlsrv_query($conn, "SELECT * FROM Table1");
$outValue = null;  
if ($stmt === false) {  
    echo "Error in statement execution.<br>";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
// Retrieve and display the data
//   
if (sqlsrv_fetch($stmt)) {  
    $outValue = sqlsrv_get_field($stmt, 1, SQLSRV_PHPTYPE_STRING(SQLSRV_ENC_CHAR));
    echo "Value: " . $outValue . "<br>";
    if ($value !== $outValue) {
        echo "Data retrieved, \'$outValue\', is unexpected!<br>";
    }
}  
else {  
    echo "Error in fetching data.<br>";  
    die(print_r(sqlsrv_errors(), true));  
}  

// Free statement and connection resources
//   
sqlsrv_free_stmt($stmt);  
sqlsrv_close($conn);  
?>  
```  
  
```
<?php  
  
// PDO_SQLSRV Example:
//
// Setting locale for the script is only necessary if Latin 1 is not the default 
// in the environment
$locale = strtoupper(PHP_OS) === 'LINUX' ? 'en_US.ISO-8859-1' : 'en_US.ISO8859-1';
setlocale(LC_ALL, $locale);
        
$serverName = 'MyServer';
$database = 'Test';

try {
    $conn = new PDO("sqlsrv:Server=$serverName;Database=$database;", $uid, $pwd);
    $conn->setAttribute(PDO::SQLSRV_ATTR_ENCODING, PDO::SQLSRV_ENCODING_SYSTEM);
    
    // Set up the Transact-SQL query to create a test table
    //   
    $stmt = $conn->query("CREATE TABLE [Table1] ([c1_int] int, [c2_varchar] varchar(512))");
    
    // Insert data using parameters, $value being some ASCII string
    //
    $stmt = $conn->prepare("INSERT INTO [Table1] (c1_int, c2_varchar) VALUES (:var1, :var2)");
    $stmt->bindValue(1, 1);
    $stmt->bindParam(2, $value);
    $stmt->execute();
    
    // Retrieve and display the data
    //
    $stmt = $conn->query("SELECT * FROM [Table1]");
    $outValue = null;
    if ($row = $stmt->fetch()) {
        $outValue = $row[1];
        echo "Value: " . $outValue . "<br>";
        if ($value !== $outValue) {
            echo "Data retrieved, \'$outValue\', is unexpected!<br>";
        }
    }
} catch (PDOException $e) {
    echo $e->getMessage() . "<br>";
} finally {
    // Free statement and connection resources
    //
    unset($stmt);
    unset($conn);
}

?>  
```  

## <a name="see-also"></a>Voir aussi  
[Récupération de données](../../connect/php/retrieving-data.md)  
[Utilisation des données UTF-8](../../connect/php/how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support.md)
[mise à jour des données &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)  
[Informations de référence sur l’API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Constantes &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
[Exemple d’application &#40;pilote SQLSRV&#41;](../../connect/php/example-application-sqlsrv-driver.md)  
  

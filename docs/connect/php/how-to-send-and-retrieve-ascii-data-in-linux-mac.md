---
title: 'Procédure: envoyer et récupérer des données ASCII dans Linux et macOS (SQL) | Microsoft Docs'
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
manager: v-mabarw
ms.openlocfilehash: 9edd73f5ef01d1d3f22db78400cc3c204efe1379
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68251905"
---
# <a name="how-to-send-and-retrieve-ascii-data-in-linux-and-macos"></a>Guide pratique pour envoyer et récupérer des données ASCII dans Linux et macOS 
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cet article suppose que les paramètres régionaux ASCII (non UTF-8) ont été générés ou installés sur vos systèmes Linux ou macOS. 

Pour envoyer ou récupérer des jeux de caractères ASCII sur le serveur:  

1.  Si les paramètres régionaux souhaités ne sont pas la valeur par défaut dans votre environnement système, `setlocale(LC_ALL, $locale)` veillez à appeler avant d’établir la première connexion. La fonction PHP setlocale () modifie les paramètres régionaux uniquement pour le script en cours et, si elle est appelée après avoir effectué la première connexion, elle peut être ignorée.
 
2.  Lorsque vous utilisez le pilote sqlsrv, vous pouvez `'CharacterSet' => SQLSRV_ENC_CHAR` spécifier en tant qu’option de connexion, mais cette étape est facultative, car il s’agit de l’encodage par défaut.

3.  Lorsque vous utilisez le pilote PDO_SQLSRV, il existe deux façons de procéder. Tout d’abord, lorsque vous établissez `PDO::SQLSRV_ATTR_ENCODING` la `PDO::SQLSRV_ENCODING_SYSTEM` connexion, affectez à la valeur (pour obtenir un exemple de définition d’une option de connexion, consultez [PDO:: __construct](../../connect/php/pdo-construct.md)). Vous pouvez également ajouter cette ligne après la connexion réussie.`$conn->setAttribute(PDO::SQLSRV_ATTR_ENCODING, PDO::SQLSRV_ENCODING_SYSTEM);` 
  
Lorsque vous spécifiez l’encodage d’une ressource de connexion (dans SQLSRV) ou d’un objet de connexion (PDO_SQLSRV), le pilote part du principe que les autres chaînes d’option de connexion utilisent ce même encodage. Les chaînes de nom de serveur et de requête sont également supposées utiliser le même jeu de caractères.  
  
L’encodage par défaut pour le pilote PDO_SQLSRV est UTF-8 (PDO:: SQLSRV_ENCODING_UTF8), contrairement au pilote SQLSRV. Pour plus d’informations sur ces constantes, consultez [Constantes &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md). 
  
## <a name="example"></a>Exemple  
Les exemples suivants montrent comment envoyer et récupérer des données ASCII à l’aide des pilotes PHP pour SQL Server en spécifiant des paramètres régionaux particuliers avant d’établir la connexion. Les paramètres régionaux de différentes plateformes Linux peuvent être nommés différemment des mêmes paramètres régionaux dans macOS. Par exemple, les paramètres régionaux ISO-8859-1 (latin 1) des États `en_US.ISO-8859-1` -Unis sont dans Linux tandis que `en_US.ISO8859-1`dans MacOS le nom est.
  
Les exemples partent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du principe que est installé sur un serveur. Toutes les sorties sont écrites dans le navigateur quand les exemples sont exécutés à partir du navigateur.  
  
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
[Utilisation des](../../connect/php/how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support.md)
données de mise à jour des données UTF-8[ &#40;Microsoft drivers&#41; for PHP for SQL Server](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)  
[Informations de référence sur l’API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Constantes &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
[Exemple d’application &#40;pilote SQLSRV&#41;](../../connect/php/example-application-sqlsrv-driver.md)  
  

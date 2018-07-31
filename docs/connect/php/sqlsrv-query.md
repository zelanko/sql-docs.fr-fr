---
title: sqlsrv_query | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- sqlsrv_query
apitype: NA
helpviewer_keywords:
- sqlsrv_query
- executing queries
- API Reference, sqlsrv_query
ms.assetid: 9fa7c4c8-4da8-4299-9893-f61815055aa3
caps.latest.revision: 46
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8f4ecf98769f064c6d25b1aa466d8e4fe27f5ab5
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38979961"
---
# <a name="sqlsrvquery"></a>sqlsrv_query
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Prépare et exécute une instruction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sqlsrv_query(resource $conn, string $tsql [, array $params [, array $options]])  
```  
  
#### <a name="parameters"></a>Paramètres  
*$conn*: ressource de connexion associée à l’instruction préparée.  
  
*$tsql* : expression Transact-SQL qui correspond à l’instruction préparée.  
  
*$params* [FACULTATIF] : objet **array** de valeurs qui correspondent aux paramètres d’une requête paramétrable. Chaque élément du tableau peut être l’un des éléments suivants :
  
-   Une valeur littérale  
  
-   Une variable PHP  
  
-   Un objet **array** avec la structure suivante :  
  
    ```  
    array($value [, $direction [, $phpType [, $sqlType]]])  
    ```  
  
    La description de chaque élément du tableau figure dans le tableau suivant :  
  
    |Élément|Description|  
    |-----------|---------------|  
    |*$value*|Valeur littérale, variable PHP ou variable PHP par référence.|  
    |*$direction*[facultatif]|L’une des constantes **SQLSRV_PARAM_\*** utilisées pour indiquer la direction du paramètre : **SQLSRV_PARAM_IN**, **SQLSRV_PARAM_OUT**, **SQLSRV_PARAM_INOUT**. La valeur par défaut est **SQLSRV_PARAM_IN**.<br /><br />Pour plus d’informations sur les constantes PHP, consultez [Constantes &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
    |*$phpType*[facultatif]|Constante **SQLSRV_PHPTYPE_\*** qui spécifie le type de données PHP de la valeur retournée.<br /><br />Pour plus d’informations sur les constantes PHP, consultez [Constantes &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
    |*$sqlType*[facultatif]|Constante **SQLSRV_SQLTYPE_\*** qui spécifie le type de données SQL Server de la valeur d’entrée.<br /><br />Pour plus d’informations sur les constantes PHP, consultez [Constantes &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).|  
  
*$options* [FACULTATIF] : tableau associatif qui définit les propriétés de la requête. Les clés prises en charge sont les suivantes :  
  
|Key|Valeurs prises en charge|Description|  
|-------|--------------------|---------------|  
|QueryTimeout|Valeur d'entier positif.|Définit le délai d’expiration de la requête, en secondes. Par défaut, le pilote attend les résultats indéfiniment.|  
|SendStreamParamsAtExec|**true** ou **false**<br /><br />La valeur par défaut est **true**.|Configure le pilote pour envoyer toutes les données de flux au moment de l’exécution (**true**), ou pour les envoyer par blocs (**false**). La valeur par défaut est **true**. Pour plus d’informations, consultez [sqlsrv_send_stream_data](../../connect/php/sqlsrv-send-stream-data.md).|  
|Défilement|SQLSRV_CURSOR_FORWARD<br /><br />SQLSRV_CURSOR_STATIC<br /><br />SQLSRV_CURSOR_DYNAMIC<br /><br />SQLSRV_CURSOR_KEYSET<br /><br />SQLSRV_CURSOR_CLIENT_BUFFERED|Pour plus d’informations sur ces valeurs, consultez [Spécification d’un type de curseur et sélection de lignes](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md).|  
  
## <a name="return-value"></a>Valeur retournée  
Ressource d’instruction. Si l’instruction ne peut pas être créée et/ou exécutée, la valeur **false** est retournée.  
  
## <a name="remarks"></a>Notes   
La fonction **sqlsrv_query** convient bien aux requêtes à usage unique. Elle doit être le choix par défaut pour exécuter des requêtes, sauf en cas de circonstances particulières. Cette fonction fournit une méthode simplifiée pour exécuter une requête avec une quantité minimale de code. La fonction **sqlsrv_query** effectue à la fois la préparation et l’exécution des instructions. Vous pouvez l’utiliser pour exécuter des requêtes paramétrables.  
  
Pour plus d’informations, consultez [How to: Retrieve Output Parameters Using the SQLSRV Driver](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md).  
  
## <a name="example"></a> Exemple  
Dans l’exemple suivant, une seule ligne est insérée dans la table *Sales.SalesOrderDetail* de la base de données AdventureWorks. L’exemple part du principe que SQL Server et la base de données [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) sont installés sur l’ordinateur local.  Toute la sortie est écrite dans la console quand l’exemple est exécuté à partir de la ligne de commande.  
  
> [!NOTE]  
> Bien que l’exemple suivant utilise une instruction INSERT pour illustrer l’utilisation de **sqlsrv_query** pour exécuter une seule instruction, le concept s’applique à n’importe quelle instruction Transact-SQL.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array("Database"=>"AdventureWorks");  
$conn = sqlsrv_connect($serverName, $connectionInfo);  
if ($conn === false) {  
    echo "Could not connect.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Set up the parameterized query. */  
$tsql = "INSERT INTO Sales.SalesOrderDetail   
        (SalesOrderID,   
         OrderQty,   
         ProductID,   
         SpecialOfferID,   
         UnitPrice,   
         UnitPriceDiscount)  
        VALUES   
        (?, ?, ?, ?, ?, ?)";  
  
/* Set parameter values. */  
$params = array(75123, 5, 741, 1, 818.70, 0.00);  
  
/* Prepare and execute the query. */  
$stmt = sqlsrv_query($conn, $tsql, $params);  
if ($stmt) {  
    echo "Row successfully inserted.\n";  
} else {  
    echo "Row insertion failed.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt($stmt);  
sqlsrv_close($conn);  
?>  
```  
  
## <a name="example"></a> Exemple  
L’exemple suivant met à jour un champ dans la table *Sales.SalesOrderDetail* de la base de données AdventureWorks. L’exemple part du principe que SQL Server et la base de données [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) sont installés sur l’ordinateur local.  Toute la sortie est écrite dans la console quand l’exemple est exécuté à partir de la ligne de commande.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array("Database"=>"AdventureWorks");  
$conn = sqlsrv_connect($serverName, $connectionInfo);  
if ($conn === false) {  
    echo "Could not connect.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Set up the parameterized query. */  
$tsql = "UPDATE Sales.SalesOrderDetail   
         SET OrderQty = (?)   
         WHERE SalesOrderDetailID = (?)";  
  
/* Assign literal parameter values. */  
$params = array(5, 10);  
  
/* Execute the query. */  
if (sqlsrv_query($conn, $tsql, $params)) {  
    echo "Statement executed.\n";  
} else {  
    echo "Error in statement execution.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Free connection resources. */  
sqlsrv_close($conn);  
?>  
```  
  
> [!NOTE]
> Il est recommandé d’utiliser des chaînes en tant qu’entrées lors de la liaison des valeurs à un [colonne decimal ou numeric](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql) pour vérifier la précision et l’exactitude que PHP est limitée à la précision pour [nombres à virgule flottante](http://php.net/manual/en/language.types.float.php). Va de même pour des colonnes bigint, en particulier lorsque les valeurs sont en dehors de la plage d’un [entier](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md).

## <a name="example"></a> Exemple  
Cet exemple de code montre comment lier une valeur décimale en tant que paramètre d’entrée.  

```
<?php
$serverName = "(local)";
$connectionInfo = array("Database"=>"YourTestDB");  
$conn = sqlsrv_connect($serverName, $connectionInfo);  
if ($conn === false) {  
     echo "Could not connect.\n";  
     die(print_r(sqlsrv_errors(), true));  
}  

// Assume TestTable exists with a decimal field 
$input = "9223372036854.80000";
$params = array($input);
$stmt = sqlsrv_query($conn, "INSERT INTO TestTable (DecimalCol) VALUES (?)", $params);

sqlsrv_free_stmt($stmt);  
sqlsrv_close($conn);  

?>
```


## <a name="see-also"></a> Voir aussi  
[Informations de référence sur l’API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  

[Guide pratique pour exécuter des requêtes paramétrables](../../connect/php/how-to-perform-parameterized-queries.md)  

[À propos des exemples de code dans la documentation](../../connect/php/about-code-examples-in-the-documentation.md)  

[Guide pratique pour envoyer des données sous forme de flux](../../connect/php/how-to-send-data-as-a-stream.md)  

[Utilisation de paramètres directionnels](../../connect/php/using-directional-parameters.md)  

  

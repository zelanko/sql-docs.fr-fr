---
title: PDO::Prepare | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a8b16fdc-c748-49be-acf2-a6ac7432d16b
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7ac27dbcc186eff263803da714032d532c95d3b4
ms.sourcegitcommit: f9d4f9c1815cff1689a68debdccff5e7ff97ccaf
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39367701"
---
# <a name="pdoprepare"></a>PDO::prepare
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Prépare une instruction en vue de son exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
PDOStatement PDO::prepare ( $statement [, array(key_pair)] )  
```  
  
#### <a name="parameters"></a>Paramètres  
$*statement*: chaîne qui contient l’instruction SQL.  
  
*key_pair* : tableau contenant un nom et une valeur d’attribut. Pour plus d'informations, consultez la section Remarques.  
  
## <a name="return-value"></a>Valeur retournée  
En cas de réussite, retourne un objet PDOStatement. En cas d’échec, retourne un objet de PDOException, ou false en fonction de la valeur de PDO::ATTR_ERRMODE.  
  
## <a name="remarks"></a>Notes   
Le [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] n’évalue pas les instructions préparées avant leur exécution.  
  
Le tableau suivant répertorie les valeurs possibles de *key_pair*.  
  
|Key|Description|  
|-------|---------------|  
|PDO::ATTR_CURSOR|Spécifie le comportement du curseur. La valeur par défaut est PDO::CURSOR_FWDONLY. PDO::CURSOR_SCROLL est un curseur statique.<br /><br />Par exemple, `array( PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY )`.<br /><br />Si vous utilisez PDO::CURSOR_SCROLL, vous pouvez utiliser PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE, qui est décrit ci-dessous.<br /><br />Pour plus d’informations sur les jeux de résultats et les curseurs dans le pilote PDO_SQLSRV, consultez [Types de curseurs &#40;pilote PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|  
|PDO::ATTR_EMULATE_PREPARES|Par défaut, cet attribut a la valeur false, qui peut être modifié par ce `PDO::ATTR_EMULATE_PREPARES => true`. Consultez [émuler préparer](#emulate-prepare) pour plus d’informations et d’exemple.|
|PDO::SQLSRV_ATTR_ENCODING|PDO::SQLSRV_ENCODING_UTF8 (par défaut)<br /><br />PDO::SQLSRV_ENCODING_SYSTEM<br /><br />PDO::SQLSRV_ENCODING_BINARY|  
|PDO::SQLSRV_ATTR_DIRECT_QUERY|Si la valeur est True, spécifie l’exécution de requête directe. False est synonyme d’exécution d’instruction préparée. Pour plus d’informations sur PDO::SQLSRV_ATTR_DIRECT_QUERY, consultez [Exécution d’instruction directe et exécution d’instruction préparée dans le pilote PDO_SQLSRV](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|Pour plus d’informations, consultez [PDO::setAttribute](../../connect/php/pdo-setattribute.md).|  
  
Quand vous utilisez PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL, vous pouvez utiliser PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE. Par exemple,  
  
```  
array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL, PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_DYNAMIC));  
```  
  
Le tableau suivant montre les valeurs possibles pour PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE.  
  
|Valeur|Description|  
|---------|---------------|  
|PDO::SQLSRV_CURSOR_BUFFERED|Crée un curseur statique (mis en mémoire tampon) côté client. Pour plus d’informations sur les curseurs côté client, consultez [Types de curseurs &#40;pilote PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_CURSOR_DYNAMIC|Crée un curseur dynamique (sans mise en mémoire tampon) côté serveur, qui vous permet d’accéder aux lignes dans n’importe quel ordre et reflète les modifications dans la base de données.|  
|PDO::SQLSRV_CURSOR_KEYSET_DRIVEN|Crée un curseur de jeu de clés côté serveur. Un curseur de jeu de clés ne met pas à jour le nombre de lignes si une ligne est supprimée de la table (une ligne supprimée est retournée sans valeur).|  
|PDO::SQLSRV_CURSOR_STATIC|Crée un curseur statique côté serveur, qui vous permet d’accéder aux lignes dans n’importe quel ordre mais ne reflète pas les modifications dans la base de données.<br /><br />PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL implique PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_STATIC.|  
  
Vous pouvez fermer un objet PDOStatement en lui affectant la valeur Null.  
  
## <a name="example"></a> Exemple  
Cet exemple montre comment utiliser la méthode PDO::prepare avec des marques et un curseur avant uniquement.  
  
```  
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$col1 = 'a';  
$col2 = 'b';  
  
$query = "insert into Table1(col1, col2) values(?, ?)";  
$stmt = $conn->prepare( $query, array( PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY, PDO::SQLSRV_ATTR_QUERY_TIMEOUT => 1  ) );  
$stmt->execute( array( $col1, $col2 ) );  
print $stmt->rowCount();  
echo "\n";  
  
$query = "insert into Table1(col1, col2) values(:col1, :col2)";  
$stmt = $conn->prepare( $query, array( PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY, PDO::SQLSRV_ATTR_QUERY_TIMEOUT => 1  ) );  
$stmt->execute( array( ':col1' => $col1, ':col2' => $col2 ) );  
print $stmt->rowCount();  
  
$stmt = null  
?>  
```  

## <a name="example"></a> Exemple  
Cet exemple montre comment utiliser la méthode PDO::prepare avec un curseur côté client. Pour obtenir un exemple de curseur côté serveur, consultez [Types de curseurs &#40;pilote PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "select * from Person.ContactType";  
$stmt = $conn->prepare( $query, array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL));  
$stmt->execute();  
  
echo "\n";  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n";  
}  
echo "\n..\n";  
  
$row = $stmt->fetch( PDO::FETCH_BOTH, PDO::FETCH_ORI_FIRST );  
print_r($row);  
  
$row = $stmt->fetch( PDO::FETCH_ASSOC, PDO::FETCH_ORI_REL, 1 );  
print "$row[Name]\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_NEXT );  
print "$row[1]\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_PRIOR );  
print "$row[1]..\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_ABS, 0 );  
print_r($row);  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_LAST );  
print_r($row);  
?>  
```  

<a name="emulate-prepare" />

## <a name="example"></a> Exemple 

Cet exemple montre comment utiliser la méthode PDO::prepare avec `PDO::ATTR_EMULATE_PREPARES` défini sur true. 

```
<?php
$serverName = "yourservername";
$username = "yourusername";
$password = "yourpassword";
$database = "tempdb";
$conn = new PDO("sqlsrv:server = $serverName; Database = $database", $username, $password);

$pdo_options = array();
$pdo_options[PDO::ATTR_EMULATE_PREPARES] = true;
$pdo_options[PDO::SQLSRV_ATTR_ENCODING] = PDO::SQLSRV_ENCODING_UTF8;

$stmt = $conn->prepare("CREATE TABLE TEST([id] [int] IDENTITY(1,1) NOT NULL, 
                                          [name] nvarchar(max))", 
                                          $pdo_options);
$stmt->execute();

$prefix = '가각';
$name = '가각ácasa';
$name2 = '가각sample2';

$stmt = $conn->prepare("INSERT INTO TEST(name) VALUES(:p0)", $pdo_options);
$stmt->execute(['p0' => $name]);
unset($stmt);

$stmt = $conn->prepare("SELECT * FROM TEST WHERE NAME LIKE :p0", $pdo_options);
$stmt->execute(['p0' => "$prefix%"]);
foreach ($stmt as $row) {
    echo "\n" . 'FOUND: ' . $row['name'];
}

unset($stmt);
unset($conn);
?>
```

Le pilote PDO_SQLSRV remplace en interne tous les espaces réservés par les paramètres qui sont liés par [PDOStatement::bindParam()](../../connect/php/pdostatement-bindparam.md). Par conséquent, une chaîne de requête SQL avec aucune des espaces réservés est envoyée au serveur. Prenons l’exemple suivant,

```
$statement = $PDO->prepare("INSERT into Customers (CustomerName, ContactName) VALUES (:cus_name, :con_name)");
$statement->bindParam(:cus_name, "Cardinal");
$statement->bindParam(:con_name, "Tom B. Erichsen");
$statement->execute();
```

Avec `PDO::ATTR_EMULATE_PREPARES` définie sur false (le cas par défaut), les données envoyées à la base de données sont :

```
"INSERT into Customers (CustomerName, ContactName) VALUES (:cus_name, :con_name)"
Information on :cus_name parameter
Information on :con_name parameter
```

Le serveur exécute la requête à l’aide de sa fonctionnalité de requête paramétrable pour la liaison de paramètres. En revanche, avec `PDO::ATTR_EMULATE_PREPARES` défini sur true, la requête envoyée au serveur est essentiellement :

```
"INSERT into Customers (CustomerName, ContactName) VALUES ('Cardinal', 'Tom B. Erichsen')"
```

Paramètre `PDO::ATTR_EMULATE_PREPARES` à true peut contourner certaines restrictions dans SQL Server. Par exemple, SQL Server ne prend pas en charge des paramètres nommés ou positionnels dans certaines clauses Transact-SQL. En outre, SQL Server a une limite de 2 100 paramètres de liaison.

> [!NOTE]
> Avec emulate prépare la valeur est true, la sécurité des requêtes paramétrables n’est pas en vigueur. Par conséquent, votre application doit garantir que les données liées aux paramètres ne contiennent pas de code Transact-SQL malveillant.

### <a name="encoding"></a>Encoding

Si l’utilisateur souhaite lier les paramètres avec des encodages différents (par exemple, UTF-8 ou binaire), utilisateur doit indiquer clairement l’encodage dans le script PHP.

Le pilote PDO_SQLSRV vérifie d’abord l’encodage spécifié dans `PDO::bindParam()` (par exemple, `$statement->bindParam(:cus_name, "Cardinal", PDO::PARAM_STR, 10, PDO::SQLSRV_ENCODING_UTF8)`). 

Si introuvable, le pilote vérifie si n’importe quel encodage est défini `PDO::prepare()` ou `PDOStatement::setAttribute()`. Sinon, le pilote utilise l’encodage spécifié dans `PDO::__construct()` ou `PDO::setAttribute()`.

### <a name="limitations"></a>Limitations

Comme vous pouvez le voir, liaison est effectuée en interne par le pilote. Une requête valide est envoyée au serveur pour l’exécution sans aucun paramètre. Par rapport à Normal, certaines limitations entraînent lorsque la fonctionnalité de requête paramétrable n’est pas en cours d’utilisation.

- Il ne fonctionne pas pour les paramètres qui sont liées en tant que `PDO::PARAM_INPUT_OUTPUT`.
    - Lorsque l’utilisateur spécifie `PDO::PARAM_INPUT_OUTPUT` dans `PDO::bindParam()`, une exception PDO est levée.
- Il ne fonctionne pas pour les paramètres qui sont liées en tant que paramètres de sortie.
    - Lorsque l’utilisateur crée une instruction préparée avec des espaces réservés qui sont destinés aux paramètres de sortie (autrement dit, avoir un signe égal immédiatement après un espace réservé, tels que `SELECT ? = COUNT(*) FROM Table1`), une exception PDO est levée.
    - Lorsqu’une instruction préparée appelle une procédure stockée avec un espace réservé comme argument pour un paramètre de sortie, aucune exception n’est levée, car le pilote ne peut pas détecter le paramètre de sortie. Toutefois, la variable fournies par l’utilisateur pour le paramètre de sortie restera inchangée.
- Des espaces réservés en double pour un paramètre codé en binaire ne fonctionnent pas

## <a name="see-also"></a> Voir aussi  
[Classe PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  

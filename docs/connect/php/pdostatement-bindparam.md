---
title: PDOStatement::bindParam | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 65212058-2632-47a4-ba7d-2206883abf09
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d8186b87e5dde50b07aa69e4dde870d8474265bd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66795584"
---
# <a name="pdostatementbindparam"></a>PDOStatement::bindParam
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Lie un paramètre à un espace réservé nommé ou de point d’interrogation dans l’instruction SQL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
bool PDOStatement::bindParam($parameter, &$variable[, $data_type[, $length[, $driver_options]]]);  
```  
  
#### <a name="parameters"></a>Paramètres  
$*parameter* : identificateur de paramètre (mixte). Pour une instruction qui utilise des espaces réservés nommés, utilisez un nom de paramètre (:name). Pour une instruction préparée qui utilise la syntaxe constituée de points d’interrogation, il s’agit de l’index en base 1 du paramètre.  
  
&$*variable* : nom (mixte) de la variable PHP à lier au paramètre d’instruction SQL.  
  
$*data_type*: constante facultative (entier) PDO::PARAM_*. La valeur par défaut est PDO::PARAM_STR.  
  
$*length* : longueur facultative du type de données (entier). Vous pouvez spécifier PDO::SQLSRV_PARAM_OUT_DEFAULT_SIZE pour indiquer la taille par défaut quand vous utilisez PDO::PARAM_INT ou PDO::PARAM_BOOL dans $*data_type*.  
  
$*driver_options*: les options spécifiques au pilote (mixtes) facultatives. Par exemple, vous pouvez spécifier PDO::SQLSRV_ENCODING_UTF8 pour lier la colonne à une variable en tant que chaîne encodée au format UTF-8.  
  
## <a name="return-value"></a>Valeur retournée  
TRUE en cas de réussite ; sinon, FALSE.  
  
## <a name="remarks"></a>Notes  
Lors de la liaison de données null à des colonnes de serveur de type varbinary, binary ou varbinary(max), vous devez spécifier l’encodage binaire (PDO::SQLSRV_ENCODING_BINARY) à l’aide de $*driver_options*. Pour plus d’informations sur l’encodage des constantes, consultez [Constantes](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).  
  
La prise en charge de PDO a été ajoutée dans la version 2.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  

## <a name="example"></a>Exemple  
Cet exemple de code montre qu’après la liaison de $contact au paramètre, le fait de modifier la valeur change la valeur transmise dans la requête.  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = ?");  
$stmt->bindParam(1, $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
  
$stmt = null;  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = :contact");  
$stmt->bindParam(':contact', $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
?>  
```  
  
## <a name="example"></a>Exemple  
Cet exemple de code montre comment accéder à un paramètre de sortie.  
  
```  
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
$input1 = 'bb';  
  
$stmt = $conn->prepare("select ? = count(*) from Sys.tables");  
$stmt->bindParam(1, $input1, PDO::PARAM_STR, 10);  
$stmt->execute();  
echo $input1;  
?>  
```  
  
> [!NOTE]
> Lors de la liaison d’un paramètre de sortie à un type bigint, si la valeur peut retrouver en dehors de la plage d’un [entier](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md), l’utilisation de PDO::PARAM_INT avec PDO::SQLSRV_PARAM_OUT_DEFAULT_SIZE peut entraîner une exception de « valeur hors limites ». Par conséquent, utilisez à la place de la valeur par défaut PDO::PARAM_STR et indiquent la taille de la chaîne finale résultante, est au maximum de 21. Il est le nombre maximal de chiffres, y compris le signe négatif, de n’importe quelle valeur bigint. 

## <a name="example"></a>Exemple  
Cet exemple de code montre comment utiliser un paramètre d’entrée/sortie.  
  
```  
<?php  
   $database = "AdventureWorks";  
   $server = "(local)";  
   $dbh = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
   $dbh->query("IF OBJECT_ID('dbo.sp_ReverseString', 'P') IS NOT NULL DROP PROCEDURE dbo.sp_ReverseString");  
   $dbh->query("CREATE PROCEDURE dbo.sp_ReverseString @String as VARCHAR(2048) OUTPUT as SELECT @String = REVERSE(@String)");  
   $stmt = $dbh->prepare("EXEC dbo.sp_ReverseString ?");  
   $string = "123456789";  
   $stmt->bindParam(1, $string, PDO::PARAM_STR | PDO::PARAM_INPUT_OUTPUT, 2048);  
   $stmt->execute();  
   print $string;   // Expect 987654321  
?>  
```  

> [!NOTE]
> Il est recommandé d’utiliser des chaînes en entrée pour lier des valeurs à une [colonne décimale ou numérique](../../t-sql/data-types/decimal-and-numeric-transact-sql.md) pour des raisons de précision et d’exactitude, car PHP n’offre qu’une précision limitée pour les [nombres à virgule flottante](https://php.net/manual/en/language.types.float.php). Il en va de même pour les colonnes bigint, en particulier si les valeurs sont en dehors de la plage des [entiers](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md).

## <a name="example"></a>Exemple  
Cet exemple de code montre comment lier une valeur décimale comme paramètre d’entrée.  

```
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  

// Assume TestTable exists with a decimal field 
$input = 9223372036854.80000;
$stmt = $conn->prepare("INSERT INTO TestTable (DecimalCol) VALUES (?)");
// by default it is PDO::PARAM_STR, rounding of a large input value may
// occur if PDO::PARAM_INT is specified
$stmt->bindParam(1, $input, PDO::PARAM_STR);
$stmt->execute();
```


## <a name="see-also"></a>Voir aussi  
[PDOStatement, classe](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  

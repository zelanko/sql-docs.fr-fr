---
title: PDOStatement::bindValue | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 13bc4ece-420e-4887-8809-bf0705ddf126
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e3da628d31f3e127f2e2499f9a4b697cff28d9e6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47790517"
---
# <a name="pdostatementbindvalue"></a>PDOStatement::bindValue
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Lie une valeur à un espace réservé nommé ou constitué de points d’interrogation dans l’instruction SQL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
bool PDOStatement::bindValue($parameter, $value[, $data_type]);  
```  
  
#### <a name="parameters"></a>Paramètres  
$*parameter* : identificateur de paramètre (mixte). Pour une instruction qui utilise des espaces réservés nommés, utilisez un nom de paramètre (:name). Pour une instruction préparée qui utilise la syntaxe constituée de points d’interrogation, il s’agit de l’index en base 1 du paramètre.
  
$*value* : valeur (mixte) à lier au paramètre.  
  
$*data_type* : type de données (entier) facultatif représenté par une constante PDO::PARAM_*. La valeur par défaut est PDO::PARAM_STR.  
  
## <a name="return-value"></a>Valeur retournée  
TRUE en cas de réussite ; sinon, FALSE.  
  
## <a name="remarks"></a>Notes   
  
La prise en charge de PDO a été ajoutée dans la version 2.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a> Exemple  
Cet exemple montre qu’une fois que la valeur de $contact est liée, sa modification ne change pas la valeur transmise dans la requête.  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = ?");  
$stmt->bindValue(1, $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
  
$stmt = null;  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = :contact");  
$stmt->bindValue(':contact', $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
?>  
```

> [!NOTE]
> Il est recommandé d’utiliser des chaînes en tant qu’entrées lors de la liaison des valeurs à un [colonne decimal ou numeric](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql) pour vérifier la précision et l’exactitude que PHP est limitée à la précision pour [nombres à virgule flottante](http://php.net/manual/en/language.types.float.php). Va de même pour des colonnes bigint, en particulier lorsque les valeurs sont en dehors de la plage d’un [entier](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md).

## <a name="example"></a> Exemple  
Cet exemple de code montre comment lier une valeur décimale en tant que paramètre d’entrée.  

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
$stmt->bindValue(1, $input, PDO::PARAM_STR);
$stmt->execute();
```
  
## <a name="see-also"></a> Voir aussi  
[PDOStatement, classe](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  

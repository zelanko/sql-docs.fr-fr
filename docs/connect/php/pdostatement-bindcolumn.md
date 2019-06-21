---
title: PDOStatement::bindColumn | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: bbdcea53-d23d-4769-89a0-95c7cf4d5390
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: de72eb899274502e6a99e160e4911b5e4bf275b8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66761962"
---
# <a name="pdostatementbindcolumn"></a>PDOStatement::bindColumn
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Lie une variable à une colonne dans un jeu de résultats.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
bool PDOStatement::bindColumn($column, &$param[, $type[, $maxLen[, $driverdata ]]] );  
```  
  
#### <a name="parameters"></a>Paramètres  
$*column* : numéro (mixte) de la colonne (index de base 1) ou nom de la colonne dans le jeu de résultats.  
  
&$*param* : nom (mixte) de la variable PHP à laquelle la colonne va être liée.  
  
$*type* : type de données facultatif du paramètre, représenté par une constante PDO::PARAM_* constant.  
  
$*maxLen*: entier facultatif, non utilisé par les pilotes Microsoft SQL Server pour PHP.  
  
$*driverdata* : paramètres mixte(s) facultatif(s) du pilote. Par exemple, vous pouvez spécifier PDO::SQLSRV_ENCODING_UTF8 pour lier la colonne à une variable en tant que chaîne encodée au format UTF-8.  
  
## <a name="return-value"></a>Valeur retournée  
TRUE en cas de réussite ; sinon, FALSE.  
  
## <a name="remarks"></a>Notes  
La prise en charge de PDO a été ajoutée dans la version 2.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Exemple  
Cet exemple montre comment une variable peut être liée à une colonne dans un jeu de résultats.  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "SELECT Title, FirstName, EmailAddress FROM Person.Contact where LastName = 'Estes'";  
$stmt = $conn->prepare($query);  
$stmt->execute();  
  
$stmt->bindColumn('EmailAddress', $email);  
while ( $row = $stmt->fetch( PDO::FETCH_BOUND ) ){  
   echo "$email\n";  
}  
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[PDOStatement, classe](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  

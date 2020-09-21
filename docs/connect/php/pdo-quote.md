---
title: PDO::quote
description: Référence API pour la fonction PDO::quote dans le Pilote Microsoft PDO_SQLSRV pour PHP pour SQL Server.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ab9ddc48-42f8-4edf-aa8b-b0fc66706161
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2cc39e175c46317428836af6562abc9af3d02dd9
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88645541"
---
# <a name="pdoquote"></a>PDO::quote
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Traite une chaîne à utiliser dans une requête en plaçant des guillemets autour de la chaîne d’entrée comme l’exige la base de données SQL Server sous-jacente. PDO::quote échappe les caractères spéciaux dans la chaîne d’entrée à l’aide d’un style approprié à SQL Server.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
string PDO::quote( $string[, $parameter_type ] )  
```  
  
#### <a name="parameters"></a>Paramètres  
$*string* : chaîne à placer entre guillemets.  
  
$*parameter_type* : symbole (entier) facultatif indiquant le type de données.  La valeur par défaut est PDO::PARAM_STR.  

De nouvelles constantes PDO ont été introduites dans PHP 7.2 pour prendre en charge la [liaison des chaînes Unicode et non-Unicode](https://wiki.php.net/rfc/extended-string-types-for-pdo). Les chaînes Unicode peuvent être placées entre guillemets avec N comme préfixe (par exemple, N'string' au lieu de 'string').

1. PDO::PARAM_STR_NATL - nouveau type de chaînes Unicode à appliquer comme opérateur au niveau du bit - ou à PDO::PARAM_STR
1. PDO::PARAM_STR_CHAR - nouveau type de chaînes non-Unicode à appliquer comme opérateur au niveau du bit - OU à PDO::PARAM_STR
1. PDO::ATTR_DEFAULT_STR_PARAM - définir sur PDO::PARAM_STR_NATL ou PDO::PARAM_STR_CHAR pour indiquer une valeur au niveau du bit OU à PDO::PARAM_STR par défaut

À partir de la version 5.8.0, vous pouvez utiliser ces constantes avec PDO::quote.
  
## <a name="return-value"></a>Valeur de retour  
Chaîne entre guillemets qui peut être passée à une instruction SQL, ou false en cas d’échec.  
  
## <a name="remarks"></a>Notes  
La prise en charge de PDO a été ajoutée dans la version 2.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Exemple  
  
```  
<?php  
$database = "test";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$param = 'a \' g';  
$param2 = $conn->quote( $param );  
  
$query = "INSERT INTO Table1 VALUES( ?, '1' )";  
$stmt = $conn->prepare( $query );  
$stmt->execute(array($param));  
  
$query = "INSERT INTO Table1 VALUES( ?, ? )";  
$stmt = $conn->prepare( $query );  
$stmt->execute(array($param, $param2));  
?>  
```  
  
## <a name="example"></a> Exemple  

Le script suivant montre quelques exemples de la façon dont les types de chaînes étendus affectent PDO::quote() avec PHP 7.2 +.

```
<?php
$database = "test";
$server = "(local)";
$db = new PDO("sqlsrv:server=$server; Database=$database", "", "");

$db->quote('über', PDO::PARAM_STR | PDO::PARAM_STR_NATL); // N'über'
$db->quote('foo'); // 'foo'

$db->setAttribute(PDO::ATTR_DEFAULT_STR_PARAM, PDO::PARAM_STR_NATL);
$db->quote('über'); // N'über'
$db->quote('foo', PDO::PARAM_STR | PDO::PARAM_STR_CHAR); // 'foo'
?>
```
  
## <a name="see-also"></a>Voir aussi  
[PDO, classe](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  

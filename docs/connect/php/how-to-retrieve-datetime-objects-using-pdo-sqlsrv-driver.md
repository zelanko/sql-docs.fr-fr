---
title: 'Procédure : récupérer des types date et heure sous forme d’objets DateHeure PHP à l’aide du pilote PDO_SQLSRV | Microsoft Docs'
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- date and time types, retrieving as datetime objects
author: yitam
ms.author: v-yitam
manager: mbarwin
ms.openlocfilehash: 54e5b5c9c1ba59ed64db740fbbb1a643e7cb1b2c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63210437"
---
# <a name="how-to-retrieve-date-and-time-types-as-php-datetime-objects-using-the-pdosqlsrv-driver"></a>Procédure : récupérer des types date et heure sous forme d’objets DateHeure PHP à l’aide du pilote PDO_SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cette fonctionnalité, ajoutée dans la version 5.6.0, est uniquement valide lorsque vous utilisez le pilote PDO_SQLSRV pour le [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].

### <a name="to-retrieve-date-and-time-types-as-datetime-objects"></a>Pour récupérer des types de date et heure en tant qu’objets DateTime

Lorsque vous utilisez PDO_SQLSRV, les types de date et d’heure (**smalldatetime**, **datetime**, **date**, **temps**, **datetime2**, et **datetimeoffset**) sont par défaut retournée sous forme de chaînes. Ni le PDO::ATTR_STRINGIFY_FETCHES ni l’attribut PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE a aucun effet. Afin de récupérer des types de date et heure en tant que [PHP DateTime](http://php.net/manual/en/class.datetime.php) objets, définissez l’attribut de connexion ou une instruction `PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE` à **true** (il s’agit **false** par défaut).

> [!NOTE]
> Cette connexion ou un attribut d’instruction s’applique uniquement à l’extraction régulière des types de date et d’heure, car les objets DateTime ne peut pas être spécifiés en tant que paramètres de sortie.

## <a name="example---use-the-connection-attribute"></a>Exemple : utiliser l’attribut de connexion
Les exemples suivants omettent la vérification des erreurs pour plus de clarté. Celui-ci montre comment définir l’attribut de connexion :

```php
<?php
$server = 'myserver';
$databaseName = 'mydatabase';
$username = 'myusername';
$passwd = 'mypasword';
$tableName = 'mytable';

$conn = new PDO("sqlsrv:Server = $server; Database = $databaseName", $username, $passwd);

// To set the connection attribute
$conn->setAttribute(PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE, true);
$query = "SELECT DateTimeCol FROM $tableName";
$stmt = $conn->prepare($query);
$stmt->execute();

// Expect a DateTimeCol value as a PHP DateTime type
$row = $stmt->fetch(PDO::FETCH_ASSOC);
var_dump($row);

unset($stmt);
unset($conn);
?>
```

## <a name="example---use-the-statement-attribute"></a>Exemple : utiliser l’attribut d’instruction
Cet exemple montre comment définir l’attribut d’instruction :

```php
<?php
$database = "test";
$server = "(local)";
$conn = new PDO("sqlsrv:server = $server; Database = $database", "", "");
$query = "SELECT DateTimeCol FROM myTable";
$stmt = $conn->prepare($query);
$stmt->setAttribute(PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE, true);
$stmt->execute();

// Expect a DateTimeCol value as a PHP DateTime type
$row = $stmt->fetch(PDO::FETCH_NUM);
var_dump($row);

unset($stmt);
unset($conn);
?>
```

## <a name="example---use-the-statement-option"></a>Exemple : utiliser l’option d’instruction
Vous pouvez également définir l’attribut d’instruction en tant qu’option :

```php
<?php
$database = "test";
$server = "(local)";
$conn = new PDO("sqlsrv:server = $server; Database = $database", "", "");

$dateObj = null;
$query = "SELECT DateTimeCol FROM aTable";
$options = array(PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE => true);
$stmt = $conn->prepare($query, $options);
$stmt->execute();
$stmt->bindColumn(1, $dateObj, PDO::PARAM_LOB);
$row = $stmt->fetch(PDO::FETCH_BOUND);
var_dump($dateObj);

unset($stmt);
unset($conn);
?>
```

## <a name="example---retrieve-datetime-types-as-strings"></a>Exemple : récupérer des types de date/heure sous forme de chaînes
L’exemple suivant montre comment obtenir l’inverse (qui n’est pas vraiment nécessaire, car il a la valeur false par défaut) :

```php
<?php
$database = "MyData";
$conn = new PDO("sqlsrv:server = (local); Database = $database");

$dateStr = null;
$query = 'SELECT DateTimeCol FROM table1';
$options = array(PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE => false);
$stmt = $conn->prepare($query, $options);
$stmt->execute();
$stmt->bindColumn(1, $dateStr);
$row = $stmt->fetch(PDO::FETCH_BOUND);
echo $dateStr . PHP_EOL;

unset($stmt);
unset($conn);
?>
```

## <a name="see-also"></a>Voir aussi
[Récupération de données](../../connect/php/retrieving-data.md)

[Récupérer des types date et heure sous forme de chaînes à l’aide du pilote SQLSRV](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md)
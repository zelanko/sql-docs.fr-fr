---
title: Mise en forme des chaînes décimales et valeurs monétaires (pilote PDO_SQLSRV) | Microsoft Docs
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- formatting, decimal types, money values
author: yitam
ms.author: v-yitam
manager: v-mabarw
ms.openlocfilehash: 76c314159faf15e63bf77b17a8a45abf217b205c
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265152"
---
# <a name="formatting-decimal-strings-and-money-values-pdosqlsrv-driver"></a>Mise en forme des chaînes décimales et valeurs monétaires (pilote PDO_SQLSR)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Pour préserver la précision, les [types Decimal ou numeric](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql) sont toujours récupérés sous forme de chaînes avec des précisions et des échelles exactes. Si une valeur est inférieure à 1, le zéro non significatif est manquant. Il est identique aux champs Money et smallmoney, car il s’agit de champs décimaux avec une échelle fixe égale à 4.

## <a name="add-leading-zeroes-if-missing"></a>Ajouter des zéros non significatifs s’ils sont manquants
À partir de la version 5.6.0, l’attribut `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` de connexion ou d’instruction permet à l’utilisateur de mettre en forme des chaînes décimales. Cet attribut attend une valeur booléenne (true ou false) et affecte uniquement la mise en forme des valeurs décimales ou numériques dans les résultats récupérés. En d’autres termes, cet attribut n’a aucun effet sur d’autres opérations telles que l’insertion ou la mise à jour.

Par défaut, `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` est défini sur **false**. Si la valeur est true, les zéros non significatifs pour les chaînes décimales sont ajoutés pour toute valeur décimale inférieure à 1.

## <a name="configure-number-of-decimal-places"></a>Configurer le nombre de décimales
Lorsqu’il est `PDO::SQLSRV_ATTR_DECIMAL_PLACES` activé,unautreattributdeconnexionoud’instruction,,permetauxutilisateursdeconfigurerlenombrededécimaleslorsdel’affichagedesdonnées`PDO::SQLSRV_ATTR_FORMAT_DECIMALS` Money et smallmoney. Il accepte les valeurs entières dans la plage [0, 4], et l’arrondi peut se produire lorsqu’il est affiché. Toutefois, les données monétaires sous-jacentes restent les mêmes.

Les attributs d’instruction remplacent toujours les paramètres de connexion correspondants. Notez que l' `PDO::SQLSRV_ATTR_DECIMAL_PLACES` option affecte **uniquement** les données Money et `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` doit avoir la valeur true. Dans le cas contraire, la mise en forme `PDO::SQLSRV_ATTR_DECIMAL_PLACES` est désactivée, quel que soit le paramètre.

> [!NOTE]
> Dans la mesure où les champs Money ou smallmoney ont `PDO::SQLSRV_ATTR_DECIMAL_PLACES` l’échelle 4, la définition de n’importe quel nombre négatif ou toute valeur supérieure à 4 est ignorée. Il n’est pas recommandé d’utiliser des données monétaires mises en forme comme entrées pour un calcul.

### <a name="to-set-the-connection-attributes"></a>Pour définir les attributs de connexion

-   Définissez les attributs au point de connexion:

    ```php
    $attrs = array(PDO::SQLSRV_ATTR_FORMAT_DECIMALS => true,
                   PDO::SQLSRV_ATTR_DECIMAL_PLACES => 2);

    $conn = new PDO("sqlsrv:Server = myServer; Database = myDB", $username, $password, $attrs);
    ```

-   Définir les attributs après la connexion:

    ```php
    $conn = new PDO("sqlsrv:Server = myServer; Database = myDB", $username, $password);
    $conn->setAttribute(PDO::SQLSRV_ATTR_FORMAT_DECIMALS, true);
    $conn->setAttribute(PDO::SQLSRV_ATTR_DECIMAL_PLACES, 2);
    ```

## <a name="example---format-money-data"></a>Exemple: mettre en forme les données Money
L’exemple suivant montre comment extraire des données Money à l’aide de [PDOStatement:: bindColumn](../../connect/php/pdostatement-bindcolumn.md):

```php
<?php
$database = "myDB";
$server = "(local)";
$conn = new PDO( "sqlsrv:server=$server; Database = $database", "", "");
$conn->setAttribute(PDO::SQLSRV_ATTR_FORMAT_DECIMALS, true);

$numDigits = 3;
$query = "SELECT smallmoney1 FROM aTable";
$options = array(PDO::SQLSRV_ATTR_DECIMAL_PLACES => $numDigits);
$stmt = $conn->prepare($query, $options);
$stmt->execute();

$stmt->bindColumn('smallmoney1', $field);
$result = $stmt->fetch(PDO::FETCH_BOUND);
echo $field;    // expect a number string with 3 decimal places

unset($stmt);
unset($conn);
?>
```

## <a name="example---override-connection-attributes"></a>Exemple: remplacer les attributs de connexion
L’exemple suivant montre comment remplacer les attributs de connexion:

```php
<?php
$database = 'myDatabase';
$server = 'myServer';
$username = 'myuser';
$password = 'mypassword'

$conn = new PDO("sqlsrv:server=$server; Database = $database", $username, $password);
$conn->setAttribute(PDO::SQLSRV_ATTR_FORMAT_DECIMALS, true);
$conn->setAttribute(PDO::SQLSRV_ATTR_DECIMAL_PLACES, 2);

$query = 'SELECT smallmoney1 FROM testTable1';
$options = array(PDO::SQLSRV_ATTR_FORMAT_DECIMALS => false);
$stmt = $conn->prepare($query, $options);
$stmt->execute();

$stmt->bindColumn('smallmoney1', $field);
$result = $stmt->fetch(PDO::FETCH_BOUND);  
echo $field;   // expect a number string showing the original scale -- 4 decimal places

unset($stmt);
unset($conn);
?>
```

## <a name="see-also"></a>Voir aussi
[Mise en forme des chaînes décimales et valeurs monétaires (pilote SQLSRV)](../../connect/php/formatting-decimals-sqlsrv-driver.md)

[Récupération de données](../../connect/php/retrieving-data.md)

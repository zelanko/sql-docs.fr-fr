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
manager: mbarwin
ms.openlocfilehash: 35626c192c3d74ad0201cee3c5e97adbce92a3aa
ms.sourcegitcommit: c1105ce638078d2c941cd656b34f78486e6b2d89
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56676530"
---
# <a name="formatting-decimal-strings-and-money-values-pdosqlsrv-driver"></a>Mise en forme des chaînes décimales et valeurs monétaires (pilote PDO_SQLSR)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Pour conserver l’exactitude, [types décimales ou numériques](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql) sont toujours extraites sous forme de chaînes avec les précisions exactes et les échelles. Si n’importe quelle valeur est inférieure à 1, le zéro non significatif est manquant. Il est le même avec des champs money et smallmoney tels qu’ils sont des champs décimaux avec une échelle fixe égale à 4.

## <a name="add-leading-zeroes-if-missing"></a>Ajouter des zéros non significatifs si manquant
À partir de la version 5.6.0, la connexion ou l’attribut d’instruction `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` permet à l’utilisateur à mettre les chaînes décimales. Cet attribut attend une valeur booléenne (true ou false) et affecte uniquement la mise en forme des valeurs décimales ou numériques dans les résultats d’extraction. En d’autres termes, cet attribut n’a aucun effet sur les autres opérations telles que l’insertion ou la mise à jour.

Par défaut, `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` est défini sur **false**. Si la valeur true, les zéros non significatifs pour les chaînes décimales doivent être ajoutée pour n’importe quelle valeur décimale inférieure à 1.

## <a name="configure-number-of-decimal-places"></a>Configurer le nombre de décimales
Avec `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` sous tension, un autre attribut de connexion ou une instruction, `PDO::SQLSRV_ATTR_DECIMAL_PLACES`, permet aux utilisateurs de configurer le nombre de décimales lors de l’affichage de données money et smallmoney. Il accepte les valeurs d’entier dans la plage [0, 4], et arrondi peut se produire lors de son affichage. Toutefois, les données money sous-jacentes restent les mêmes.

Les attributs d’instruction remplacent toujours les paramètres de connexion correspondante. Notez que le `PDO::SQLSRV_ATTR_DECIMAL_PLACES` option **uniquement** affecte les données de l’argent, et `PDO::SQLSRV_ATTR_FORMAT_DECIMALS` doit être définie sur true. Sinon, la mise en forme est désactivée, indépendamment du `PDO::SQLSRV_ATTR_DECIMAL_PLACES` paramètre.

> [!NOTE]
> Étant donné que les champs money ou smallmoney échelle 4, paramètre `PDO::SQLSRV_ATTR_DECIMAL_PLACES` à n’importe quel nombre négatif ou n’importe quelle valeur supérieure à 4 vont être ignorés. Il n’est pas recommandé d’utiliser toutes les données money mis en forme en tant qu’entrées pour le calcul de votre choix.

### <a name="to-set-the-connection-attributes"></a>Pour définir les attributs de connexion

-   Définir des attributs au moment de la connexion :

    ```php
    $attrs = array(PDO::SQLSRV_ATTR_FORMAT_DECIMALS => true,
                   PDO::SQLSRV_ATTR_DECIMAL_PLACES => 2);

    $conn = new PDO("sqlsrv:Server = myServer; Database = myDB", $username, $password, $attrs);
    ```

-   Définir les attributs connexion post :

    ```php
    $conn = new PDO("sqlsrv:Server = myServer; Database = myDB", $username, $password);
    $conn->setAttribute(PDO::SQLSRV_ATTR_FORMAT_DECIMALS, true);
    $conn->setAttribute(PDO::SQLSRV_ATTR_DECIMAL_PLACES, 2);
    ```

## <a name="example---format-money-data"></a>Exemple : des données au format money
L’exemple suivant montre comment extraire des données de l’argent à l’aide [PDOStatement::bindColumn](../../connect/php/pdostatement-bindcolumn.md):

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

## <a name="example---override-connection-attributes"></a>Exemple : les attributs de connexion de remplacement
L’exemple suivant montre comment substituer les attributs de connexion :

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

## <a name="see-also"></a> Voir aussi
[Mise en forme des chaînes décimales et valeurs monétaires (pilote SQLSRV)](../../connect/php/formatting-decimals-sqlsrv-driver.md)

[Récupération de données](../../connect/php/retrieving-data.md)

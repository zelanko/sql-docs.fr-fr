---
title: Mise en forme des chaînes décimales et valeurs monétaires (pilote SQLSRV) | Microsoft Docs
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
ms.openlocfilehash: 76b6d27acedcfe2ec462a764559237a1a2218f78
ms.sourcegitcommit: c1105ce638078d2c941cd656b34f78486e6b2d89
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56676524"
---
# <a name="formatting-decimal-strings-and-money-values-sqlsrv-driver"></a>Mise en forme des chaînes décimales et valeurs monétaires (pilote SQLSRV)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Pour conserver l’exactitude, [types décimales ou numériques](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql) sont toujours extraites sous forme de chaînes avec les précisions exactes et les échelles. Si n’importe quelle valeur est inférieure à 1, le zéro non significatif est manquant. Il est le même avec des champs money et smallmoney tels qu’ils sont des champs décimaux avec une échelle fixe égale à 4.

## <a name="add-leading-zeroes-if-missing"></a>Ajouter des zéros non significatifs si manquant
Depuis la version 5.6.0, l’option `FormatDecimals` est ajouté aux niveaux de connexion et d’instruction sqlsrv, ce qui permet à l’utilisateur à mettre les chaînes décimales. Cette option attend une valeur booléenne (true ou false) et affecte uniquement la mise en forme de valeurs décimales ou numériques dans les résultats d’extraction. En d’autres termes, la `FormatDecimals` option n’a aucun effet sur les autres opérations telles que l’insertion ou la mise à jour.

Par défaut, `FormatDecimals` est défini sur **false**. Si la valeur true, les zéros non significatifs pour les chaînes décimales doivent être ajoutée pour n’importe quelle valeur décimale inférieure à 1.

## <a name="configure-number-of-decimal-places"></a>Configurer le nombre de décimales
Avec `FormatDecimals` sous tension, une autre option, `DecimalPlaces`, permet aux utilisateurs de configurer le nombre de décimales lors de l’affichage de données money et smallmoney. Il accepte les valeurs d’entier dans la plage [0, 4], et arrondi peut se produire lors de son affichage. Toutefois, les données money sous-jacentes restent les mêmes.

Les deux options peuvent être définies au niveau de l’instruction ou de connexion, et toujours l’instruction remplace le paramètre de connexion correspondante. Notez que le `DecimalPlaces` option **uniquement** affecte les données de l’argent, et `FormatDecimals` doit être définie sur true pour `DecimalPlaces` entrent en vigueur. Sinon, la mise en forme est désactivée, indépendamment du `DecimalPlaces` paramètre.

> [!NOTE]
> Étant donné que les champs money ou smallmoney échelle 4, paramètre `DecimalPlaces` valeur à n’importe quel nombre négatif ou n’importe quelle valeur supérieure à 4 vont être ignorés. Il n’est pas recommandé d’utiliser toutes les données money mis en forme en tant qu’entrées pour le calcul de votre choix.

## <a name="example---a-simple-fetch"></a>Exemple : une extraction simple
L’exemple suivant montre comment utiliser les nouvelles options dans une extraction simple.

```php
<?php
$username = 'myusername';
$password = 'mypasword';
$tableName = 'mytable';

$connectionInfo = array("UID" => $username, "PWD" => $password, "Database" => "myDB", "FormatDecimals" => true);  
$server = "myServer";  // IP address also works
$conn = sqlsrv_connect( $server, $connectionInfo);  

$numDigits = 2;
$query = "SELECT money1 FROM $tableName";
$options = array("DecimalPlaces" => $numDigits);
$stmt = sqlsrv_prepare($conn, $query, array(), $options);
sqlsrv_execute($stmt);

if (sqlsrv_fetch($stmt)) {
    $field = sqlsrv_get_field($stmt, 0);  
    echo $field;   // expect a numeric value string with 2 decimal places
}

sqlsrv_free_stmt($stmt);
sqlsrv_close($conn);
?>
```

## <a name="example---format-the-output-parameter"></a>Exemple - format, le paramètre de sortie
Si un champ décimal ou numérique est retourné en tant que le [paramètre de sortie](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md), la valeur retournée sera considérée comme une chaîne varchar régulière. Toutefois, si SQLSRV_SQLTYPE_DECIMAL ou SQLSRV_SQLTYPE_NUMERIC est spécifié, vous pouvez définir `FormatDecimals` comme « true » afin de garantir ne zéro pour la valeur de chaîne numérique est manquant. Pour plus d’informations, veuillez lire [Procédure : récupérer des paramètres de sortie à l’aide du pilote SQLSRV](../..//connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md).

L’exemple suivant montre comment mettre en forme le paramètre de sortie d’une procédure stockée qui retourne une valeur decimal(8,4).

```php
$outString = '';
$outSql = '{CALL myStoredProc(?)}';
$stmt = sqlsrv_prepare($conn, 
                       $outSql, 
                       array(array(&$outString, SQLSRV_PARAM_OUT, null, SQLSRV_SQLTYPE_DECIMAL(8, 4))),
                       array('FormatDecimals' => true));

if (sqlsrv_execute($stmt)) {
    echo $outString;  // expect a numeric value string with no missing leading zero
}
```

## <a name="see-also"></a> Voir aussi
[Mise en forme des chaînes décimales et valeurs monétaires (pilote PDO_SQLSRV)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md)

[Récupération de données](../../connect/php/retrieving-data.md)

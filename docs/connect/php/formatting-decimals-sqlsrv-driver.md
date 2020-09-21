---
title: Mise en forme des chaînes décimales et valeurs monétaires (pilote SQLSRV)
description: Découvrez comment utiliser les options FormatDecimals et DecimalPlaces pour mettre en forme les valeurs décimales ou monétaires lors de l’utilisation du pilote Microsoft SQLSRV pour PHP pour SQL Server.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- formatting, decimal types, money values
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c6d77fb9fcfdc720c4053688f8f0dcf759af15c8
ms.sourcegitcommit: d1051f05a7db81ec62d9785bb6af572408f3d4e0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88680724"
---
# <a name="formatting-decimal-strings-and-money-values-sqlsrv-driver"></a>Mise en forme des chaînes décimales et valeurs monétaires (pilote SQLSRV)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Pour préserver la précision, [les types décimaux ou numériques](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql) sont toujours récupérés sous forme de chaînes avec des précisions et des échelles exactes. Si une valeur est inférieure à 1, le zéro non significatif est manquant. C’est identique aux champs money et smallmoney, car il s’agit de champs décimaux avec une échelle fixe égale à 4.

## <a name="add-leading-zeroes-if-missing"></a>Ajouter des zéros non significatifs s’ils sont manquants
À partir de la version 5.6.0, l’option `FormatDecimals` est ajoutée aux niveaux de connexion et d’instruction sqlsrv, ce qui permet à l’utilisateur de mettre en forme des chaînes décimales. Cette option attend une valeur booléenne (true ou false) et affecte uniquement la mise en forme des valeurs décimales ou numériques dans les résultats récupérés. En d’autres termes, l’option `FormatDecimals` n’a aucun effet sur les autres opérations, telles que l’insertion ou la mise à jour.

Par défaut, `FormatDecimals` est défini sur **false**. Si la valeur est true, les zéros non significatifs pour les chaînes décimales sont ajoutés pour toute valeur décimale inférieure à 1.

## <a name="configure-number-of-decimal-places"></a>Configurer le nombre de décimales
Si `FormatDecimals` est activé, une autre option, `DecimalPlaces`, permet aux utilisateurs de configurer le nombre de décimales lors de l’affichage des données money et smallmoney. Il accepte les valeurs entières dans la plage [0, 4], et un arrondi peut se produire lorsqu’il est affiché. Toutefois, les données monétaires sous-jacentes restent les mêmes.

Les deux options peuvent être définies au niveau de la connexion ou de l’instruction, et le paramètre d’instruction remplace toujours le paramètre de connexion correspondant. Notez que l’option `DecimalPlaces` affecte **uniquement** les données money, et que `FormatDecimals` doit avoir la valeur true pour que `DecimalPlaces` s’applique. Dans le cas contraire, la mise en forme est désactivée, quel que soit le paramètre `DecimalPlaces`.

> [!NOTE]
> Étant donné que les champs money ou smallmoney ont l’échelle 4, la définition de la valeur `DecimalPlaces` sur un nombre négatif quelconque ou sur une valeur supérieure à 4 est ignorée. Il n’est pas recommandé d’utiliser des données monétaires mises en forme comme entrées pour un calcul.

## <a name="example---a-simple-fetch"></a>Exemple : extraction simple
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

## <a name="example---format-the-output-parameter"></a>Exemple : mettre en forme le paramètre de sortie
Si un champ décimal ou numérique est renvoyé comme [paramètre de sortie](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md), la valeur renvoyée sera considérée comme une chaîne varchar normale. Toutefois, si SQLSRV_SQLTYPE_DECIMAL ou SQLSRV_SQLTYPE_NUMERIC est spécifié, vous pouvez définir `FormatDecimals` sur true pour vous assurer qu’il n’existe pas de zéro non significatif pour la valeur de chaîne numérique. Pour plus d’informations, veuillez lire [Procédure : récupérer des paramètres de sortie à l’aide du pilote SQLSRV](../..//connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md).

L’exemple suivant montre comment mettre en forme le paramètre de sortie d’une procédure stockée qui renvoie une valeur décimale (8,4).

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

## <a name="see-also"></a>Voir aussi
[Mise en forme des chaînes décimales et valeurs monétaires (pilote PDO_SQLSR)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md)

[Récupération de données](../../connect/php/retrieving-data.md)

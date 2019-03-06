---
title: PDOStatement::setAttribute | Microsoft Docs
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 329d9b5e-1c5d-40b0-9127-1051d0646fc7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3ec2ed7275c3580554c385940c5cef134244ae35
ms.sourcegitcommit: 958cffe9288cfe281280544b763c542ca4025684
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56744339"
---
# <a name="pdostatementsetattribute"></a>PDOStatement::setAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Définit une valeur d’attribut, à savoir un attribut PDO prédéfini ou un attribut de pilote personnalisé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
bool PDOStatement::setAttribute ($attribute, $value );  
```  
  
#### <a name="parameters"></a>Paramètres  
$*attribute* : entier, une des constantes PDO::ATTR_* ou PDO::SQLSRV_ATTR_\*. Consultez la section Notes pour obtenir la liste des attributs disponibles.  
  
$*value* : valeur (mixte) à définir pour le $*attribute* spécifié.  
  
## <a name="return-value"></a>Valeur retournée  
TRUE en cas de réussite, FALSE dans le cas contraire.  
  
## <a name="remarks"></a>Notes   
Le tableau suivant contient la liste des attributs disponibles :  
  
|attribute|Valeurs|Description|  
|-------------|----------|---------------|  
|PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE|De 1 jusqu’à la limite de la mémoire PHP.|Configure la taille de la mémoire tampon qui contient le jeu de résultats pour un curseur côté client.<br /><br />La valeur par défaut est 10 240 Ko (10 Mo).<br /><br />Pour plus d’informations sur les curseurs côté client, consultez [Types de curseurs &#40;pilote PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_DECIMAL_PLACES|Entier compris entre 0 et 4 (inclus)|Spécifie le nombre de décimales lors du formatage extraites des valeurs monétaires.<br /><br />N’importe quel entier négatif ou supérieur à 4 valeur sera ignorée.<br /><br />Cette option fonctionne uniquement lorsque PDO::SQLSRV_ATTR_FORMAT_DECIMALS a la valeur true.<br /><br />Cette option peut également être définie au niveau de la connexion. Dans ce cas, cette option remplace l’option de niveau connexion.<br /><br />Pour plus d’informations, consultez [mise en forme les chaînes décimales et les valeurs de l’argent (pilote PDO_SQLSRV)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md).|
|PDO::SQLSRV_ATTR_ENCODING|Entier<br /><br />PDO::SQLSRV_ENCODING_UTF8 (valeur par défaut)<br /><br />PDO::SQLSRV_ENCODING_SYSTEM<br /><br />PDO::SQLSRV_ENCODING_BINARY|Définit l’encodage de jeu de caractères utilisé par le pilote pour communiquer avec le serveur.|  
|PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE|True ou False|Spécifie s’il faut récupérer des types de date et heure en tant que [PHP DateTime](http://php.net/manual/en/class.datetime.php) objets. Si false, le comportement par défaut consiste à retourner en tant que chaînes.<br /><br />Cette option peut également être définie au niveau de la connexion. Dans ce cas, cette option remplace l’option de niveau connexion.<br /><br />Pour plus d’informations, consultez [Comment : récupérer la Date et l’heure des Types comme PHP à des objets DateTime à l’aide du pilote PDO_SQLSRV](../../connect/php/how-to-retrieve-datetime-objects-using-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE|True ou False|Gère les extractions de numériques à partir de colonnes avec des types numériques SQL (bit, entier, smallint, tinyint, float ou real).<br /><br />Lorsque indicateur d’option de connexion ATTR_STRINGIFY_FETCHES est activé, la valeur de retour est une chaîne, même lorsque SQLSRV_ATTR_FETCHES_NUMERIC_TYPE est activé.<br /><br />Lorsque le type PDO retourné dans la colonne de la liaison est PDO_PARAM_INT, la valeur de retour à partir d’une colonne d’entiers est int, même si SQLSRV_ATTR_FETCHES_NUMERIC_TYPE est désactivé.|  
|PDO::SQLSRV_ATTR_FORMAT_DECIMALS|True ou False|Spécifie s’il faut ajouter des zéros non significatifs pour les chaînes décimales lorsque cela est approprié. Si définie, cette option Active l’option de PDO::SQLSRV_ATTR_DECIMAL_PLACES pour mettre en forme des types de l’argent. Si false, le comportement par défaut de renvoi exacte précision et l’omission des zéros non significatifs pour les valeurs inférieures à 1 est utilisé.<br /><br />Cette option peut également être définie au niveau de la connexion. Dans ce cas, cette option remplace l’option de niveau connexion.<br /><br />Pour plus d’informations, consultez [mise en forme les chaînes décimales et les valeurs de l’argent (pilote PDO_SQLSRV)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md).| 
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|Entier|Définit le délai d’expiration de la requête, en secondes.<br /><br />Par défaut, le pilote attend indéfiniment les résultats. Les nombres négatifs ne sont pas autorisés.<br /><br />0 signifie aucun délai d’attente.|  
  
## <a name="example"></a> Exemple  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "", array('MultipleActiveResultSets'=>false )  );  
  
$stmt = $conn->prepare('SELECT * FROM Person.ContactType');  
  
echo $stmt->getAttribute( constant( "PDO::ATTR_CURSOR" ) );  
  
echo "\n";  
  
$stmt->setAttribute(PDO::SQLSRV_ATTR_QUERY_TIMEOUT, 2);  
echo $stmt->getAttribute( constant( "PDO::SQLSRV_ATTR_QUERY_TIMEOUT" ) );  
?>  
```  
  
## <a name="see-also"></a> Voir aussi  
[PDOStatement, classe](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  

---
title: PDOStatement::setAttribute | Microsoft Docs
ms.custom: ''
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 329d9b5e-1c5d-40b0-9127-1051d0646fc7
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 07bd25dfc7a1acb52be63b846e601c66fb39fd1f
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37991321"
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
|PDO::SQLSRV_ATTR_ENCODING|Entier<br /><br />PDO::SQLSRV_ENCODING_UTF8 (valeur par défaut)<br /><br />PDO::SQLSRV_ENCODING_SYSTEM<br /><br />PDO::SQLSRV_ENCODING_BINARY|Définit l’encodage de jeu de caractères utilisé par le pilote pour communiquer avec le serveur.|  
|PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE|True ou False|Gère les extractions de numériques à partir de colonnes avec des types numériques SQL (bit, entier, smallint, tinyint, float ou real).<br /><br />Lorsque indicateur d’option de connexion ATTR_STRINGIFY_FETCHES est activé, la valeur de retour est une chaîne, même lorsque SQLSRV_ATTR_FETCHES_NUMERIC_TYPE est activé.<br /><br />Lorsque le type PDO retourné dans la colonne de la liaison est PDO_PARAM_INT, la valeur de retour à partir d’une colonne d’entiers est int, même si SQLSRV_ATTR_FETCHES_NUMERIC_TYPE est désactivé.|  
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|Entier|Définit le délai d’attente de la requête, en secondes.<br /><br />Par défaut, le pilote attend indéfiniment les résultats. Les nombres négatifs ne sont pas autorisés.<br /><br />0 signifie aucun délai d’attente.|  
  
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

[PDO](http://php.net/manual/book.pdo.php)  
  

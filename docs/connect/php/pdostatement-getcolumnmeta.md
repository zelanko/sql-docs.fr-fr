---
title: PDOStatement::getColumnMeta | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c92a21cc-8e53-43d0-a4bf-542c77c100c9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 57bc8d1e6112a64f99864ce08f7adb81db6df781
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66799121"
---
# <a name="pdostatementgetcolumnmeta"></a>PDOStatement::getColumnMeta
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Récupère des métadonnées pour une colonne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
array PDOStatement::getColumnMeta ( $column );  
```  
  
#### <a name="parameters"></a>Paramètres  
*$conn* : (entier) numéro en base zéro de la colonne dont vous voulez récupérer les métadonnées.  
  
## <a name="return-value"></a>Valeur retournée  
Tableau associatif (clé et valeur) contenant les métadonnées pour la colonne. Consultez la section Notes pour obtenir une description des champs du tableau.  
  
## <a name="remarks"></a>Notes  
Le tableau suivant décrit les champs du tableau retourné par getColumnMeta.  
  
|NAME|VALUES|  
|--------|----------|  
|native_type|Spécifie le type PHP de la colonne. Toujours une chaîne.|  
|driver:decl_type|Spécifie le type SQL utilisé pour représenter la valeur de la colonne dans la base de données. Si la colonne dans le jeu de résultats est le résultat d’une fonction, cette valeur n’est pas retournée par PDOStatement::getColumnMeta.|  
|flags|Spécifie les indicateurs définis pour cette colonne. Toujours 0.|  
|NAME|Spécifie le nom de la colonne dans la base de données.|  
|table|Spécifie le nom de la table qui contient la colonne dans la base de données. Toujours vide.|  
|len|Spécifie la longueur de la colonne.|  
|precision|Spécifie la précision numérique de cette colonne.|  
|pdo_type|Spécifie le type de cette colonne comme représenté par les constantes PDO::PARAM_*. Toujours PDO::PARAM_STR (2).|  
  
La prise en charge de PDO a été ajoutée dans la version 2.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Exemple  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$stmt = $conn->query("select * from Person.ContactType");  
$metadata = $stmt->getColumnMeta(2);  
var_dump($metadata);  
  
print $metadata['sqlsrv:decl_type'] . "\n";  
print $metadata['native_type'] . "\n";  
print $metadata['name'];  
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[PDOStatement, classe](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  

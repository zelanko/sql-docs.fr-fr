---
title: PDOStatement::closeCursor
description: Référence API pour la fonction PDOStatement::closeCursor dans le Pilote Microsoft PDO_SQLSRV pour PHP pour SQL Server.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8997ab61-e948-4d54-8d32-fc080d55525c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 61ced9d3c4dca42dfe71baaef1a3201fb4f2d260
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88645330"
---
# <a name="pdostatementclosecursor"></a>PDOStatement::closeCursor
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Ferme le curseur, ce qui permet de réexécuter l’instruction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
bool PDOStatement::closeCursor();  
```  
  
## <a name="return-value"></a>Valeur de retour  
true en cas de réussite ; sinon, false.  
  
## <a name="remarks"></a>Notes  
closeCursor a un effet quand l’option de connexion MultipleActiveResultSets a la valeur False.  Pour plus d’informations sur l’option de connexion MultipleActiveResultSets, consultez [Guide pratique pour désactiver MARS (Multiple Active Result Set)](../../connect/php/how-to-disable-multiple-active-resultsets-mars.md).  
  
Au lieu d’appeler closeCursor, vous pouvez simplement affecter la valeur null au handle d’instruction.  
  
La prise en charge de PDO a été ajoutée dans la version 2.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a> Exemple  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "", array('MultipleActiveResultSets' => false ) );  
  
$stmt = $conn->prepare('SELECT * FROM Person.ContactType');  
  
$stmt2 = $conn->prepare('SELECT * FROM HumanResources.Department');  
  
$stmt->execute();  
  
$result = $stmt->fetch();  
print_r($result);  
  
$stmt->closeCursor();  
  
$stmt2->execute();  
$result = $stmt2->fetch();  
print_r($result);  
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[PDOStatement, classe](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  

---
title: PDOStatement::errorCode | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4161abec-c12b-444e-9de5-f1dac7b3e0e4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 78a7486d17d103bec3c8b1ef29d533da2f164c29
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67936077"
---
# <a name="pdostatementerrorcode"></a>PDOStatement::errorCode
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Récupère la valeur SQLSTATE de la dernière opération sur l’objet d’instruction de base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
string PDOStatement::errorCode();  
```  
  
## <a name="return-value"></a>Valeur retournée  
Retourne une valeur SQLSTATE à cinq caractères sous la forme d’une chaîne, ou NULL si aucune opération n’a eu lieu sur le handle d’instruction.  
  
## <a name="remarks"></a>Notes  
La prise en charge de PDO a été ajoutée dans la version 2.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Exemple  
Cet exemple montre une requête SQL qui comporte une erreur.  Le code d’erreur est ensuite indiqué.  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks", "", "");  
$stmt = $conn->prepare('SELECT * FROM Person.Addressx');  
  
$stmt->execute();  
print $stmt->errorCode();  
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[PDOStatement, classe](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  

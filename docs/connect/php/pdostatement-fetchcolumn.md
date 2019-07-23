---
title: PDOStatement::fetchColumn | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6ebf385c-ddb0-4c53-9dc6-7df0d3740b04
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4021a6a5c550ea9674c0bf699462eece1d9c2f9b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67993038"
---
# <a name="pdostatementfetchcolumn"></a>PDOStatement::fetchColumn
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Retourne une colonne d’une ligne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
string PDOStatement::fetchColumn ([ $column_number ] );  
```  
  
#### <a name="parameters"></a>Paramètres  
$*column_number* : entier facultatif indiquant le numéro de colonne de base zéro. La valeur par défaut est 0 (la première colonne de la ligne).  
  
## <a name="return-value"></a>Valeur retournée  
Une colonne ou la valeur false s’il n’y a plus de ligne.  
  
## <a name="remarks"></a>Notes  
La prise en charge de PDO a été ajoutée dans la version 2.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Exemple  
  
```  
<?php  
   $server = "(local)";  
   $database = "AdventureWorks";  
   $conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   while ( $result = $stmt->fetchColumn(1)) {   
      print($result . "\n");   
   }  
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[PDOStatement, classe](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  

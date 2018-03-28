---
title: PDOStatement::errorInfo | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45bebe8-ea4c-49b6-93db-cf1ae65f530c
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 211f10c6d421821d3862f8b58e4a3c92dc471d83
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="pdostatementerrorinfo"></a>PDOStatement::errorInfo
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Récupère les informations d’erreur étendues de la dernière opération effectuée sur le handle d’instruction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
array PDOStatement::errorInfo();  
```  
  
## <a name="return-value"></a>Valeur retournée  
Tableau d’informations d’erreur sur la dernière opération effectuée sur le handle d’instruction. Le tableau comprend les champs suivants :  
  
-   Code d’erreur SQLSTATE  
  
-   Code d’erreur spécifique du pilote  
  
-   Message d’erreur spécifique du pilote  
  
En l’absence d’erreur, ou si la valeur SQLSTATE n’est pas définie, les champs propres au pilote ont la valeur NULL.  
  
## <a name="remarks"></a>Notes  
La prise en charge de PDO a été ajoutée dans la version 2.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Exemple  
Dans cet exemple, l’instruction SQL comporte une erreur, qui est par la suite signalée.  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks", "", "");  
$stmt = $conn->prepare('SELECT * FROM Person.Addressx');  
  
$stmt->execute();  
print_r ($stmt->errorInfo());  
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[PDOStatement, classe](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  

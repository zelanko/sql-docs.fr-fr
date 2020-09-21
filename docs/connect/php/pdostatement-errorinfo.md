---
title: PDOStatement::errorInfo
description: Référence API pour la fonction PDOStatement::errorInfo dans le Pilote Microsoft PDO_SQLSRV pour PHP pour SQL Server.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e45bebe8-ea4c-49b6-93db-cf1ae65f530c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4e05d43caec418257bb107dcb40aa918e406538f
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88645210"
---
# <a name="pdostatementerrorinfo"></a>PDOStatement::errorInfo
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Récupère les informations d’erreur étendues de la dernière opération effectuée sur le handle d’instruction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
array PDOStatement::errorInfo();  
```  
  
## <a name="return-value"></a>Valeur de retour  
Tableau d’informations d’erreur sur la dernière opération effectuée sur le handle d’instruction. Le tableau comprend les champs suivants :  
  
-   Code d’erreur SQLSTATE  
  
-   Code d’erreur spécifique du pilote  
  
-   Message d’erreur spécifique du pilote  
  
En l’absence d’erreur, ou si la valeur SQLSTATE n’est pas définie, les champs propres au pilote ont la valeur NULL.  
  
## <a name="remarks"></a>Notes  
La prise en charge de PDO a été ajoutée dans la version 2.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a> Exemple  
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

[PDO](https://php.net/manual/book.pdo.php)  
  

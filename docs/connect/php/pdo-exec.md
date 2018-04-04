---
title: PDO::exec | Microsoft Docs
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
ms.assetid: 359a87c6-c13a-4518-8f23-a922e7f3b171
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e3708ab788738ea523f2f879efbcac5eb584614e
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="pdoexec"></a>PDO::exec
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Prépare et exécute une instruction SQL dans un appel de fonction unique, en retournant le nombre de lignes affectées par l’instruction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
int PDO::exec ($statement)  
```  
  
#### <a name="parameters"></a>Paramètres  
*$statement*: chaîne qui contient l’instruction SQL à exécuter.  
  
## <a name="return-value"></a>Valeur retournée  
Entier indiquant le nombre de lignes affectées.  
  
## <a name="remarks"></a>Notes  
Si *$statement* contient plusieurs instructions SQL, le nombre de lignes affectées est indiqué pour la dernière instruction uniquement.  
  
PDO::exec ne retourne pas de résultats pour une instruction SELECT.  
  
Les attributs suivants affectent le comportement de PDO::exec :  
  
-   PDO::ATTR_DEFAULT_FETCH_MODE  
  
-   PDO::SQLSRV_ATTR_ENCODING  
  
-   PDO::SQLSRV_ATTR_QUERY_TIMEOUT  
  
Pour plus d’informations, consultez [PDO::setAttribute](../../connect/php/pdo-setattribute.md). 
  
La prise en charge de PDO a été ajoutée dans la version 2.0 de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
## <a name="example"></a>Exemple  
Cet exemple supprime les lignes dans Table1 qui comportent « xxxyy » dans col1. L’exemple indique ensuite le nombre de lignes qui ont été supprimées.  
  
```  
<?php  
   $c = new PDO( "sqlsrv:server=(local)");  
  
   $c->exec("use Test");  
   $ret = $c->exec("delete from Table1 where col1 = 'xxxyy'");  
   echo $ret;  
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[Classe PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  

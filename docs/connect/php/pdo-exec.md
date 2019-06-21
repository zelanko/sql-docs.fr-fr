---
title: PDO::exec | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 359a87c6-c13a-4518-8f23-a922e7f3b171
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 5b6d3341dd3ade106495c606896b6496a9bc2f6c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66762127"
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
  
Les attributs suivants affectent le comportement de PDO::exec :  
  
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

[PDO](https://php.net/manual/book.pdo.php)  
  

---
title: PDO::EXEC | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 359a87c6-c13a-4518-8f23-a922e7f3b171
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ca46ace5ee5e5c0c461687d1e84ef5e0072506e5
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35308188"
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
  
## <a name="return-value"></a>Valeur de retour  
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
  

---
title: Instruction directe - Exécution d’instruction préparée dans le pilote PDO_SQLSRV | Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 05544ca6-1e07-486c-bf03-e8c2c25b3024
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fa9e544fb7b79009d86a5742946a722d5adc18f2
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67993622"
---
# <a name="direct-statement-execution-and-prepared-statement-execution-in-the-pdo_sqlsrv-driver"></a>Exécution d’instruction directe et exécution d’instruction préparée dans le pilote PDO_SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cette rubrique décrit l’utilisation de l’attribut PDO::SQLSRV_ATTR_DIRECT_QUERY pour spécifier l’exécution d’une instruction directe plutôt que le comportement par défaut, qui est l’exécution d’une instruction préparée. L’utilisation d’une instruction préparée peut entraîner de meilleures performances si l’instruction est exécutée plusieurs fois à l’aide d’une liaison de paramètre.  
  
## <a name="remarks"></a>Notes  
Si vous souhaitez envoyer une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] directement au serveur sans préparation d’instruction par le pilote, vous pouvez définir l’attribut PDO::SQLSRV_ATTR_DIRECT_QUERY avec [PDO::setAttribute](../../connect/php/pdo-setattribute.md) (ou en tant qu’option de pilote transmise à [PDO::__construct](../../connect/php/pdo-construct.md)) ou lorsque vous appelez [PDO::prepare](../../connect/php/pdo-prepare.md). Par défaut, la valeur de PDO::SQLSRV_ATTR_DIRECT_QUERY est False (utilisez l’exécution d’instruction préparée).  
  
Si vous utilisez [PDO::query](../../connect/php/pdo-query.md), vous pouvez opter pour l’exécution directe. Avant d’appeler [PDO::query](../../connect/php/pdo-query.md), appelez [PDO::setAttribute](../../connect/php/pdo-setattribute.md) et définissez PDO::SQLSRV_ATTR_DIRECT_QUERY sur True.  Chaque appel à [PDO::query](../../connect/php/pdo-query.md) peut être exécuté avec un paramètre différent pour PDO::SQLSRV_ATTR_DIRECT_QUERY.  
  
Si vous utilisez [PDO::prepare](../../connect/php/pdo-prepare.md) and [PDOStatement::execute](../../connect/php/pdostatement-execute.md) pour exécuter une requête plusieurs fois à l’aide de paramètres liés, l’exécution d’une instruction préparée optimise l’exécution de la requête répétée.  Dans ce cas, appelez [PDO::prepare](../../connect/php/pdo-prepare.md) en définissant PDO::SQLSRV_ATTR_DIRECT_QUERY sur False dans le paramètre du tableau des options du pilote. Si nécessaire, vous pouvez exécuter des instructions préparées en définissant PDO::SQLSRV_ATTR_DIRECT_QUERY sur False.  
  
Après avoir avez appelé [PDO::prepare](../../connect/php/pdo-prepare.md), la valeur PDO::SQLSRV_ATTR_DIRECT_QUERY ne peut pas être modifiée lors de l’exécution de la requête préparée.  
  
Si une requête nécessite la définition du contexte dans une requête précédente, exécutez vos requêtes en définissant PDO::SQLSRV_ATTR_DIRECT_QUERY sur True. Par exemple, si vous utilisez des tables temporaires dans vos requêtes, PDO::SQLSRV_ATTR_DIRECT_QUERY doit avoir la valeur True.  
  
L’exemple suivant montre que lorsque le contexte d’une instruction précédente est requis, vous devez définir PDO::SQLSRV_ATTR_DIRECT_QUERY sur True. Cet exemple utilise des tables temporaires uniquement disponibles pour les instructions suivantes dans votre programme lorsque des requêtes sont exécutées directement.  
  
> [!NOTE]
> Si la requête consiste à appeler une procédure stockée et que des tables temporaires sont utilisées dans cette procédure stockée, utilisez plutôt [PDO::exec](../../connect/php/pdo-exec.md).

```  
<?php  
   $conn = new PDO('sqlsrv:Server=(local)', '', '');  
   $conn->setAttribute(constant('PDO::SQLSRV_ATTR_DIRECT_QUERY'), true);  
  
   $stmt1 = $conn->query("DROP TABLE #php_test_table");  
  
   $stmt2 = $conn->query("CREATE TABLE #php_test_table ([c1_int] int, [c2_int] int)");  
  
   $v1 = 1;  
   $v2 = 2;  
  
   $stmt3 = $conn->prepare("INSERT INTO #php_test_table (c1_int, c2_int) VALUES (:var1, :var2)");  
  
   if ($stmt3) {  
      $stmt3->bindValue(1, $v1);  
      $stmt3->bindValue(2, $v2);  
  
      if ($stmt3->execute())  
         echo "Execution succeeded\n";       
      else  
         echo "Execution failed\n";  
   }  
   else  
      var_dump($conn->errorInfo());  
  
   $stmt4 = $conn->query("DROP TABLE #php_test_table");  
?>  
```  
  
## <a name="see-also"></a>Voir aussi  
[Guide de programmation pour les pilotes Microsoft pour PHP pour SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)
  

---
title: Instruction directe-pilote PDO_SQLSRV d’exécution d’instruction préparée | Microsoft Docs
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67993622"
---
# <a name="direct-statement-execution-and-prepared-statement-execution-in-the-pdosqlsrv-driver"></a>Exécution d’instruction directe et exécution d’instruction préparée dans le pilote PDO_SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cette rubrique décrit l’utilisation de l’attribut PDO::SQLSRV_ATTR_DIRECT_QUERY pour spécifier l’exécution d’une instruction directe plutôt que le comportement par défaut, qui est l’exécution d’une instruction préparée. L’utilisation d’une instruction préparée peut entraîner de meilleures performances si l’instruction est exécutée plusieurs fois à l’aide d’une liaison de paramètre.  
  
## <a name="remarks"></a>Notes  
Si vous souhaitez envoyer directement une [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction au serveur sans que le pilote ait procédé à la préparation de l’instruction, vous pouvez définir l’attribut PDO:: SQLSRV_ATTR_DIRECT_QUERY avec [PDO:: setAttribute](../../connect/php/pdo-setattribute.md) (ou en tant qu’option de pilote transmise à [PDO:: __construct ](../../connect/php/pdo-construct.md)) ou lorsque vous appelez [PDO::p reparenthèse](../../connect/php/pdo-prepare.md). Par défaut, la valeur de PDO:: SQLSRV_ATTR_DIRECT_QUERY est false (utilisez l’exécution d’instruction préparée).  
  
Si vous utilisez [PDO:: Query](../../connect/php/pdo-query.md), vous souhaiterez peut-être exécuter l’exécution directe. Avant d’appeler [PDO:: Query](../../connect/php/pdo-query.md), appelez [PDO:: setAttribute](../../connect/php/pdo-setattribute.md) et affectez à PDO:: SQLSRV_ATTR_DIRECT_QUERY la valeur true.  Chaque appel à [PDO:: Query](../../connect/php/pdo-query.md) peut être exécuté avec un paramètre différent pour PDO:: SQLSRV_ATTR_DIRECT_QUERY.  
  
Si vous utilisez [PDO::p](../../connect/php/pdo-prepare.md) resfacer et [PDOStatement:: Execute](../../connect/php/pdostatement-execute.md) pour exécuter une requête plusieurs fois à l’aide de paramètres liés, l’exécution d’instructions préparées optimise l’exécution de la requête répétée.  Dans ce cas, appelez [PDO::p](../../connect/php/pdo-prepare.md) rescelle avec PDO:: SQLSRV_ATTR_DIRECT_QUERY défini sur false dans le paramètre Array des options du pilote. Si nécessaire, vous pouvez exécuter des instructions préparées avec PDO:: SQLSRV_ATTR_DIRECT_QUERY défini sur false.  
  
Après avoir appelé [PDO::p](../../connect/php/pdo-prepare.md)reparenthèses, la valeur de PDO:: SQLSRV_ATTR_DIRECT_QUERY ne peut pas être modifiée lors de l’exécution de la requête préparée.  
  
Si une requête requiert le contexte qui a été défini dans une requête précédente, exécutez vos requêtes avec PDO:: SQLSRV_ATTR_DIRECT_QUERY défini sur true. Par exemple, si vous utilisez des tables temporaires dans vos requêtes, PDO:: SQLSRV_ATTR_DIRECT_QUERY doit avoir la valeur true.  
  
L’exemple suivant montre que lorsque le contexte d’une instruction précédente est requis, vous devez définir PDO:: SQLSRV_ATTR_DIRECT_QUERY sur true. Cet exemple utilise des tables temporaires, qui sont uniquement disponibles pour les instructions suivantes dans votre programme lorsque les requêtes sont exécutées directement.  
  
> [!NOTE]
> Si la requête consiste à appeler une procédure stockée et que des tables temporaires sont utilisées dans cette procédure stockée, utilisez [PDO:: exec](../../connect/php/pdo-exec.md) à la place.

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
  

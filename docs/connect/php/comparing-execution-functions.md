---
title: "Comparaison des fonctions d’exécution | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- executing queries
ms.assetid: 130fc0fd-87dd-46b2-918f-de9dc572c769
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e74c7433ab2e3a831d6aa800a2a1a9abbbda5863
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="comparing-execution-functions"></a>Comparaison des fonctions d’exécution
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] fournit plusieurs options pour les fonctions d’exécution.  
  
Si vous utilisez le pilote SQLSRV, utilisez [sqlsrv_query](../../connect/php/sqlsrv-query.md) pour exécuter une requête unique et [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md) avec [sqlsrv_execute](../../connect/php/sqlsrv-execute.md) pour exécuter une instruction préparée plusieurs fois avec différentes valeurs de paramètre pour chaque exécution.  
  
Si vous utilisez le pilote PDO_SQLSRV, vous pouvez exécuter une requête avec l’une des fonctions suivantes :  
  
-   [PDO::exec](../../connect/php/pdo-exec.md)  
  
-   [PDO::Query](../../connect/php/pdo-query.md)  
  
-   [PDO::prepare](../../connect/php/pdo-prepare.md) et [PDOStatement::execute](../../connect/php/pdostatement-execute.md).  
  
## <a name="see-also"></a>Voir aussi  
[référence d’API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Référence de pilote PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
[Guide de programmation pour le pilote SQL PHP](../../connect/php/programming-guide-for-php-sql-driver.md)
  


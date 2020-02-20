---
title: Comparer les fonctions d’exécution| Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- executing queries
ms.assetid: 130fc0fd-87dd-46b2-918f-de9dc572c769
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f2b4d6c85c399589aae4eedbaade4bbdc4f70609
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67993744"
---
# <a name="comparing-execution-functions"></a>Comparaison des fonctions d’exécution
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] fournit plusieurs options pour les fonctions d’exécution.  

## <a name="sqlsrv-execution-functions"></a>Fonctions d’exécution SQLSRV  
Si vous utilisez le pilote SQLSRV, utilisez [sqlsrv_query](../../connect/php/sqlsrv-query.md) pour exécuter une requête unique et [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md) avec [sqlsrv_execute](../../connect/php/sqlsrv-execute.md) pour exécuter une instruction préparée plusieurs fois avec différentes valeurs de paramètre pour chaque exécution.  

## <a name="pdo_sqlsrv-execution-functions"></a>Fonctions d’exécution PDO_SQLSRV 
Si vous utilisez le pilote PDO_SQLSRV, vous pouvez exécuter une requête avec l’une des fonctions suivantes :  
  
-   [PDO::exec](../../connect/php/pdo-exec.md)  
  
-   [PDO::query](../../connect/php/pdo-query.md)  
  
-   [PDO::prepare](../../connect/php/pdo-prepare.md) et [PDOStatement::execute](../../connect/php/pdostatement-execute.md).  
  
## <a name="see-also"></a> Voir aussi  
[Informations de référence sur l’API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Informations de référence sur le pilote PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)

[Guide de programmation pour les pilotes Microsoft pour PHP pour SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)
  

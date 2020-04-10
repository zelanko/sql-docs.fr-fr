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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 68575f3a0227c6400ed5d927ff603b66bd6f440d
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925867"
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
  
## <a name="see-also"></a>Voir aussi  
[Informations de référence sur l’API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Informations de référence sur le pilote PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)

[Guide de programmation pour les pilotes Microsoft pour PHP pour SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)
  

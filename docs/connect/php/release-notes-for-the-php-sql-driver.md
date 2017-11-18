---
title: Notes de publication pour le pilote SQL PHP | Documents Microsoft
ms.custom: 
ms.date: 07/12/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- what's new in version 1.1
ms.assetid: 91cca3d2-ba99-4a6d-b0de-beb9699cb3f8
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2c63079bda91844995540aade94bac397be6b94c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="release-notes-for-the-php-sql-driver"></a>Notes de publication pour le pilote SQL PHP
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cette rubrique explique ce qui a été ajouté dans chaque version de la [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  

## <a name="whats-new-in-version-43"></a>Nouveautés de la Version 4.3

- Prise en charge de PHP 7.1
- Prise en charge de Mac OS Sierra et Mac OS El Capitan
- Prise en charge d’Ubuntu 15.10 et Debian 8
- Prise en charge supprimée pour Ubuntu 15.04
- Prise en charge pour les groupes de disponibilité Always On via la résolution IP réseau Transparent. Pour plus d’informations, consultez [Connection Options](../../connect/php/connection-options.md). 
- Prise en charge supplémentaire pour le type de données sql_variant limitation.
- Prise en charge de résilience des connexions inactive dans Windows. Pour plus d’informations, consultez [Connection Options](../../connect/php/connection-options.md).
- Connexion mise en pool de prise en charge de Linux et macOS. Pour plus d’informations, consultez [le regroupement de connexions](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md).
- Prise en charge pour l’authentification Azure Active Directory avec ActiveDirectoryPassword et SqlPassword. Pour plus d’informations, consultez [Connection Options](../../connect/php/connection-options.md).
  
## <a name="whats-new-in-version-40"></a>Quelles sont les nouveautés dans la Version 4.0 

- Prise en charge de PHP 7.0  
- Prise en charge 64 bits
- Prise en charge d’Ubuntu 15.04 et Ubuntu 16.04 RedHat 7

## <a name="whats-new-in-version-32"></a>Nouveautés de la version 3.2 

- Prise en charge de PHP 5.6   
- Inclut les dernières mises à jour pour les versions antérieures PHP 5.5 et 5.4   
- Nécessite Microsoft ODBC Driver 11 pour SQL Server  
  
## <a name="whats-new-in-version-31"></a>Nouveautés de la version 3.1
 
- Prise en charge de PHP 5.5  
- Nécessite Microsoft ODBC Driver 11 pour SQL Server. Les versions précédentes nécessitaient SQL Native Client.  
  
## <a name="whats-new-in-version-30"></a>Nouveautés de la version 3.0  

- Prise en charge de PHP 5.4.  PHP 5.2 n’est pas pris en charge dans la version 3 du [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
- Ajout de l’option de connexion AttachDBFileName. Pour plus d’informations, consultez [Connection Options](../../connect/php/connection-options.md).  
- Prise en charge de la base de données locale, qui a été ajoutée dans [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]. Pour plus d’informations, consultez [PHP Driver for SQL Server Support for LocalDB](../../connect/php/php-driver-for-sql-server-support-for-localdb.md).
- Ajout de l’option de connexion AttachDBFileName. Pour plus d’informations, consultez [Connection Options](../../connect/php/connection-options.md).  
- Prise en charge des fonctionnalités de récupération d’urgence/haute disponibilité. Pour plus d’informations, consultez [Pilote PHP pour la prise en charge de la haute disponibilité et de la récupération d’urgence par SQL Server](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).
- Prise en charge des curseurs côté client (mise en cache d’un jeu de résultats en mémoire). Pour plus d’informations, consultez [Types de curseur &#40; Pilote SQLSRV &#41; ](../../connect/php/cursor-types-sqlsrv-driver.md) et [Types de curseur &#40; Pilote PDO_SQLSRV &#41; ](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).
- Ajout de l’attribut PDO::ATTR_EMULATE_PREPARES. Pour plus d’informations, consultez [PDO::prepare](../../connect/php/pdo-prepare.md).  
  
## <a name="whats-new-in-version-20"></a>Nouveautés de la version 2.0  
Dans la version 2.0, la prise en charge du pilote PDO_SQLSRV a été ajoutée. Pour plus d’informations, consultez [Référence de pilote PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md).  
  
## <a name="see-also"></a>Voir aussi  
[Vue d’ensemble du pilote SQL PHP](../../connect/php/overview-of-the-php-sql-driver.md)
  


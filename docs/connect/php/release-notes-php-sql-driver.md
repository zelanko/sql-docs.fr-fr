---
title: Notes de publication des pilotes Microsoft pour PHP pour SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 02/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: v-dapugl, kenvh
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- what's new in version 1.1
ms.assetid: 91cca3d2-ba99-4a6d-b0de-beb9699cb3f8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 23ac53a8515f55dfc0cad282fd14294e5f285af9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67935915"
---
# <a name="release-notes-for-the-microsoft-drivers-for-php-for-sql-server"></a>Notes de publication de Microsoft Drivers for PHP for SQL Server

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cette page décrit ce qui a été ajouté dans chaque version de [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  

<!--
Hello, We are standardizing the format of content inside our Release Notes (or What's New) articles.
Instead of bullets (or paragraphs), we have shifted to the 2-column format you see for H2 **What's New in Version 5.6**.
It is not necessary to reformat all the older H2 sections in this Release Notes file, but.....

Going forward, please be sure to use the 2-column format.

Also, all Release Notes .md file names now must begin with 'release-notes-*.md'.  And no filler words.
The 5.6 edition of this file is being renamed.....
FROM:  'release-notes-for-the-php-sql-driver.md'
TO  :  'release-notes-php-sql-driver.md'

For any questions, ask GeneMi or CraigG.
Thanks a lot.  2019-03-28  (DevO= 1467988)
-->

## <a name="whats-new-in-version-56"></a>Nouveautés de la version 5.6

| Nouvel élément | Détails |
| :------- | :------ |
| Prise en charge de PHP 7.3. | &nbsp; |
| Suppression de la prise en charge de PHP 7,0. | &nbsp; |
| Prise en charge du pilote Microsoft ODBC 17,3 sur toutes les plateformes. | &nbsp; |
| Prise en charge de macOS Mojave. | Requiert le pilote ODBC 17,3 ou version ultérieure. |
| Prise en charge d’Ubuntu 18,10 et SUSE Linux 15. | Les deux nécessitent le pilote ODBC 17,3 ou version ultérieure. |
| Suppression de la prise en charge de Linux Ubuntu 17,10 et macOS El Capitan. | &nbsp; |
| Prise en charge d’Azure AD jeton d’accès. | Sur Linux et macOS, requiert le pilote ODBC 17.2 + et unixODBC 2.3.6 +. |
| Prise en charge de l’authentification avec Azure AD à l’aide de l’identité managée pour les ressources Azure. | Nécessite ODBC Driver 17.3 +. |
| Nouvelles fonctionnalités d’extraction | &bull;&nbsp; Nouvel indicateur PDO:: SQLSRV_ATTR_FETCHES_DATETIME_TYPE pour pdo_sqlsrv pour retourner DateTime en tant qu’objets.<br/><br/>&bull;&nbsp; Ajoutez l’option ReturnDatesAsStrings au niveau de l’instruction pour SQLSRV.<br/><br/>&bull;&nbsp; Nouvelles options au niveau de la connexion et des instructions pour les deux pilotes afin de mettre en forme les valeurs décimales dans les résultats récupérés. |
| Prise en charge de la compilation statique des pilotes si les utilisateurs choisissent de générer à partir de la source. | &nbsp; |
| Amélioration des performances en mettant en cache les métadonnées lors des extractions et en accélérant les conversions de chaînes Unicode. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="whats-new-in-version-53"></a>Nouveautés de la version 5.3

- Prise en charge du pilote Microsoft ODBC 17,2 sur toutes les plateformes
- Prise en charge de macOS High Sierra (requiert le pilote ODBC 17 et versions ultérieures)
- La prise en charge de Azure Key Vault pour Always Encrypted pour les fonctionnalités CRUD de base, car Always Encrypted fonctionnalité est disponible pour toutes les plateformes Windows, Linux ou macOS prises en charge [à l’aide de Always Encrypted avec les pilotes php pour SQL Server](../../connect/php/using-always-encrypted-php-drivers.md)
- Prise en charge d’Ubuntu 18,04 LTS (requiert le pilote ODBC 17,2)
- Prise en charge de la résilience des connexions dans Linux ou macOS (nécessite le pilote ODBC 17,2)

## <a name="whats-new-in-version-52"></a>Nouveautés de la version 5.2

- Prise en charge de PHP 7.2.1 et up sur Windows, et 7.2.0 et sur d’autres plateformes
- Prise en charge de Microsoft ODBC Driver 17
  - La version 17 est désormais la valeur par défaut sur toutes les plateformes
- Prise en charge d’Ubuntu 17,10, Debian 9 et SuSE Enterprise Linux 12
- Suppression de la prise en charge d’Ubuntu 15,10
- Prise en charge de Always Encrypted avec des fonctionnalités CRUD sur Windows. Pour plus d’informations, consultez [Utilisation d’Always Encrypted avec les pilotes PHP pour SQL Server](../../connect/php/using-always-encrypted-php-drivers.md)
  - Prise en charge du magasin de certificats Windows
  - Always Encrypted est pris en charge uniquement avec le pilote Microsoft ODBC 17 et versions ultérieures
- Prise en charge des paramètres régionaux non-UTF8 sur Linux et macOS
  - Les paramètres régionaux non UTF8 sur Linux et macOS sont uniquement pris en charge avec le pilote Microsoft ODBC 17 et versions ultérieures
- Prise en charge d’Azure SQL Data Warehouse
- Prise en charge d’Azure SQL Managed Instance (préversion privée étendue)

## <a name="whats-new-in-version-43"></a>Nouveautés de la version 4.3

- Prise en charge de PHP 7.1
- Prise en charge de macOS Sierra et macOS El Capitan
- Prise en charge d’Ubuntu 15,10 et de Debian 8
- Suppression de la prise en charge d’Ubuntu 15,04
- La prise en charge de Always On groupes de disponibilité via une résolution d’adresse IP réseau transparente. Pour plus d’informations, consultez [Connection Options](../../connect/php/connection-options.md).
- Ajout de la prise en charge du type de données sql_variant avec limitation.
- Prise en charge de la résilience des connexions inactives dans Windows. Pour plus d’informations, consultez [Connection Options](../../connect/php/connection-options.md).
- Prise en charge du regroupement de connexions pour Linux et macOS. Pour plus d’informations, consultez [Regroupement de connexions](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md).
- Prise en charge de l’authentification Azure Active Directory avec ActiveDirectoryPassword et SqlPassword. Pour plus d’informations, consultez [Connection Options](../../connect/php/connection-options.md).

## <a name="whats-new-in-version-40"></a>Nouveautés de la version 4.0

- Prise en charge de PHP 7.0  
- Prise en charge complète de 64 bits
- Prise en charge d’Ubuntu 15,04, Ubuntu 16,04 et RedHat 7

## <a name="whats-new-in-version-32"></a>Nouveautés de la version 3.2

- Prise en charge de PHP 5.6   
- Inclut les dernières mises à jour pour les versions antérieures PHP 5.5 et 5.4   
- Nécessite Microsoft ODBC Driver 11 for SQL Server  

## <a name="whats-new-in-version-31"></a>Nouveautés de la version 3.1

- Prise en charge de PHP 5.5  
- Nécessite Microsoft ODBC Driver 11 for SQL Server. Les versions précédentes nécessitaient SQL Native Client.  

## <a name="whats-new-in-version-30"></a>Nouveautés de la version 3.0  

- Prise en charge de PHP 5.4.  PHP 5.2 n’est pas pris en charge dans la version 3 du [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
- Ajout de l’option de connexion AttachDBFileName. Pour plus d’informations, consultez [Connection Options](../../connect/php/connection-options.md).  
- Prise en charge de la Base de données locale, qui a été ajoutée dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Pour plus d’informations, consultez [prise en charge de](../../connect/php/php-driver-for-sql-server-support-for-localdb.md)la base de données locale.
- Ajout de l’option de connexion AttachDBFileName. Pour plus d’informations, consultez [Connection Options](../../connect/php/connection-options.md).  
- Prise en charge des fonctionnalités de récupération d’urgence/haute disponibilité. Pour plus d’informations, consultez [Prise en charge de la haute disponibilité et de la récupération d'urgence](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).
- Prise en charge des curseurs côté client (mise en cache d’un jeu de résultats en mémoire). Pour plus d’informations, consultez [Types de curseur &#40;pilote SQLSRV&#41;](../../connect/php/cursor-types-sqlsrv-driver.md) et [Types de curseur &#40;pilote PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).
- Ajout de l’attribut PDO::ATTR_EMULATE_PREPARES. Pour plus d’informations, consultez [PDO::prepare](../../connect/php/pdo-prepare.md).  

## <a name="whats-new-in-version-20"></a>Nouveautés de la version 2.0

Dans la version 2.0, la prise en charge du pilote PDO_SQLSRV a été ajoutée. Pour plus d’informations, consultez [Référence de pilote PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md).  

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft Drivers for PHP for SQL Server](../../connect/php/overview-of-the-php-sql-driver.md)

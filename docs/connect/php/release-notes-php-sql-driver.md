---
title: Notes de publication des pilotes Microsoft pour PHP pour SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 01/31/2020
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
ms.openlocfilehash: 5e279ba446e790a2262e5f0effe160632065dcba
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76941218"
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

## <a name="whats-new-in-version-58"></a>Nouveautés de la version 5.8

| Nouvel élément | Détails |
| :------- | :------ |
| Ajout de la prise en charge de PHP 7.4. | &nbsp; |
| Prise en charge de PHP 7.1 abandonnée. | &nbsp; |
| Ajout de la prise en charge de Microsoft ODBC Driver 17.5 sur toutes les plateformes. | &nbsp; |
| Ajout de la prise en charge de Debian 10 et Red Hat 8. | Les deux nécessitent le pilote ODBC 17.4 ou une version ultérieure. |
| Ajout de la prise en charge de macOS Catalina, Alpine Linux 3.11<sup>1</sup> et Ubuntu 19.10. | Tous nécessitent le pilote ODBC 17.5 ou une version ultérieure. |
| Suppression de la prise en charge de SQL Server 2008 R2, macOS Sierra, Ubuntu 18.10 et Ubuntu 19.04. | &nbsp; |
| Prise en charge de l’option de langue lors de la connexion à SQL Server. | &nbsp; |
| Prise en charge des types de chaînes étendus introduits dans PHP 7.2. | &nbsp; |
| Prise en charge de la récupération des métadonnées de sensibilité de la classification des données. | Nécessite SQL Server 2019 et le pilote ODBC 17.4.2 ou une version ultérieure. |
| Prise en charge d’Always Encrypted avec enclaves sécurisées. | Requiert le pilote ODBC 17.4 ou une version ultérieure. |
| Prise en charge des options configurables pour les paramètres régionaux dans Linux et macOS. |
| Amélioration des performances grâce à la mise en cache des métadonnées lors des extractions et l’omission des appels redondants. | &nbsp; |
| &nbsp; | &nbsp; |

<sup>1</sup> La prise en charge d’Alpine Linux est expérimentale pour la version 5.8.

## <a name="whats-new-in-version-56"></a>Nouveautés de la version 5.6

| Nouvel élément | Détails |
| :------- | :------ |
| Prise en charge de PHP 7.3. | &nbsp; |
| Prise en charge de PHP 7.0 abandonnée. | &nbsp; |
| Prise en charge de Microsoft ODBC Driver 17.3 sur toutes les plateformes. | &nbsp; |
| Prise en charge de macOS Mojave. | Requiert le pilote ODBC 17.3 ou une version ultérieure. |
| Prise en charge d’Ubuntu 18.10 et SUSE Linux 15. | Les deux nécessitent le pilote ODBC 17.3 ou une version ultérieure. |
| Suppression de la prise en charge de Linux Ubuntu 17.10 et macOS El Capitan. | &nbsp; |
| Prise en charge du jeton d’accès Azure AD. | Sur Linux et macOS, requiert le pilote ODBC 17.2+ et unixODBC 2.3.6+. |
| Prise en charge de l’authentification avec Azure AD à l’aide de l’identité managée pour les ressources Azure. | Nécessite ODBC Driver 17.3+. |
| Nouvelles fonctionnalités d’extraction | &bull; &nbsp; Nouvel indicateur PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE pour que pdo_sqlsrv renvoie des datetime en tant qu’objets.<br/><br/>&bull; &nbsp; Ajout de l’option ReturnDatesAsStrings au niveau de l’instruction pour sqlsrv.<br/><br/>&bull; &nbsp; Nouvelles options au niveau de la connexion et des instructions pour les deux pilotes afin de mettre en forme les valeurs décimales dans les résultats récupérés. |
| Prise en charge de la compilation statique des pilotes si les utilisateurs choisissent de générer à partir de la source. | &nbsp; |
| Amélioration des performances en mettant en cache les métadonnées lors des extractions et en accélérant les conversions de chaînes Unicode. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="whats-new-in-version-53"></a>Nouveautés de la version 5.3

- Prise en charge de Microsoft ODBC Driver 17.2 sur toutes les plateformes
- Prise en charge de macOS High Sierra (requiert le pilote ODBC 17 ou une version ultérieure)
- Prise en charge d’Azure Key Vault pour Always Encrypted pour les fonctionnalités CRUD de base, car la fonctionnalité Always Encrypted est disponible pour toutes les plateformes Windows, Linux ou macOS prises en charge [Utilisation d’Always Encrypted avec Microsoft Drivers for PHP for SQL Server](../../connect/php/using-always-encrypted-php-drivers.md)
- Prise en charge d’Ubuntu 18.04 LTS (requiert le pilote ODBC 17.2)
- Prise en charge de la résilience des connexions dans Linux ou macOS (nécessite le pilote ODBC 17.2)

## <a name="whats-new-in-version-52"></a>Nouveautés de la version 5.2

- Prise en charge de PHP 7.2.1 et versions ultérieures sur Windows, et de la version 7.2.0 sur les autres plateformes
- Prise en charge de Microsoft ODBC Driver 17
  - La version 17 est désormais la version par défaut sur toutes les plateformes
- Prise en charge d’Ubuntu 17.10, Debian 9 et SuSE Enterprise Linux 12
- Prise en charge d’Ubuntu 15.10 abandonnée
- Prise en charge d’Always Encrypted avec des fonctionnalités CRUD sur Windows. Pour plus d’informations, consultez [Utilisation d’Always Encrypted avec les pilotes PHP pour SQL Server](../../connect/php/using-always-encrypted-php-drivers.md)
  - Prise en charge du Magasin de certificats Windows
  - Always Encrypted est pris en charge uniquement avec le pilote Microsoft ODBC 17 et versions ultérieures
- Prise en charge des paramètres régionaux non UTF8 sur Linux et macOS
  - Les paramètres régionaux non UTF8 sur Linux et macOS sont uniquement pris en charge avec le pilote Microsoft ODBC 17 et versions ultérieures
- Prise en charge d’Azure SQL Data Warehouse
- Prise en charge d’Azure SQL Managed Instance

## <a name="whats-new-in-version-43"></a>Nouveautés de la version 4.3

- Prise en charge de PHP 7.1
- Prise en charge de macOS Sierra et de macOS El Capitan
- Prise en charge d’Ubuntu 15.10 et de Debian 8
- Prise en charge d’Ubuntu 15.04 abandonnée
- Prise en charge des groupes de disponibilité Always On via une résolution d’adresse IP réseau transparente. Pour plus d’informations, consultez [Connection Options](../../connect/php/connection-options.md).
- Ajout de la prise en charge du type de données sql_variant avec des limitations.
- Prise en charge de la résilience des connexions inactives dans Windows. Pour plus d’informations, consultez [Connection Options](../../connect/php/connection-options.md).
- Prise en charge du regroupement de connexions pour Linux et macOS. Pour plus d’informations, consultez [Regroupement de connexions](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md).
- Prise en charge de l’authentification Azure Active Directory avec ActiveDirectoryPassword et SqlPassword. Pour plus d’informations, consultez [Connection Options](../../connect/php/connection-options.md).

## <a name="whats-new-in-version-40"></a>Nouveautés de la version 4.0

- Prise en charge de PHP 7.0  
- Prise en charge 64 bits complète
- Prise en charge d’Ubuntu 15.04, Ubuntu 16.04 et RedHat 7

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
- Prise en charge de la Base de données locale, qui a été ajoutée dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Pour plus d’informations, consultez [Prise en charge de LocalDB](../../connect/php/php-driver-for-sql-server-support-for-localdb.md).
- Ajout de l’option de connexion AttachDBFileName. Pour plus d’informations, consultez [Connection Options](../../connect/php/connection-options.md).  
- Prise en charge des fonctionnalités de récupération d’urgence/haute disponibilité. Pour plus d’informations, consultez [Prise en charge de la haute disponibilité et de la récupération d'urgence](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).
- Prise en charge des curseurs côté client (mise en cache d’un jeu de résultats en mémoire). Pour plus d’informations, consultez [Types de curseur &#40;pilote SQLSRV&#41;](../../connect/php/cursor-types-sqlsrv-driver.md) et [Types de curseur &#40;pilote PDO_SQLSRV&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).
- Ajout de l’attribut PDO::ATTR_EMULATE_PREPARES. Pour plus d’informations, consultez [PDO::prepare](../../connect/php/pdo-prepare.md).  

## <a name="whats-new-in-version-20"></a>Nouveautés de la version 2.0

Dans la version 2.0, la prise en charge du pilote PDO_SQLSRV a été ajoutée. Pour plus d’informations, consultez [Référence de pilote PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md).  

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft Drivers for PHP for SQL Server](../../connect/php/overview-of-the-php-sql-driver.md)

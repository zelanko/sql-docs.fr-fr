---
title: Configuration requise des pilotes Microsoft pour PHP pour SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- requirements
ms.assetid: 5db4b75f-c605-4785-9560-399a533c0fc9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b601d4fbb02b489aca228acb719cfe8bad834dc0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67992571"
---
# <a name="system-requirements-for-the-microsoft-drivers-for-php-for-sql-server"></a>Configuration système requise pour Microsoft Drivers for PHP for SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Ce document répertorie les composants qui doivent être installés sur votre système pour accéder aux données d’un SQL Server ou Azure SQL Database [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]à l’aide de l'.

Les versions 3,1 et ultérieures des pilotes Microsoft PHP pour SQL Server sont officiellement prises en charge. Pour plus d’informations sur les cycles de vie de support et la configuration requise, notamment les versions antérieures des pilotes PHP, consultez la [matrice de prise en charge](../../connect/php/microsoft-php-drivers-for-sql-server-support-matrix.md).

## <a name="php"></a>PHP

Pour plus d’informations sur le téléchargement et l’installation des derniers fichiers binaires PHP stables, consultez le [site web PHP](https://php.net).  Les pilotes Microsoft pour PHP pour SQL Server requièrent les versions suivantes de PHP:

|Version du pilote PHP pour SQL Server&#8594;<br />&#8595; Version de PHP|5.6|5.3|5.2|4.3|4.0|3.2|3.1|
|:---:|---|---|---|---|---|---|---|
|7.3|7.3.0+ | | | | | | |
|7.2|7.2 +<sup>1</sup>|7.2 +<sup>1</sup>|7.2 +<sup>1</sup>| | | | |
|7.1|7.1.0+ |7.1.0+ |7.1.0+ |7.1.0+ |       |        |        |
|7.0|       |7.0.0+ |7.0.0+ |7.0.0+ |7.0.0+ |        |        |
|5.6|       |       |       |       |       |5.6.4+  |        |
|5.5|       |       |       |       |       |5.5.16+ |5.5.16+ |
|5.4|       |       |       |       |       |5.4.32  |5.4.32  |

1. Les versions 7.2.1 et ultérieures sont prises en charge sur Windows, tandis que les versions 7.2.0 et ultérieures sont prises en charge sur Linux et macOS.

-   Une version du fichier de pilote doit se trouver dans votre répertoire d’extensions PHP. Pour plus d’informations sur les différents fichiers de pilotes, consultez [versions de pilote](#driver-versions) .  Pour télécharger les pilotes, consultez [Télécharger Microsoft Drivers for PHP for SQL Server](../../connect/php/download-drivers-php-sql-server.md). Pour plus d’informations sur la configuration du pilote PHP, consultez [Chargement de Microsoft Drivers for PHP for SQL Server](../../connect/php/loading-the-php-sql-driver.md).

-   Un serveur web est nécessaire. Votre serveur web doit être configuré pour exécuter PHP. Pour plus d’informations sur l’hébergement d’applications PHP avec IIS, consultez le [didacticiel sur le site Web de php](http://docs.php.net/manual/da/install.windows.iis7.php).

    Les [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] ont été testés à l’aide d’IIS 10 avec FastCGI.  

    > [!NOTE]  
    > Microsoft prend en charge uniquement IIS.  

## <a name="odbc-driver"></a>Pilote ODBC

La version correcte du Microsoft ODBC Driver for SQL Server est requise sur l’ordinateur sur lequel PHP est en cours d’exécution. Vous pouvez télécharger toutes les versions prises en charge du pilote pour les plateformes prises en charge sur [cette page](https://docs.microsoft.com/sql/connect/odbc/download-odbc-driver-for-sql-server?view=sql-server-2017).

Si vous téléchargez la version Windows du pilote sur une version 64 bits de Windows, le programme d’installation ODBC 64 bits installe les pilotes ODBC 32 bits et 64 bits. Si vous utilisez une version 32 bits de Windows, utilisez le programme d’installation ODBC x86. Sur les plateformes non-Windows, seules les versions 64 bits du pilote sont disponibles.

|Version du pilote PHP pour SQL Server&#8594;<br />&#8595; Version du pilote ODBC|5.6|5.3|5.2|4.3|4.0|3.2|3.1|
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|ODBC Driver 17+ |O|O|O| | | | |
|ODBC Driver 13.1|O|O|O|O|O| | |
|ODBC Driver 13  | | | | |O| | |
|ODBC Driver 11  |O|O|O|O|O|O|O|

Si vous utilisez le pilote sqlsrv, [sqlsrv_client_info](../../connect/php/sqlsrv-client-info.md) retourne des informations sur la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Microsoft ODBC Driver for SQL Server utilisée par le [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. Si vous utilisez le pilote PDO_SQLSRV, vous pouvez utiliser [PDO::getAttribute](../../connect/php/pdo-getattribute.md) pour découvrir la version.  

## <a name="sql-server"></a>SQL Server

Les bases de données SQL Azure sont prises en charge. Pour plus d’informations, consultez [Connexion à Microsoft Azure SQL Database](../../connect/php/connecting-to-microsoft-azure-sql-database.md).

|Version du pilote PHP pour SQL Server&#8594;<br />&#8595; Version de SQL Server|5.6|5.3|5.2|4.3|4.0|3.2|3.1|
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Azure SQL Database        |O|O|O|O| | | |
|Azure SQL Managed Instance|O|O|O|O| | | |
|Azure SQL Data Warehouse.  |O|O|O|O| | | |
|SQL Server 2017           |O|O|O|O| | | |
|SQL Server 2016           |O|O|O|O|O| | |
|SQL Server 2014           |O|O|O|O|O|O|O|
|SQL Server 2012           |O|O|O|O|O|O|O|
|SQL Server 2008 R2        |O|O|O|O|O|O|O|
|SQL Server 2008           | | | | |O|O|O|

## <a name="operating-systems"></a>Systèmes d'exploitation
Les systèmes d’exploitation pris en charge pour chaque version du pilote sont les suivants:

|Version du pilote PHP pour SQL Server&#8594;<br />&#8595; Système d’exploitation|5.6|5.3|5.2|4.3|4.0|3.2|3.1|
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Windows Server 2016                 |O  |O  |O  |O  |   |   |   |
|Windows Server 2012 R2              |O  |O  |O  |O  |O  |O  |O  |
|Windows Server 2012                 |O  |O  |O  |O  |O  |O  |O  |
|Windows Server 2008 R2 SP1          |   |   |   |   |O  |O  |O  |
|Windows Server 2008 SP2             |   |   |   |   |O  |O  |O  |
|Windows 10                          |O  |O  |O  |O  |O  |   |   |
|Windows 8.1                         |O  |O  |O  |O  |O  |O  |O  |
|Windows 8                           |   |   |   |O  |O  |O  |O  |
|Windows 7 SP1                       |   |   |   |   |O  |O  |O  |
|Windows Vista SP2                   |   |   |   |   |O  |O  |O  |
|Ubuntu 18,10 (64 bits)               |O  |   |   |   |   |   |   |
|Ubuntu 18,04 (64 bits)               |O  |O  |   |   |   |   |   |
|Ubuntu 17,10 (64 bits)               |   |O  |O  |   |   |   |   |
|Ubuntu 16,04 (64 bits)               |O  |O  |O  |O  |O  |   |   |
|Ubuntu 15,10 (64 bits)               |   |   |   |O  |   |   |   |
|Ubuntu 15,04 (64 bits)               |   |   |   |   |O  |   |   |
|Debian 9 (64 bits)                   |O  |O  |O  |   |   |   |   |
|Debian 8 (64 bits)                   |O  |O  |O  |O  |   |   |   |
|Red Hat Enterprise Linux 7 (64-bit) |O  |O  |O  |O  |O  |   |   |
|SuSE Enterprise Linux 15 (64 bits)   |O  |   |   |   |   |   |   |
|SuSE Enterprise Linux 12 (64 bits)   |O  |O  |O  |   |   |   |   |
|macOS Mojave (64 bits)               |O  |   |   |   |   |   |   |
|macOS High Sierra (64 bits)          |O  |O  |   |   |   |   |   |
|macOS Sierra (64 bits)               |O  |O  |O  |O  |   |   |   |
|macOS El Capitan (64 bits)           |   |O  |O  |O  |   |   |   |

## <a name="driver-versions"></a>Versions de pilotes  
Cette section répertorie les fichiers de pilote qui sont inclus avec chaque version [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]de. Chaque package d’installation contient des fichiers de pilote SQLSRV et PDO_SQLSRV dans des variantes de thread et non thread. Sur Windows, elles sont également disponibles en variantes 32 bits et 64 bits. Pour configurer le pilote à utiliser avec le runtime PHP, suivez les instructions d’installation dans [chargement des pilotes Microsoft pour PHP pour SQL Server](../../connect/php/loading-the-php-sql-driver.md).

Sur les versions prises en charge de Linux et macOS, les pilotes appropriés peuvent être installés à l’aide du système de package PECL de PHP, en suivant les [instructions d’installation de Linux et de MacOS](../../connect/php/installation-tutorial-linux-mac.md). Vous pouvez également télécharger des fichiers binaires prégénérés pour votre plateforme à partir de la page de projets [Microsoft drivers for PHP for SQL Server](https://github.com/Microsoft/msphpsql/releases) GitHub--les tableaux ci-dessous répertorient les fichiers trouvés dans les packages binaires prégénérés.

**Microsoft Drivers 5.6 PHP pour SQL Server :**  

Sur Windows, les versions suivantes du pilote sont incluses:

|Fichier de pilote|Version de PHP|Thread-safe ?|Utiliser avec .dll PHP|  
|---------------|:---------------:|:----------------:|---------------------|  
|32-bit php_sqlsrv_71_nts.dll<br />32-bit php_pdo_sqlsrv_71_nts.dll|7.1|non |32-bit php7. dll|  
|32-bit php_sqlsrv_71_ts.dll <br />32-bit php_pdo_sqlsrv_71_ts.dll |7.1|oui|32-bit php7ts. dll|  
|64-bit php_sqlsrv_71_nts.dll<br />64-bit php_pdo_sqlsrv_71_nts.dll|7.1|non |64-bit php7. dll|  
|64-bit php_sqlsrv_71_ts.dll <br />64-bit php_pdo_sqlsrv_71_ts.dll |7.1|oui|64-bit php7ts. dll|   
|32-bit php_sqlsrv_72_nts.dll<br />32-bit php_pdo_sqlsrv_72_nts.dll|7.2|non |32-bit php7. dll|  
|32-bit php_sqlsrv_72_ts.dll <br />32-bit php_pdo_sqlsrv_72_ts.dll |7.2|oui|32-bit php7ts. dll|  
|64-bit php_sqlsrv_72_nts.dll<br />64-bit php_pdo_sqlsrv_72_nts.dll|7.2|non |64-bit php7. dll|  
|64-bit php_sqlsrv_72_ts.dll <br />64-bit php_pdo_sqlsrv_72_ts.dll |7.2|oui|64-bit php7ts. dll|  
|32-bit php_sqlsrv_73_nts.dll<br />32-bit php_pdo_sqlsrv_73_nts.dll|7.3|non |32-bit php7. dll|  
|32-bit php_sqlsrv_73_ts.dll <br />32-bit php_pdo_sqlsrv_73_ts.dll |7.3|oui|32-bit php7ts. dll|  
|64-bit php_sqlsrv_73_nts.dll<br />64-bit php_pdo_sqlsrv_73_nts.dll|7.3|non |64-bit php7. dll|  
|64-bit php_sqlsrv_73_ts.dll <br />64-bit php_pdo_sqlsrv_73_ts.dll |7.3|oui|64-bit php7ts. dll|  

Sur Linux, les versions suivantes du pilote sont incluses:

|Fichier de pilote|Version de PHP|Thread-safe ?|
|---------------|:---------------:|:----------------:|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|non |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|oui|  
|php_sqlsrv_72_nts.so<br />php_pdo_sqlsrv_72_nts.so|7.2|non |
|php_sqlsrv_72_ts.so <br />php_pdo_sqlsrv_72_ts.so |7.2|oui|
|php_sqlsrv_73_nts.so<br />php_pdo_sqlsrv_73_nts.so|7.3|non |
|php_sqlsrv_73_ts.so <br />php_pdo_sqlsrv_73_ts.so |7.3|oui|

**Microsoft Drivers 5.3 for PHP for SQL Server :**  

Sur Windows, les versions suivantes du pilote sont incluses:

|Fichier de pilote|Version de PHP|Thread-safe ?|Utiliser avec .dll PHP|  
|---------------|:---------------:|:----------------:|---------------------|  
|32-bit php_sqlsrv_7_nts.dll <br />32-bit php_pdo_sqlsrv_7_nts.dll |7.0|non |32-bit php7. dll|
|32-bit php_sqlsrv_7_ts.dll  <br />32-bit php_pdo_sqlsrv_7_ts.dll  |7.0|oui|32-bit php7ts. dll|
|64-bit php_sqlsrv_7_nts.dll <br />64-bit php_pdo_sqlsrv_7_nts.dll |7.0|non |64-bit php7. dll|  
|64-bit php_sqlsrv_7_ts.dll  <br />64-bit php_pdo_sqlsrv_7_ts.dll  |7.0|oui|64-bit php7ts. dll|
|32-bit php_sqlsrv_71_nts.dll<br />32-bit php_pdo_sqlsrv_71_nts.dll|7.1|non |32-bit php7. dll|  
|32-bit php_sqlsrv_71_ts.dll <br />32-bit php_pdo_sqlsrv_71_ts.dll |7.1|oui|32-bit php7ts. dll|  
|64-bit php_sqlsrv_71_nts.dll<br />64-bit php_pdo_sqlsrv_71_nts.dll|7.1|non |64-bit php7. dll|  
|64-bit php_sqlsrv_71_ts.dll <br />64-bit php_pdo_sqlsrv_71_ts.dll |7.1|oui|64-bit php7ts. dll|   
|32-bit php_sqlsrv_72_nts.dll<br />32-bit php_pdo_sqlsrv_72_nts.dll|7.2|non |32-bit php7. dll|  
|32-bit php_sqlsrv_72_ts.dll <br />32-bit php_pdo_sqlsrv_72_ts.dll |7.2|oui|32-bit php7ts. dll|  
|64-bit php_sqlsrv_72_nts.dll<br />64-bit php_pdo_sqlsrv_72_nts.dll|7.2|non |64-bit php7. dll|  
|64-bit php_sqlsrv_72_ts.dll <br />64-bit php_pdo_sqlsrv_72_ts.dll |7.2|oui|64-bit php7ts. dll|  

Sur Linux, les versions suivantes du pilote sont incluses:

|Fichier de pilote|Version de PHP|Thread-safe ?|
|---------------|:---------------:|:----------------:|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|non |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|oui|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|non |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|oui|  
|php_sqlsrv_72_nts.so<br />php_pdo_sqlsrv_72_nts.so|7.2|non |
|php_sqlsrv_72_ts.so <br />php_pdo_sqlsrv_72_ts.so |7.2|oui|

**Microsoft Drivers 5.2 for PHP for SQL Server :**  

Sur Windows, les versions suivantes du pilote sont incluses:

|Fichier de pilote|Version de PHP|Thread-safe ?|Utiliser avec .dll PHP|  
|---------------|:---------------:|:----------------:|---------------------|  
|32-bit php_sqlsrv_7_nts.dll <br />32-bit php_pdo_sqlsrv_7_nts.dll |7.0|non |32-bit php7. dll|
|32-bit php_sqlsrv_7_ts.dll  <br />32-bit php_pdo_sqlsrv_7_ts.dll  |7.0|oui|32-bit php7ts. dll|
|64-bit php_sqlsrv_7_nts.dll <br />64-bit php_pdo_sqlsrv_7_nts.dll |7.0|non |64-bit php7. dll|  
|64-bit php_sqlsrv_7_ts.dll  <br />64-bit php_pdo_sqlsrv_7_ts.dll  |7.0|oui|64-bit php7ts. dll|
|32-bit php_sqlsrv_71_nts.dll<br />32-bit php_pdo_sqlsrv_71_nts.dll|7.1|non |32-bit php7. dll|  
|32-bit php_sqlsrv_71_ts.dll <br />32-bit php_pdo_sqlsrv_71_ts.dll |7.1|oui|32-bit php7ts. dll|  
|64-bit php_sqlsrv_71_nts.dll<br />64-bit php_pdo_sqlsrv_71_nts.dll|7.1|non |64-bit php7. dll|  
|64-bit php_sqlsrv_71_ts.dll <br />64-bit php_pdo_sqlsrv_71_ts.dll |7.1|oui|64-bit php7ts. dll|   
|32-bit php_sqlsrv_72_nts.dll<br />32-bit php_pdo_sqlsrv_72_nts.dll|7.2|non |32-bit php7. dll|  
|32-bit php_sqlsrv_72_ts.dll <br />32-bit php_pdo_sqlsrv_72_ts.dll |7.2|oui|32-bit php7ts. dll|  
|64-bit php_sqlsrv_72_nts.dll<br />64-bit php_pdo_sqlsrv_72_nts.dll|7.2|non |64-bit php7. dll|  
|64-bit php_sqlsrv_72_ts.dll <br />64-bit php_pdo_sqlsrv_72_ts.dll |7.2|oui|64-bit php7ts. dll|  

Sur Linux, les versions suivantes du pilote sont incluses:

|Fichier de pilote|Version de PHP|Thread-safe ?|
|---------------|:---------------:|:----------------:|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|non |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|oui|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|non |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|oui|  
|php_sqlsrv_72_nts.so<br />php_pdo_sqlsrv_72_nts.so|7.2|non |
|php_sqlsrv_72_ts.so <br />php_pdo_sqlsrv_72_ts.so |7.2|oui|

**Microsoft Drivers 4.3 for PHP for SQL Server :**  

Sur Windows, les versions suivantes du pilote sont incluses:

|Fichier de pilote|Version de PHP|Thread-safe ?|Utiliser avec .dll PHP|  
|---------------|:---------------:|:----------------:|---------------------|  
|32-bit php_sqlsrv_7_nts.dll <br />32-bit php_pdo_sqlsrv_7_nts.dll |7.0|non |32-bit php7. dll|
|32-bit php_sqlsrv_7_ts.dll  <br />32-bit php_pdo_sqlsrv_7_ts.dll  |7.0|oui|32-bit php7ts. dll|
|64-bit php_sqlsrv_7_nts.dll <br />64-bit php_pdo_sqlsrv_7_nts.dll |7.0|non |64-bit php7. dll|  
|64-bit php_sqlsrv_7_ts.dll  <br />64-bit php_pdo_sqlsrv_7_ts.dll  |7.0|oui|64-bit php7ts. dll|
|32-bit php_sqlsrv_71_nts.dll<br />32-bit php_pdo_sqlsrv_71_nts.dll|7.1|non |32-bit php7. dll|  
|32-bit php_sqlsrv_71_ts.dll <br />32-bit php_pdo_sqlsrv_71_ts.dll |7.1|oui|32-bit php7ts. dll|  
|64-bit php_sqlsrv_71_nts.dll<br />64-bit php_pdo_sqlsrv_71_nts.dll|7.1|non |64-bit php7. dll|  
|64-bit php_sqlsrv_71_ts.dll <br />64-bit php_pdo_sqlsrv_71_ts.dll |7.1|oui|64-bit php7ts. dll|   

Sur Linux, les versions suivantes du pilote sont incluses:

|Fichier de pilote|Version de PHP|Thread-safe ?|
|---------------|:---------------:|:----------------:|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|non |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|oui|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|non |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|oui|  

**Microsoft Drivers 4.0 for PHP for SQL Server :**  

Sur Windows, les versions suivantes du pilote sont incluses:

|Fichier de pilote|Version de PHP|Thread-safe ?|Utiliser avec .dll PHP|  
|---------------|:---------------:|:----------------:|---------------------|  
|php_sqlsrv_7_nts_x86.dll<br />php_pdo_sqlsrv_7_nts_x86.dll|7.0|non|32-bit php7. dll|  
|php_sqlsrv_7_ts_x86.dll<br />php_pdo_sqlsrv_7_ts_x86.dll|7.0|oui|32-bit php7ts. dll|  
|php_sqlsrv_7_nts_x64.dll<br />php_pdo_sqlsrv_7_nts_x64.dll|7.0|non|64-bit php7. dll|  
|php_sqlsrv_7_ts_x64.dll<br />php_pdo_sqlsrv_7_ts_x64.dll|7.0|oui|64-bit php7ts. dll|   

Sur Linux, les versions suivantes du pilote sont incluses:

|Fichier de pilote|Version de PHP|Thread-safe ?|
|---------------|:---------------:|:----------------:|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|non |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|oui|

**Microsoft Drivers 3.2 for PHP for SQL Server :**  

Sur Windows, les versions suivantes du pilote sont incluses:

|Fichier de pilote|Version de PHP|Thread-safe ?|Utiliser avec .dll PHP|  
|---------------|:---------------:|:----------------:|---------------------|  
|php_sqlsrv_54_nts.dll<br />php_pdo_sqlsrv_54_nts.dll|5.4|non|php5.dll|  
|php_sqlsrv_54_ts.dll<br />php_pdo_sqlsrv_54_ts.dll|5.4|oui|php5ts.dll|  
|php_sqlsrv_55_nts.dll<br />php_pdo_sqlsrv_55_nts.dll|5.5|non|php5.dll|  
|php_sqlsrv_55_ts.dll<br />php_pdo_sqlsrv_55_ts.dll|5.5|oui|php5ts.dll|  
|php_sqlsrv_56_nts.dll<br />php_pdo_sqlsrv_56_nts.dll|5.6|non|php5.dll|  
|php_sqlsrv_56_ts.dll<br />php_pdo_sqlsrv_56_ts.dll|5.6|oui|php5ts.dll|  

**Microsoft Drivers 3.1 for PHP for SQL Server :**  

Sur Windows, les versions suivantes du pilote sont incluses:

|Fichier de pilote|Version de PHP|Thread-safe ?|Utiliser avec .dll PHP|  
|---------------|:---------------:|:----------------:|---------------------|  
|php_sqlsrv_54_nts.dll<br />php_pdo_sqlsrv_54_nts.dll|5.4|non|php5.dll|  
|php_sqlsrv_54_ts.dll<br />php_pdo_sqlsrv_54_ts.dll|5.4|oui|php5ts.dll|  
|php_sqlsrv_55_nts.dll<br />php_pdo_sqlsrv_55_nts.dll|5.5|non|php5.dll|  
|php_sqlsrv_55_ts.dll<br />php_pdo_sqlsrv_55_ts.dll|5.5|oui|php5ts.dll|  

## <a name="see-also"></a>Voir aussi  
[Bien démarrer avec les pilotes Microsoft pour PHP pour SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Guide de programmation pour les pilotes Microsoft pour PHP pour SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Informations de référence sur l’API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Référence API du pilote PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  

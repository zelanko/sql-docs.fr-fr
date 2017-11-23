---
title: "Configuration système requise pour le pilote SQL PHP | Documents Microsoft"
ms.custom: 
ms.date: 07/12/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: requirements
ms.assetid: 5db4b75f-c605-4785-9560-399a533c0fc9
caps.latest.revision: "93"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: abff6843dbf1b8f1362f10dbf2fe52fa5f686515
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="system-requirements-for-the-php-sql-driver"></a>Configuration requise pour le pilote SQL PHP
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Pour accéder aux données dans une base de données SQL Azure ou de SQL Server à l’aide de la [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], vous devez disposer des composants suivants sur votre ordinateur :  
  
-   PHP est requis. Pour plus d’informations sur la façon de télécharger et installer les derniers fichiers binaires stables, consultez [http://php.net](http://go.microsoft.com/fwlink/?LinkId=101876).  Le Microsoft Drivers for PHP for SQL Server nécessitent les versions suivantes :
  
|Version du Pilote Microsoft SQL Server pour PHP|Versions de PHP prises en charge|  
|----------------------------------------------------|--------------------------|  
|4.3|PHP 7.0 et PHP 7.1| 
|4.0|PHP 7.0|  
|3.2|PHP 5.6.4+ ou<br /><br />PHP 5.5.16+ ou<br /><br />PHP 5.4.32|  
|3.1|PHP 5.5.16+ ou<br /><br />PHP 5.4.32|  
|3|PHP 5.4.32 ou<br /><br />PHP 5.3.0|  
|2|PHP 5.3.0 ou<br /><br />PHP 5.2.4 ou<br /><br />PHP 5.2.13|  
  
-   Une version du fichier de pilote doit se trouver dans votre répertoire d’extensions PHP. Pour plus d’informations sur les différents fichiers de pilotes, consultez Versions de pilotes plus loin dans cette rubrique. Pour plus d’informations sur la configuration du pilote pour le runtime PHP, consultez [Chargement du pilote SQL PHP](../../connect/php/loading-the-php-sql-driver.md)  . Pour télécharger les pilotes, consultez [Microsoft Drivers for PHP for SQL Server](http://www.microsoft.com/download/details.aspx?id=20098).  
  
-   Un serveur web est nécessaire. Votre serveur web doit être configuré pour exécuter PHP. Pour plus d’informations sur l’hébergement des applications PHP avec les Services Internet (IIS) 6.0, consultez [Using FastCGI to Host PHP Applications on IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=117131). Pour plus d’informations sur l’hébergement d’applications PHP avec IIS 7.0, consultez [Using FastCGI to Host PHP Applications on IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=117132).  
  
    Le [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] a été testé à l’aide d’IIS 6 et IIS 7 avec FastCGI.  
  
    > [!NOTE]  
    > Microsoft prend en charge uniquement IIS.  
  
-   La version correcte du pilote Microsoft ODBC pour SQL Server ou SQL Server Native Client est requis sur l’ordinateur où s’exécute PHP.  Si vous utilisez un système d’exploitation de 64 bits, le programme d’installation ODBC 64 bits installe des pilotes ODBC 32 bits et 64 bits. Si vous utilisez un système d’exploitation 32 bits, utilisez ODBC x86 programme d’installation.

|Version du Pilote Microsoft SQL Server pour PHP|Version du pilote Microsoft ODBC pour SQL Server ou SQL Server Native Client|  
|----------------------------------------------------|--------------------------|
|4.3|Microsoft ODBC Driver 11 for SQL Server ou Microsoft ODBC Driver 13.1 for SQL Server. Pour télécharger le pilote ODBC de Microsoft, consultez le [Microsoft ODBC Driver 11 pour la page de SQL Server](http://www.microsoft.com/download/details.aspx?id=36434) ou [Microsoft ODBC Driver 13.1 pour la page de SQL Server](https://www.microsoft.com/en-us/download/details.aspx?id=53339)|    
|4.0|Microsoft ODBC Driver 11 for SQL Server ou Microsoft ODBC Driver 13 for SQL Server. Pour télécharger le pilote ODBC de Microsoft, consultez le [Microsoft ODBC Driver 11 pour la page de SQL Server](http://www.microsoft.com/download/details.aspx?id=36434) ou [Microsoft ODBC Driver 13 pour la page de SQL Server](https://www.microsoft.com/download/details.aspx?id=50420)|  
|3.2 ou <br><br> 3.1|Microsoft ODBC Driver 11 pour SQL Server. Pour télécharger le pilote ODBC de Microsoft, consultez le [Microsoft ODBC Driver 11 pour la page de SQL Server](http://www.microsoft.com/download/details.aspx?id=36434)|   
|3.0|Microsoft [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] Native Client. Vous pouvez télécharger Microsoft [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] Native Client à partir de la [page Microsoft SQL Server 2012 Feature Pack](http://go.microsoft.com/fwlink/?LinkID=236805)| 
|2.0|Microsoft [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro_md.md)] Native Client :<br /><br />[Package de téléchargement le X86](http://go.microsoft.com/fwlink/?LinkID=188400&clcid=0x409) pour les systèmes d’exploitation 32 bits <br /><br />[Package de téléchargement le X64](http://go.microsoft.com/fwlink/?LinkID=188401&clcid=0x409) pour les systèmes d’exploitation 64 bits|  

  
Si vous utilisez le pilote SQLSRV, [sqlsrv_client_info](../../connect/php/sqlsrv-client-info.md) retourne des informations sur la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Native Client ou le pilote Microsoft ODBC pour SQL Server est utilisé par le [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. Si vous utilisez le pilote PDO_SQLSRV, vous pouvez utiliser [PDO::getAttribute](../../connect/php/pdo-getattribute.md) pour découvrir la version.  



## <a name="database-versions"></a>Versions de base de données
-   Bases de données SQL Azure sont pris en charge. Pour plus d’informations, consultez [la connexion à la base de données SQL Microsoft Azure](../../connect/php/connecting-to-microsoft-azure-sql-database.md). 

- [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]version 4.3 prend en charge SQL Server 2008 R2 et versions ultérieures
- [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]prise en charge de la version 4.0 SQL Server 2008 et versions ultérieur
- [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]prise en charge de la version 3.1 SQL Server 2008 et versions ultérieur
- [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]prise en charge de la version 2.0 et 3.0 SQL Server 2005 et versions ultérieur


## <a name="driver-versions"></a>Versions de pilotes  
Cette section répertorie les pilotes qui sont incluses avec chaque version de la [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
Pour configurer le pilote à utiliser avec le runtime PHP, suivez les instructions d’installation dans [le chargement du pilote SQL PHP](../../connect/php/loading-the-php-sql-driver.md).  
  
**Pilotes Microsoft 4.3 pour PHP pour SQL Server :**  

Sous Windows, les versions suivantes du pilote sont installées pour 4.3 :
  
|Fichier de pilote|Version de PHP|Thread-safe ?|Utiliser avec .dll PHP|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_7_nts_x86.dll<br /><br />php_pdo_sqlsrv_7_nts_x86.dll|7.0|non|php7.dll de 32 bits| 
|php_sqlsrv_7_ts_x86.dll<br /><br />php_pdo_sqlsrv_7_ts_x86.dll|7.0|oui|php7ts.dll de 32 bits| 
|php_sqlsrv_7_nts_x64.dll<br /><br />php_pdo_sqlsrv_7_nts_x64.dll|7.0|non|php7.dll de 64 bits|  
|php_sqlsrv_7_ts_x64.dll<br /><br />php_pdo_sqlsrv_7_ts_x64.dll|7.0|oui|php7ts.dll de 64 bits| 
|php_sqlsrv_71_nts_x86.dll<br /><br />php_pdo_sqlsrv_71_nts_x86.dll|7.1|non|php7.dll de 32 bits|  
|php_sqlsrv_71_ts_x86.dll<br /><br />php_pdo_sqlsrv_71_ts_x86.dll|7.1|oui|php7ts.dll de 32 bits|  
|php_sqlsrv_71_nts_x64.dll<br /><br />php_pdo_sqlsrv_71_nts_x64.dll|7.1|non|php7.dll de 64 bits|  
|php_sqlsrv_71_ts_x64.dll<br /><br />php_pdo_sqlsrv_71_ts_x64.dll|7.1|oui|php7ts.dll de 64 bits|   
  
**Pilotes Microsoft 4.0 pour PHP pour SQL Server :**  

Sous Windows, les versions suivantes du pilote sont installées pour la version 4.0 :
  
|Fichier de pilote|Version de PHP|Thread-safe ?|Utiliser avec .dll PHP|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_7_nts_x86.dll<br /><br />php_pdo_sqlsrv_7_nts_x86.dll|7.0|non|php7.dll de 32 bits|  
|php_sqlsrv_7_ts_x86.dll<br /><br />php_pdo_sqlsrv_7_ts_x86.dll|7.0|oui|php7ts.dll de 32 bits|  
|php_sqlsrv_7_nts_x64.dll<br /><br />php_pdo_sqlsrv_7_nts_x64.dll|7.0|non|php7.dll de 64 bits|  
|php_sqlsrv_7_ts_x64.dll<br /><br />php_pdo_sqlsrv_7_ts_x64.dll|7.0|oui|php7ts.dll de 64 bits|   
  
Sur les versions prises en charge de Linux, la version appropriée de sqlsrv et/ou pdo_sqlsrv peut être installée à l’aide du système de package PECL de PHP. 
  
**Les Pilotes Microsoft SQL Server 3.2 pour PHP installent les versions suivantes du pilote :**  
  
|Fichier de pilote|Version de PHP|Thread-safe ?|Utiliser avec .dll PHP|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_54_nts.dll<br /><br />php_pdo_sqlsrv_54_nts.dll|5.4|non|php5.dll|  
|php_sqlsrv_54_ts.dll<br /><br />php_pdo_sqlsrv_54_ts.dll|5.4|oui|php5ts.dll|  
|php_sqlsrv_55_nts.dll<br /><br />php_pdo_sqlsrv_55_nts.dll|5.5|non|php5.dll|  
|php_sqlsrv_55_ts.dll<br /><br />php_pdo_sqlsrv_55_ts.dll|5.5|oui|php5ts.dll|  
|php_sqlsrv_56_nts.dll<br /><br />php_pdo_sqlsrv_56_nts.dll|5.6|non|php5.dll|  
|php_sqlsrv_56_ts.dll<br /><br />php_pdo_sqlsrv_56_ts.dll|5.6|oui|php5ts.dll|  
  
**Les Pilotes Microsoft SQL Server 3.1 pour PHP installent les versions suivantes du pilote :**  
  
|Fichier de pilote|Version de PHP|Thread-safe ?|Utiliser avec .dll PHP|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_54_nts.dll<br /><br />php_pdo_sqlsrv_54_nts.dll|5.4|non|php5.dll|  
|php_sqlsrv_54_ts.dll<br /><br />php_pdo_sqlsrv_54_ts.dll|5.4|oui|php5ts.dll|  
|php_sqlsrv_55_nts.dll<br /><br />php_pdo_sqlsrv_55_nts.dll|5.5|non|php5.dll|  
|php_sqlsrv_55_ts.dll<br /><br />php_pdo_sqlsrv_55_ts.dll|5.5|oui|php5ts.dll|  
  
**Les Pilotes Microsoft SQL Server 3.0 pour PHP installent les versions suivantes du pilote :**  
  
|Fichier de pilote|Version de PHP|Thread-safe ?|Utiliser avec .dll PHP|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_53_nts.dll<br /><br />php_pdo_sqlsrv_53_nts.dll|5.3|non|php5.dll|  
|php_sqlsrv_53_ts.dll<br /><br />php_pdo_sqlsrv_53_ts.dll|5.3|oui|php5ts.dll|  
|php_sqlsrv_54_nts.dll<br /><br />php_pdo_sqlsrv_54_nts.dll|5.4|non|php5.dll|  
|php_sqlsrv_54_ts.dll<br /><br />php_pdo_sqlsrv_54_ts.dll|5.4|oui|php5ts.dll|  
  
**Les Pilotes Microsoft SQL Server 2.0 pour PHP installent les versions suivantes du pilote :**  
  
|Fichier de pilote|Version de PHP|Thread-safe ?|Utiliser avec .dll PHP|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_53_nts_vc6.dll<br /><br />php_pdo_sqlsrv_53_nts_vc6.dll|5.3|non|php5.dll|  
|php_sqlsrv_53_nts_vc9.dll<br /><br />php_pdo_sqlsrv_53_nts_vc9.dll|5.3|non|php5.dll|  
|php_sqlsrv_53_ts_vc6.dll<br /><br />php_pdo_sqlsrv_53_ts_vc6.dll|5.3|oui|php5ts.dll|  
|php_sqlsrv_53_ts_vc9.dll<br /><br />php_pdo_sqlsrv_53_ts_vc9.dll|5.3|oui|php5ts.dll|  
|php_sqlsrv_52_nts_vc6.dll<br /><br />php_pdo_sqlsrv_52_nts_vc6.dll|5.2|non|php5.dll|  
|php_sqlsrv_52_ts_vc6.dll<br /><br />php_pdo_sqlsrv_52_ts_vc6.dll|5.2|oui|php5ts.dll|  
  
Si le nom du fichier de pilote contient « vc9 », il doit être utilisé avec une version de PHP compilée avec Visual C++ 9.0.  
## <a name="operating-systems"></a>Systèmes d'exploitation 
Les systèmes d’exploitation pris en charge pour les versions du pilote sont les suivantes :

-   4.3:
    -   Windows Server 2012  
    -   Windows Server 2012 R2
    -   Windows Server 2016 
    -   Windows 8  
    -   Windows 8.1   
    -   Windows 10
    -   15.10 d’Ubuntu (64 bits)
    -   Ubuntu 16.04 (64 bits)
    -   Debian 8 (64 bits)
    -   Red Hat Enterprise Linux 7 (64 bits)
    -   Mac OS Sierra (64 bits)
    -   Mac OS El Capitan (64 bits)
    
-   4.0:  
    -   Windows Server 2008 SP2
    -   Windows Server 2008 R2 SP1  
    -   Windows Server 2012  
    -   Windows Server 2012 R2  
    -   Windows Vista SP2  
    -   Windows 7 SP1  
    -   Windows 8  
    -   Windows 8.1   
    -   Windows 10 
    -   Ubuntu 15.04 (64 bits)
    -   Ubuntu 16.04 (64 bits)
    -   Red Hat Enterprise Linux 7 (64 bits)

 
-   3.2 et 3.1 :  
    -   Windows Server 2008 R2 SP1  
    -   Windows Vista SP2  
    -   Windows Server 2008 SP2  
    -   Windows 7 SP1  
    -   Windows Server 2012  
    -   Windows Server 2012 R2  
    -   Windows 8  
    -   Windows 8.1  
  
  
-   3.0:  
    -   Windows Server 2008 R2 SP1  
    -   Windows Vista SP2  
    -   Windows Server 2008 SP2  
    -   Windows 7 SP1  


-   2.0:
    -   [!INCLUDE[winxpsvr](../../includes/winxpsvr_md.md)] Service Pack 1  
    -   Windows XP Service Pack 3  
    -   Windows Vista Service Pack 1 ou version ultérieure  
    -   Windows Server 2008  
    -   Windows Server 2008 R2  
    -   Windows 7  
  
## <a name="see-also"></a>Voir aussi  
[Prise en main du pilote SQL PHP](../../connect/php/getting-started-with-the-php-sql-driver.md)
[Guide de programmation pour le pilote SQL PHP](../../connect/php/programming-guide-for-php-sql-driver.md)
[Référence d’API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
  

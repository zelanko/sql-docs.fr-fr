---
title: Configuration système requise, installation et fichiers de pilote | Microsoft Docs
ms.custom: ''
ms.date: 02/14/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d90fa182-1dab-4d6f-bd85-a04dd1479986
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a38bcb91b0a074edbf80cea1245580ba16c237af
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51600959"
---
# <a name="system-requirements-installation-and-driver-files"></a>Configuration système requise, installation et fichiers de pilote
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge les connexions à SQL Server 2014, SQL Server 2012 R2, [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssKatmai](../../../includes/sskatmai_md.md)]et [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Windows peut être installé sur un ordinateur qui possède également une ou plusieurs versions de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
ODBC Driver 13 et 13.1 pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], outre les précautions ci-dessus, prend en charge de SQL Server 2016. 

La version 17 du pilote ODBC pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge toutes celles ci-dessus et également SQL Server 2017.
  
Le nom du pilote que vous spécifiez dans une chaîne de connexion est `ODBC Driver 11 for SQL Server` ou `ODBC Driver 13 for SQL Server` (pour 13 et 13.1) ou `ODBC Driver 17 for SQL Server`.
  
## <a name="supported-operating-systems"></a>Systèmes d'exploitation pris en charge

Vous pouvez exécuter des applications avec le pilote sur les systèmes d’exploitation Windows suivants :  

-   Windows Server 2008 R2 
-   Windows Server 2012
-   Windows Server 2012 R2    
-   Windows Vista SP2 *(le pilote ODBC 11 uniquement)*  
-   Windows 7  
-   Windows 8
-   Windows 8.1
-   Windows 10
  
## <a name="installing-microsoft-odbc-driver-for-sql-server"></a>Installation de Microsoft ODBC Driver for SQL Server

Le pilote est installé lorsque vous exécutez `msodbcsql.msi` à partir d’un des liens suivants :

- [Télécharger Microsoft ODBC Driver 17 for SQL Server sur Windows](https://www.microsoft.com/download/details.aspx?id=56567)
- [Télécharger Microsoft ODBC Driver 13.1 for SQL Server sur Windows](https://www.microsoft.com/download/details.aspx?id=53339)
- [Télécharger Microsoft ODBC Driver 13 for SQL Server sur Windows](https://www.microsoft.com/download/details.aspx?id=50420)
- [Télécharger Microsoft ODBC Driver 11 for SQL Server sur Windows](https://www.microsoft.com/download/details.aspx?id=36434) 

> [!NOTE]
> Pour ceux qui pilote 17.1.0.1 ou être ci-dessous installé, il est recommandé de désinstaller manuellement avant d’installer la version la plus récente du pilote

Il peut être installé côte à côte avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  

Quand vous appelez `msodbcsql.msi`, seuls les composants clients sont installés par défaut. Les composants clients sont des fichiers qui prennent en charge l’exécution d’une application développée à l’aide du pilote. Pour installer les composants du SDK, spécifiez `ADDLOCAL=ALL` sur la ligne de commande. Exemple :  
  
```  
msiexec /i msodbcsql.msi ADDLOCAL=ALL  
```  
  
 Spécifiez `IACCEPTMSODBCSQLLICENSETERMS=YES` pour accepter les termes du contrat de licence utilisateur final, si vous utilisez l’option `/passive`, `/qn`, `/qb` ou `/qr` pour l’installation. Cette option doit être spécifiée tout en majuscules. Exemple :  
  
```  
msiexec /quiet /passive /qn /i msodbcsql.msi IACCEPTMSODBCSQLLICENSETERMS=YES ADDLOCAL=ALL  
```  
  
 Pour effectuer une désinstallation sans assistance :  
  
```  
msiexec /quiet /passive /qn /uninstall msodbcsql.msi  
```  
  
Quand une application utilise le pilote, elle doit indiquer qu’elle dépend du pilote par le biais de l’option d’installation `APPGUID`. Ainsi, le programme d’installation du pilote peut signaler les applications dépendantes avant la désinstallation. Pour spécifier une dépendance vis-à-vis du pilote, définissez le paramètre de ligne de commande `APPGUID` sur votre code de produit lors de l’installation sans assistance du pilote. (Un code de produit doit être créé si vous utilisez Microsoft Installer pour regrouper votre programme d’installation d’application.) Exemple :  
  
```  
msiexec /i msodbcsql.msi APPGUID={ <Your dependent application's APPGUID> }  
```  

## <a name="command-line-tools-sqlcmdexe-and-bcpexe"></a>Outils en ligne de commande : sqlcmd.exe et bcp.exe

Le `bcp.exe` et `sqlcmd.exe` tools pour l’utiliser avec le pilote peut être téléchargée sur [utilitaires de ligne de commande Microsoft 11 pour SQL Server](https://www.microsoft.com/download/details.aspx?id=36433), [Microsoft Command Line Utilities 13 pour SQL Server](https://www.microsoft.com/download/details.aspx?id=52680), ou [Utilitaires de ligne de commande Microsoft 13.1 pour SQL Server](https://www.microsoft.com/download/details.aspx?id=53591). Le pilote est un composant requis pour installer `sqlcmd.exe` et `bcp.exe`.
  
`bcp.exe` et `sqlcmd.exe` sont installés dans le `110\Tools` sous-dossier de `%PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC` pour la version 11, et `130\Tools` pour 13 et 13.1.

Une application qui utilise les fonctions BCP doit spécifier le pilote à partir de la même version que celle fournie avec le fichier d’en-tête et la bibliothèque utilisés pour compiler l’application.  

Par exemple, lorsque vous compilez une application ODBC avec `msodbcsql11.lib` et `msodbcsql.h`, utilisez « DRIVER = {ODBC Driver 11 for SQL Server} » dans la chaîne de connexion.

## <a name="components-of-the-microsoft-odbc-driver-for-includessnoversionincludesssnoversion-mdmd-on-windows"></a>Composants de Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Windows 
 Le pilote ODBC sur Windows contient les composants suivants :
 
|Composant|Description|  
|---------------|-----------------|  
|msodbcsql17.dll ou <br> msodbcsql13.dll ou <br> msodbcsql11.dll|Fichier DDL (Dynamic-Link Library) contenant l’ensemble des fonctionnalités du pilote. Ce fichier est installé dans % SYSTEMROOT%\System32.|  
|msodbcdiag17.dll ou <br> msodbcdiag13.dll ou <br> msodbcdiag11.dll|Le fichier de bibliothèque de liens dynamiques (DLL) qui contient l’interface de diagnostics (suivi) du pilote. Ce fichier est installé dans % SYSTEMROOT%\System32.|
|msodbcsqlr17.rll ou <br> msodbcsqlr13.rll ou <br> msodbcsqlr11.rll|Fichier de ressources qui accompagne la bibliothèque du pilote. Ce fichier est installé dans % SYSTEMROOT%\System32\1033.| 
|s13ch_msodbcsql.chm ou <br> s11ch_msodbcsql.chm |Fichier d’aide de l’Assistant Source de données qui explique comment créer une source de données pour le pilote. Ce fichier est installé dans %SYSTEMROOT%\System32\1033 <br /> <br /> **Remarque :** aucun fichier chm pour 17 du pilote ODBC. |  
|msodbcsql.h|Fichier d’en-tête qui contient toutes les nouvelles définitions nécessaires à l’utilisation du pilote.<br /><br /> **Remarque :**  vous ne pouvez pas référencer msodbcsql.h et odbcss.h dans le même programme.<br /><br /> msodbcsql.h pour ODBC Driver 17 ou 13 est installé dans %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK. <br /> msodbcsql.h pour ODBC Driver 11 est installé dans %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK.| 
|msodbcsql17.lib ou <br> msodbcsql13.lib ou <br> msodbcsql11.lib|Fichier bibliothèque nécessaire pour appeler les fonctions de l’utilitaire **bcp** qui font partie du pilote.<br /><br /> **Remarque :** Si vous référencez ce fichier bibliothèque dans votre programme, vérifiez qu’il se trouve dans votre chemin système et dans le chemin système de ceux qui utilisent l’application.<br /><br /> msodbcsql17.lib ou msodbcsql13.lib est installé dans %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK.<br /> msodbcsql11.lib est installé dans %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK.|

  
## <a name="see-also"></a> Voir aussi  
 [Pilote Microsoft ODBC pour SQL Server sur Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
  
  

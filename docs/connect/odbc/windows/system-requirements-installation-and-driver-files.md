---
title: Configuration système requise, installation et fichiers de pilote | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d90fa182-1dab-4d6f-bd85-a04dd1479986
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c8e7098cbd454b37e7de0a221c55b86194f883c3
ms.sourcegitcommit: 1c3f56deaa4c1ffbe5d7f75752ebe10447c3e7af
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71250949"
---
# <a name="system-requirements-installation-and-driver-files"></a>Configuration système requise, installation et fichiers de pilote

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Cet article décrit les pilotes ODBC qui se connectent à SQL Server.

## <a name="driver-versions"></a>Versions de pilotes

| Version du pilote | Description du support |
| :------------- | :--------------------- |
| Pilote ODBC 11 pour[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] | Prend en charge les connexions à SQL Server 2014, [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]SQL Server [!INCLUDE[ssKatmai](../../../includes/sskatmai_md.md)]2012, [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], et. |
| ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Windows | Peut être installé sur un ordinateur qui possède également une ou plusieurs versions de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. |
| Pilote ODBC 13 pour[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] | Prend en charge les connexions à SQL Server 2016, SQL Server 2014, [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]SQL Server 2012 [!INCLUDE[ssKatmai](../../../includes/sskatmai_md.md)], et. |
| Pilote ODBC 13,1 pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], <br/> Outre les éléments ci-dessus pour 13 | Prend en charge SQL Server 2017. |
| Pilote ODBC 17 pour[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] | Prend en charge les mêmes versions de base de données que 13,1. |
| ODBC Driver 17 for SQL Server | Prend en charge SQL Server 2019 à partir de la version 17,3 du pilote. |
| &nbsp; | &nbsp; |

### <a name="connection-string-details"></a>Détails de la chaîne de connexion

Le nom du pilote que vous spécifiez dans une chaîne `ODBC Driver 11 for SQL Server` de `ODBC Driver 13 for SQL Server` connexion est ou (pour 13 et 13,1 `ODBC Driver 17 for SQL Server`) ou.

## <a name="supported-operating-systems"></a>Systèmes d’exploitation pris en charge

Vous pouvez exécuter des applications avec le pilote sur les systèmes d’exploitation Windows suivants :  

- Windows Server 2008 R2
- Windows Server 2012
- Windows Server 2012 R2
- Windows Vista SP2 &nbsp; _(pilote ODBC 11 uniquement)._
- Windows 7
- Windows 8
- Windows 8.1
- Windows 10

## <a name="installing-microsoft-odbc-driver-for-sql-server"></a>Installation de Microsoft ODBC Driver for SQL Server

Le pilote est installé lorsque vous exécutez `msodbcsql.msi` à partir de l’un des liens suivants:

- [Télécharger Microsoft ODBC Driver 17 for SQL Server sur Windows](https://www.microsoft.com/download/details.aspx?id=56567)
- [Télécharger Microsoft ODBC Driver 13.1 for SQL Server sur Windows](https://www.microsoft.com/download/details.aspx?id=53339)
- [Télécharger Microsoft ODBC Driver 13 for SQL Server sur Windows](https://www.microsoft.com/download/details.aspx?id=50420)
- [Télécharger Microsoft ODBC Driver 11 for SQL Server sur Windows](https://www.microsoft.com/download/details.aspx?id=36434)

> [!NOTE]
> Pour ceux qui ont le pilote 17.1.0.1 ou une version antérieure installée, il est recommandé de le désinstaller manuellement avant d’installer la version plus récente du pilote.

### <a name="side-by-side-with-native-client"></a>Côte à côte avec Native Client

Le pilote peut être installé côte à côte avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.

Quand vous appelez `msodbcsql.msi`, seuls les composants clients sont installés par défaut. Les composants clients sont des fichiers qui prennent en charge l’exécution d’une application développée à l’aide du pilote. Pour installer les composants du SDK, spécifiez `ADDLOCAL=ALL` sur la ligne de commande. Voici un exemple.
  
```console
msiexec /i msodbcsql.msi ADDLOCAL=ALL  
```  

### <a name="end-user-license"></a>Licence utilisateur final

Spécifiez `IACCEPTMSODBCSQLLICENSETERMS=YES` pour accepter les termes de la licence utilisateur final si vous utilisez l’option `/passive`, `/qn`, `/qb` ou `/qr` pour l’installation. Cette option doit être spécifiée tout en majuscules. Voici un exemple.
  
```console
msiexec /quiet /passive /qn /i msodbcsql.msi IACCEPTMSODBCSQLLICENSETERMS=YES ADDLOCAL=ALL  
```  

### <a name="silent-uninstall"></a>Désinstallation sans assistance

L’exemple suivant montre comment effectuer une désinstallation sans assistance.
  
```console
msiexec /quiet /passive /qn /uninstall msodbcsql.msi  
```  

### <a name="indicate-dependency"></a>Indiquer une dépendance

Quand une application utilise le pilote, elle doit indiquer qu’elle dépend du pilote par le biais de l’option d’installation `APPGUID`. cette indication permet au programme d’installation du pilote de signaler les applications dépendantes avant la désinstallation. Pour spécifier une dépendance vis-à-vis du pilote, définissez le paramètre de ligne de commande `APPGUID` sur votre code de produit lors de l’installation sans assistance du pilote. Un code de produit doit être créé lors de l'utilisation de Microsoft Installer pour regrouper votre programme d'installation d'application. Voici un exemple.
  
```console
msiexec /i msodbcsql.msi APPGUID={ <Your dependent application's APPGUID> }  
```  

## <a name="command-line-tools-sqlcmdexe-and-bcpexe"></a>Outils en ligne de commande : sqlcmd.exe et bcp.exe

Les `bcp.exe` outils `sqlcmd.exe` et à utiliser avec le pilote peuvent être téléchargés à l’adresse [Microsoft utilitaires de ligne de commande 11 pour SQL Server](https://www.microsoft.com/download/details.aspx?id=36433), [Microsoft utilitaires de ligne de commande 13 pour SQL Server](https://www.microsoft.com/download/details.aspx?id=52680)ou [Microsoft utilitaires de ligne de commande 13,1 pour SQL Server](https://www.microsoft.com/download/details.aspx?id=53591). Le pilote est un composant requis pour installer `sqlcmd.exe` et `bcp.exe`.
  
`bcp.exe`et `sqlcmd.exe` sont installés dans le `110\Tools` sous-dossier `%PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC` de pour la version 11 `130\Tools` , et pour 13 et 13,1.

Une application qui utilise les fonctions BCP doit spécifier le pilote à partir de la même version que celle fournie avec le fichier d’en-tête et la bibliothèque utilisés pour compiler l’application.  

Par exemple, quand vous compilez une application `msodbcsql11.lib` ODBC `msodbcsql.h`avec et, utilisez «driver = {ODBC Driver 11 for SQL Server}» dans la chaîne de connexion.

## <a name="components-of-the-microsoft-odbc-driver-for-includessnoversionincludesssnoversion-mdmd-on-windows"></a>Composants de Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Windows

Le pilote ODBC sur Windows contient les composants suivants :

| Composant | Description |
| :-------- | :---------- |
|msodbcsql17.dll or <br/> msodbcsql13.dll ou <br/> msodbcsql11.dll|Fichier DDL (Dynamic-Link Library) contenant l’ensemble des fonctionnalités du pilote. Ce fichier est installé dans%SYSTEMROOT%\System32.|  
|msodbcdiag17. dll ou <br/> msodbcdiag13. dll ou <br/> msodbcdiag11.dll|Fichier de bibliothèque de liens dynamiques (DLL) qui contient l’interface de diagnostics (suivi) du pilote. Ce fichier est installé dans%SYSTEMROOT%\System32.|
|msodbcsqlr17. rll ou <br/> msodbcsqlr13.rll ou <br/> msodbcsqlr11.rll|Fichier de ressources qui accompagne la bibliothèque du pilote. Ce fichier est installé dans%SYSTEMROOT%\System32\1033.| 
|s13ch_msodbcsql.chm ou <br/> s11ch_msodbcsql.chm |Fichier d’aide de l’Assistant Source de données qui explique comment créer une source de données pour le pilote. Ce fichier est installé dans%SystemRoot%\system32\1033. <br /> <br /> **Remarque:** Il n’existe aucun fichier CHM pour le pilote ODBC 17. |  
|msodbcsql.h|Fichier d’en-tête qui contient toutes les nouvelles définitions nécessaires à l’utilisation du pilote.<br /><br /> **Remarque :**  vous ne pouvez pas référencer msodbcsql.h et odbcss.h dans le même programme.<br /><br /> msodbcsql.h pour ODBC Driver 17 ou 13 est installé dans %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK. <br /> msodbcsql.h pour ODBC Driver 11 est installé dans %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK.| 
|msodbcsql17.lib ou <br/> msodbcsql13.lib ou <br/> msodbcsql11.lib|Fichier bibliothèque nécessaire pour appeler les fonctions de l’utilitaire **bcp** qui font partie du pilote.<br /><br /> **Remarque :** Si vous référencez ce fichier bibliothèque dans votre programme, vérifiez qu’il se trouve dans votre chemin système et dans le chemin système de ceux qui utilisent l’application.<br /><br /> msodbcsql17.lib ou msodbcsql13.lib est installé dans %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK.<br /> msodbcsql11.lib est installé dans %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK.|
| &nbsp; | &nbsp; |

## <a name="see-also"></a>Voir aussi

[Microsoft ODBC Driver for SQL Server sur Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  

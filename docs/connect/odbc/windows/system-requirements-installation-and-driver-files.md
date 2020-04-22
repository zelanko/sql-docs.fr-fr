---
title: Configuration système requise, installation et fichiers de pilote | Microsoft Docs
description: Cet article décrit la configuration système requise pour Microsoft ODBC Driver for SQL Server.
ms.custom: ''
ms.date: 03/18/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d90fa182-1dab-4d6f-bd85-a04dd1479986
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e2b56528a369d58238a545afc20b35787003b6b1
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81484448"
---
# <a name="system-requirements-installation-and-driver-files"></a>Configuration système requise, installation et fichiers de pilote

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Cet article décrit les pilotes ODBC qui se connectent à SQL Server.

## <a name="sql-version-compatibility"></a>Compatibilité des versions de SQL

La compatibilité d’un pilote signifie qu’il a été testé sur les versions existantes de SQL au moment de sa publication. Les versions de SQL Server tentent généralement de conserver la compatibilité descendante avec les pilotes clients existants. Toutefois, les nouvelles fonctionnalités de SQL Server peuvent ne pas être disponibles avec les anciens pilotes clients.

|Version du pilote|Azure SQL Database|Azure SQL DW|Azure SQL Managed Instance|SQL Server 2019|SQL Server 2017|SQL Server 2016|SQL Server 2014|SQL Server 2012|SQL Server 2008 R2|SQL Server 2008|SQL Server 2005|
|-|-|-|-|-|-|-|-|-|-|-|-|
|17.5|O|O|O|O|O|O|O|O| | | |
|17.4|O|O|O|O|O|O|O|O| | | |
|17.3|O|O|O|O|O|O|O|O|O|O| |
|17.2|O|O|O| |O|O|O|O|O|O| |
|17.1|O|O|O| |O|O|O|O|O|O| |
|17.0|O|O|O| |O|O|O|O|O|O| |
|13.1| | | | |O|O|O|O|O|O| |
|13  | | | | | |O|O|O|O|O| |
|11  | | | | | | |O|O|O|O|O|
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

### <a name="connection-string-details"></a>Détails de la chaîne de connexion

Le nom du pilote spécifié dans une chaîne de connexion est `ODBC Driver 11 for SQL Server`, `ODBC Driver 13 for SQL Server` (pour 13 et 13.1) ou `ODBC Driver 17 for SQL Server`.

## <a name="supported-operating-systems"></a>Systèmes d’exploitation pris en charge

La matrice suivante indique la compatibilité des versions du pilote avec les différentes versions des systèmes d’exploitation Windows :

|Version du pilote|Windows Server 2019|Windows Server 2016|Windows Server 2012 R2|Windows Server 2012|Windows Server 2008 R2|Windows 10|Windows 8.1|Windows 7|Windows Vista SP2|
|-|-|-|-|-|-|-|-|-|-|
|17.5|O|O|O|O| |O|O| | |
|17.4|O|O|O|O|O|O|O|O| |
|17.3|O|O|O|O|O|O|O|O| |
|17.2| |O|O|O|O|O|O|O| |
|17.1| |O|O|O|O|O|O|O| |
|17.0| |O|O|O|O|O|O|O| |
|13.1| |O|O|O|O|O|O|O| |
|13  | | | |O|O| |O|O| |
|11  | | | |O|O| | |O|O|
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

## <a name="installing-microsoft-odbc-driver-for-sql-server"></a>Installation de Microsoft ODBC Driver for SQL Server

Le pilote est installé lorsque vous exécutez `msodbcsql.msi` à partir de l’un des liens [Téléchargements pour Windows](../download-odbc-driver-for-sql-server.md#download-for-windows).

> [!NOTE]
> Si vous possédez la version 17.1.0.1 ou une version antérieure du pilote, il est recommandé de la désinstaller manuellement avant d’installer la version plus récente.

### <a name="side-by-side-with-native-client"></a>Côte à côte avec Native Client

Le pilote peut être installé côte à côte avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Les versions principales du pilote (11, 13, 17) peuvent également être installées côte à côte.

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

### <a name="indicate-dependency"></a>Indication de la dépendance

Quand une application utilise le pilote, elle doit indiquer qu’elle dépend du pilote par le biais de l’option d’installation `APPGUID`. cette indication permet au programme d’installation du pilote de signaler les applications dépendantes avant la désinstallation. Pour spécifier une dépendance vis-à-vis du pilote, définissez le paramètre de ligne de commande `APPGUID` sur votre code de produit lors de l’installation sans assistance du pilote. Un code de produit doit être créé lors de l'utilisation de Microsoft Installer pour regrouper votre programme d'installation d'application. Voici un exemple.
  
```console
msiexec /i msodbcsql.msi APPGUID={ <Your dependent application's APPGUID> }  
```  

## <a name="command-line-tools-sqlcmdexe-and-bcpexe"></a>Outils en ligne de commande : sqlcmd.exe et bcp.exe

Les outils `bcp.exe` et `sqlcmd.exe` à utiliser avec le pilote sont téléchargeables aux emplacements suivants : [Utilitaires de ligne de commande Microsoft 11 pour SQL Server](https://www.microsoft.com/download/details.aspx?id=36433), [Utilitaires de ligne de commande Microsoft 13 pour SQL Server](https://www.microsoft.com/download/details.aspx?id=52680) et [Utilitaires de ligne de commande Microsoft 13.1 pour SQL Server](https://www.microsoft.com/download/details.aspx?id=53591). Le pilote est un composant requis pour pouvoir installer `sqlcmd.exe` et `bcp.exe`.
  
`bcp.exe` et `sqlcmd.exe` sont installés dans le sous-dossier `110\Tools` de `%PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC` pour la version 11 et `130\Tools` pour les versions 13 et 13.1.

Une application qui utilise les fonctions BCP doit spécifier le pilote à partir de la même version que celle fournie avec le fichier d’en-tête et la bibliothèque utilisés pour compiler l’application.  

Par exemple, si vous compilez une application ODBC avec `msodbcsql11.lib` et `msodbcsql.h`, indiquez « DRIVER={ODBC Driver 11 for SQL Server} » dans la chaîne de connexion.

## <a name="components-of-the-microsoft-odbc-driver-for-ssnoversion-on-windows"></a>Composants de Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Windows

Le pilote ODBC sur Windows contient les composants suivants :

| Composant | Description |
| :-------- | :---------- |
|msodbcsql17.dll or <br/> msodbcsql13.dll ou <br/> msodbcsql11.dll|Fichier DDL (Dynamic-Link Library) contenant l’ensemble des fonctionnalités du pilote. Ce fichier est installé dans %SYSTEMROOT%\System32.|  
|msodbcdiag17.dll, <br/> msodbcdiag13.dll ou <br/> msodbcdiag11.dll|Fichier bibliothèque de liens dynamiques (DLL) contenant l’interface de diagnostics (traçage) du pilote. Ce fichier est installé dans %SYSTEMROOT%\System32.|
|msodbcsqlr17.rll, <br/> msodbcsqlr13.rll ou <br/> msodbcsqlr11.rll|Fichier de ressources qui accompagne la bibliothèque du pilote. Ce fichier est installé dans %SYSTEMROOT%\System32\1033.| 
|s13ch_msodbcsql.chm ou <br/> s11ch_msodbcsql.chm |Fichier d’aide de l’Assistant Source de données qui explique comment créer une source de données pour le pilote. Ce fichier est installé dans %SYSTEMROOT%\System32\1033. <br /> <br /> **REMARQUE :** Il n’y a pas de fichier chm pour la version 17 du pilote ODBC. |  
|msodbcsql.h|Fichier d’en-tête qui contient toutes les nouvelles définitions nécessaires à l’utilisation du pilote.<br /><br /> **Remarque :**  Il n’est pas possible de faire référence à msodbcsql.h et à odbcss.h dans le même programme.<br /><br /> msodbcsql.h pour ODBC Driver 17 ou 13 est installé dans %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK. <br /> msodbcsql.h pour ODBC Driver 11 est installé dans %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK.| 
|msodbcsql17.lib ou <br/> msodbcsql13.lib ou <br/> msodbcsql11.lib|Fichier bibliothèque nécessaire pour appeler les fonctions de l’utilitaire **bcp** qui font partie du pilote.<br /><br /> **Remarque :**  Si vous faites référence à ce fichier bibliothèque dans votre programme, veillez à ce qu’il se trouve dans votre chemin système et dans celui des utilisateurs de l’application.<br /><br /> msodbcsql17.lib ou msodbcsql13.lib est installé dans %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK.<br /> msodbcsql11.lib est installé dans %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK.|
| &nbsp; | &nbsp; |

## <a name="see-also"></a>Voir aussi

[Microsoft ODBC Driver for SQL Server sur Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  

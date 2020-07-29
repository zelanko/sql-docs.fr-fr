---
title: Télécharger un pilote ODBC pour SQL Server
description: Télécharger le pilote Microsoft ODBC pour SQL Server pour développer des applications en code natif qui se connectent à SQL Server et Azure SQL Database.
ms.date: 04/24/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 53b09784-bb9d-4fd4-99d3-0492b3308ac4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 250dc0014e7ab38bf669608e9f509e273e7a9928
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86012551"
---
# <a name="download-odbc-driver-for-sql-server"></a>Télécharger un pilote ODBC pour SQL Server

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Microsoft ODBC Driver for SQL Server est une bibliothèque de liens dynamiques (DLL) unique qui prend en charge l’exécution des applications utilisant les API en code natif pour se connecter à SQL Server. Utilisez Microsoft ODBC Driver 17 for SQL Server pour créer de nouvelles applications ou améliorer des applications existantes qui doivent tirer parti des fonctionnalités plus récentes de SQL Server.

## <a name="download-for-windows"></a>Téléchargement pour Windows

Le programme d’installation redistribuable pour Microsoft ODBC Driver 17 for SQL Server installe les composants clients, qui sont nécessaires au moment de l’exécution pour tirer parti des fonctionnalités les plus récentes de SQL Server. Il installe éventuellement les fichiers d’en-tête nécessaires au développement d’une application qui utilise l’API ODBC. À partir de la version 17.4.2, le programme d’installation comprend et installe également la Bibliothèque d’authentification Microsoft Active Directory (ADAL.dll).

La version 17.5.2 est la dernière version en disponibilité générale. Si vous avez une version précédente de Microsoft ODBC Driver 17 for SQL Server installée, l’installation de la version 17.5.2 la met à niveau vers 17.5.2.

**[![Télécharger](../../ssms/media/download-icon.png) Télécharger Microsoft ODBC Driver 17 for SQL Server (x64)](https://go.microsoft.com/fwlink/?linkid=2120137)**  
**[![Télécharger](../../ssms/media/download-icon.png) Télécharger Microsoft ODBC Driver 17 for SQL Server (x86)](https://go.microsoft.com/fwlink/?linkid=2120140)**  

### <a name="version-information"></a>Informations sur la version

- Numéro de version : 17.5.2.1
- Publication : 6 mars 2020

> [!Note]
> Si vous accédez à cette page à partir d’une version autre que l’anglais et que vous souhaitez voir le contenu le plus à jour, consultez la [version anglaise (États-Unis) du site](https://aka.ms/downloadmsodbcsqlenglish). Vous pouvez télécharger différentes langues à partir du site en version anglaise (États-Unis) en sélectionnant [Langues disponibles](#available-languages).

## <a name="available-languages"></a>Langues disponibles

Cette version de Microsoft ODBC Driver for SQL Server peut être installée dans les langues suivantes :

Microsoft ODBC Driver 17.5.2 for SQL Server (x64) :  
[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2120137&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2120137&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2120137&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2120137&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2120137&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2120137&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2120137&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2120137&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2120137&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2120137&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2120137&clcid=0x40a)

Microsoft ODBC Driver 17.5.2 for SQL Server (x86) :  
[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2120140&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2120140&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2120140&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2120140&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2120140&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2120140&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2120140&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2120140&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2120140&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2120140&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2120140&clcid=0x40a)

### <a name="release-notes-for-windows"></a>Notes de publication pour Windows

Pour plus d’informations sur cette version de Windows, consultez les [notes de publication de Windows](windows\release-notes-odbc-sql-server-windows.md).

### <a name="previous-releases-for-windows"></a>Versions précédentes pour Windows

Pour télécharger les versions précédentes pour Windows, consultez [Versions précédentes de Microsoft ODBC Driver for SQL Server](windows\release-notes-odbc-sql-server-windows.md#previous-releases).

## <a name="download-for-linux-and-macos"></a>Télécharger pour Linux et macOS

Microsoft ODBC Driver for SQL Server peut être téléchargé et installé à l’aide des gestionnaires de package pour Linux et macOS en appliquant les instructions d’installation appropriées :  
[Installer ODBC for SQL Server (Linux)](linux-mac\installing-the-microsoft-odbc-driver-for-sql-server.md)  
[Installer ODBC for SQL Server (macOS)](linux-mac\install-microsoft-odbc-driver-sql-server-macos.md)  

Si vous devez télécharger les packages pour une installation hors connexion, toutes les versions sont disponibles par le biais des liens ci-dessous.

> [!Note]
> Les packages nommés `msodbcsql17-*` sont la dernière version. Les packages nommés `msodbcsql-*` sont la version 13 du pilote.

### <a name="alpine"></a>Alpine

- [17.5.2.2 Package Alpine](https://download.microsoft.com/download/e/4/e/e4e67866-dffd-428c-aac7-8d28ddafb39b/msodbcsql17_17.5.2.2-1_amd64.apk) ([Signature PGP](https://download.microsoft.com/download/e/4/e/e4e67866-dffd-428c-aac7-8d28ddafb39b/msodbcsql17_17.5.2.2-1_amd64.sig))
- [17.5.2.1 Package Alpine](https://download.microsoft.com/download/e/4/e/e4e67866-dffd-428c-aac7-8d28ddafb39b/msodbcsql17_17.5.2.1-1_amd64.apk) ([Signature PGP](https://download.microsoft.com/download/e/4/e/e4e67866-dffd-428c-aac7-8d28ddafb39b/msodbcsql17_17.5.2.1-1_amd64.sig))
- [17.5.1.1 Package Alpine](https://download.microsoft.com/download/e/4/e/e4e67866-dffd-428c-aac7-8d28ddafb39b/msodbcsql17_17.5.1.1-1_amd64.apk) ([Signature PGP](https://download.microsoft.com/download/e/4/e/e4e67866-dffd-428c-aac7-8d28ddafb39b/msodbcsql17_17.5.1.1-1_amd64.sig))

### <a name="debian"></a>Debian

- [Packages Debian 10 .deb](https://packages.microsoft.com/debian/10/prod/pool/main/m/msodbcsql17/)
- [Packages Debian 9 .deb](https://packages.microsoft.com/debian/9/prod/pool/main/m/msodbcsql17/)
- [Packages Debian 8 .deb](https://packages.microsoft.com/debian/8/prod/pool/main/m/msodbcsql17/)
- [Packages Debian 8 .deb (msodbcsql 13.x)](https://packages.microsoft.com/debian/8/prod/pool/main/m/msodbcsql/)

### <a name="redhat"></a>Red Hat

- [Packages RedHat 8. rpm](https://packages.microsoft.com/rhel/8/prod/)
- [Packages RedHat 7. rpm](https://packages.microsoft.com/rhel/7/prod/)
- [Packages RedHat 6. rpm](https://packages.microsoft.com/rhel/6/prod/)

### <a name="suse"></a>SUSE

- [Packages SuSE 15. rpm](https://packages.microsoft.com/sles/15/prod/)
- [Packages SuSE 12. rpm](https://packages.microsoft.com/sles/12/prod/)
- [Packages SuSE 11. rpm](https://packages.microsoft.com/sles/11/prod/)

### <a name="ubuntu"></a>Ubuntu

- [Packages Ubuntu 19.10 .deb](https://packages.microsoft.com/ubuntu/19.10/prod/pool/main/m/msodbcsql17/)
- [Packages Ubuntu 18.04 .deb](https://packages.microsoft.com/ubuntu/18.04/prod/pool/main/m/msodbcsql17/)
- [Packages Ubuntu 16.04 .deb](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql17/)
- [Packages Ubuntu 14.04 .deb](https://packages.microsoft.com/ubuntu/14.04/prod/pool/main/m/msodbcsql17/)
- [Packages Ubuntu 16.04 .deb (msodbcsql 13.x)](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql/)
- [Packages Ubuntu 14.04 .deb (msodbcsql 13.x)](https://packages.microsoft.com/ubuntu/14.04/prod/pool/main/m/msodbcsql/)

Consultez également [Installation du pilote Linux](linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="macos"></a>macOS

- Pour plus d’informations, consultez [Homebrew formulae](https://github.com/Microsoft/homebrew-mssql-release).

Consultez également [Installation du pilote macOS](linux-mac/install-microsoft-odbc-driver-sql-server-macos.md).

### <a name="older-linux-releases"></a>Versions antérieures de Linux

- **Red Hat Enterprise Linux 5 et 6 (64 bits)**  - [Télécharger Microsoft ODBC Driver 11 for SQL Server - Red Hat Linux](https://go.microsoft.com/fwlink/?LinkId=267321)  
- **SUSE Linux Enterprise 11 Service Pack 2 (64 bits)**  - [Télécharger Microsoft ODBC Driver 11 Preview for SQL Server - SUSE Linux](https://go.microsoft.com/fwlink/?LinkId=264916)

### <a name="release-notes-for-linux-and-macos"></a>Notes de publication pour Linux et macOS

Pour plus d’informations sur les mises en production pour Linux et macOS, consultez les [notes de publication de Linux et macOS](linux-mac\release-notes-odbc-sql-server-linux-mac.md).

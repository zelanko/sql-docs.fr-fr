---
title: Téléchargez et installez sqlpackage | Microsoft Docs
description: Téléchargez et installez sqlpackage pour Windows, macOS ou Linux
ms.custom: tools|sos
ms.date: 06/18/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sqlpackage
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
manager: craigg
ms.openlocfilehash: fa682766fe4330a34cff39600b6296403031a3e4
ms.sourcegitcommit: 0dff9dd43e80eee900eb92d25df9ca18397f3485
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37080037"
---
# <a name="download-and-install-sqlpackage"></a>Téléchargez et installez sqlpackage

Sqlpackage s’exécute sur Windows, macOS et Linux.

Téléchargez et installez la dernière version de .NET Framework et de macOS et de versions préliminaires de Linux :

|Plateforme|Télécharger|Date de publication|Options de version|Build|
|:---|:---|:---|:---|:---|
|Windows|[Programme d’installation](https://go.microsoft.com/fwlink/?linkid=875508)|22 juin 2018.|17.8|14.0.4079.2|
|Mac OS (version préliminaire)|[.zip](https://go.microsoft.com/fwlink/?linkid=873927)|9 mai 2018 |0.0.1|15.0.4057.1|
|Linux (préversion)|[.zip](https://go.microsoft.com/fwlink/?linkid=873926)|9 mai 2018 |0.0.1|15.0.4057.1|

Pour plus d’informations sur la dernière version, consultez le [notes de version](sqlpackage-release-notes.md).

## <a name="get-sqlpackage-for-windows"></a>Obtenir sqlpackage pour Windows

Cette version de sqlpackage comprend une expérience de programme d’installation Windows standard et un fichier zip : 

1. Téléchargez et exécutez le [DacFramework.msi programme d’installation Windows](https://go.microsoft.com/fwlink/?linkid=875508).
2. Ouvrez une nouvelle fenêtre d’invite de commandes et exécutez sqlpackage.exe
    - Sqlpackage est installé dans le ```C:\Program Files\Microsoft SQL Server\140\DAC\bin``` dossier

## <a name="get-sqlpackage-preview-for-macos"></a>Obtenir sqlpackage (version préliminaire) pour macOS

1. Télécharger [sqlpackage pour macOS](https://go.microsoft.com/fwlink/?linkid=873927).
2. Pour extraire le fichier et lancer sqlpackage, ouvrez une nouvelle fenêtre de Terminal et tapez les commandes suivantes :

   **Installation de fichier .zip :**

   ```bash
   mv ~/Downloads/sqlpackage-linux-<version string> ~/sqlpackage 
   echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bash_profile
   source ~/.bash_profile
   sqlpackage
   ```

## <a name="get-sqlpackage-preview-for-linux"></a>Obtenir sqlpackage (version préliminaire) pour Linux

1. Télécharger [sqlpackage pour Linux](https://go.microsoft.com/fwlink/?linkid=873926) à l’aide d’un des programmes d’installation ou de l’archive tar.gz :
2. Pour extraire le fichier et lancer sqlpackage, ouvrez une nouvelle fenêtre de Terminal et tapez les commandes suivantes :

   **Installation de fichier .zip :**

   ```bash
   cd ~
   mkdir sqlpackage
   unzip ~/Downloads/sqlpackage-linux-<version string>.zip ~/sqlpackage 
   echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bashrc
   source ~/.bashrc
   sqlpackage
   ```

   > [!NOTE]
   > Sur Ubuntu, Red Hat et Debian, vous pouvez avoir de dépendances manquantes. Utilisez les commandes suivantes pour installer ces dépendances selon votre version de Linux :

   **Debian :**

   ```bash
   sudo apt-get install libuwind8
   ```

   **Redhat :**

   ```bash
   yum install libunwind
   yum install libicu
   ```

   **Ubuntu :**

   ```bash
   sudo apt-get install libunwind8

   # install the libicu library based on the Ubuntu version
   sudo apt-get install libicu52      # for 14.x
   sudo apt-get install libicu55      # for 16.x
   sudo apt-get install libicu57      # for 17.x
   sudo apt-get install libicu60      # for 18.x
   ```

## <a name="uninstall-sqlpackage-preview"></a>Désinstaller sqlpackage (version préliminaire)

Si vous avez installé sqlpackage à l’aide du programme d’installation de Windows, puis désinstallez la même manière que n’importe quelle application Windows.

Si vous avez installé sqlpackage avec un fichier ZIP ou autres archive, supprimez simplement les fichiers.

## <a name="supported-operating-systems"></a>Systèmes d'exploitation pris en charge

Sqlpackage s’exécute sur Windows, macOS et Linux et est pris en charge sur les plateformes suivantes :

### <a name="windows"></a>Windows

- Windows 10
- Windows 8.1
- Windows 8
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2012
- Windows Server 2008 R2

### <a name="macos"></a>macOS

- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux-x64"></a>Linux (x64)

- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="next-steps"></a>Next Steps

- En savoir plus sur [sqlpackage](sqlpackage.md)

[Déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
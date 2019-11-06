---
title: Télécharger et installer sqlpackage | Microsoft Docs
description: Télécharger et installer sqlpackage pour Windows, macOS ou Linux
ms.custom: tools|sos
ms.date: 06/20/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
ms.openlocfilehash: f966de4951e5c90dac8d6e48f00f8de6ff067e3c
ms.sourcegitcommit: 82b70c39550402a2b0b327db32bf5ecf88b50d3c
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73033010"
---
# <a name="download-and-install-sqlpackage"></a>Télécharger et installer sqlpackage

sqlpackage s’exécute sur Windows, macOS et Linux.

Téléchargez et installez la dernière version de .NET Framework et les versions préliminaires de macOS et de Linux :

|Plateforme|Télécharger|Date de publication|Options de version|Build
|:---|:---|:---|:---|:---|
|Windows (x64)|[Programme d’installation MSI](https://go.microsoft.com/fwlink/?linkid=2108813)|29 octobre 2019|18.4|15.0.4573.2|
|macOS .NET Core (x64)|[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2108815)|29 octobre 2019| 18.4|15.0.4573.2|
|Linux .NET Core (x64) |[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2108814)|29 octobre 2019| 18.4|15.0.4573.2|
|Windows .NET Core (x64) |[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2109019)|29 octobre 2019| 18.4|15.0.4573.2|

Pour plus d’informations sur la dernière version, consultez les [notes de publication](release-notes-sqlpackage.md). Pour télécharger des langues supplémentaires, consultez la section [langues disponibles](#available-languages) .

[!INCLUDE[Freshness](../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="get-sqlpackage-for-windows"></a>Obtenir sqlpackage pour Windows

Cette version de sqlpackage comprend une expérience du programme d’installation Windows standard et un fichier .zip : 

1. Téléchargez et exécutez le [programme d’installation DacFramework.msi pour Windows](https://go.microsoft.com/fwlink/?linkid=2108813).
2. Ouvrez une nouvelle fenêtre d’invite de commandes et exécutez sqlpackage.exe
    - sqlpackage est installé dans le dossier ```C:\Program Files\Microsoft SQL Server\150\DAC\bin```

## <a name="get-sqlpackage-net-core-for-windows"></a>Obtenir SqlPackage .NET Core pour Windows

1. Télécharger [sqlpackage pour Windows](https://go.microsoft.com/fwlink/?linkid=2109019).
2. Pour extraire le fichier en cliquant avec le bouton droit sur le fichier dans l’Explorateur Windows, puis en sélectionnant l’option « extraire tout... », sélectionnez le répertoire cible.
3. Ouvrez une nouvelle fenêtre de terminal et un CD-ROM à l’emplacement où SqlPackage a été extrait :

   ```cmd
   > sqlpackage
   ```

## <a name="get-sqlpackage-net-core-for-macos"></a>Obtenir SqlPackage .NET Core pour macOS

1. Téléchargez [sqlpackage pour macOS](https://go.microsoft.com/fwlink/?linkid=2108815).
2. Pour extraire le fichier et lancer sqlpackage, ouvrez une nouvelle fenêtre de Terminal et tapez les commandes suivantes :

   ```bash
   $ mkdir sqlpackage
   $ unzip ~/Downloads/sqlpackage-osx-<version string>.zip ~/sqlpackage 
   $ echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bash_profile
   $ source ~/.bash_profile
   $ sqlpackage
   ```

## <a name="get-sqlpackage-net-core-for-linux"></a>Obtenir SqlPackage .NET Core pour Linux

1. Téléchargez [sqlpackage pour Linux](https://go.microsoft.com/fwlink/?linkid=2108814) à l’aide d’un des programmes d’installation ou de l’archive tar.gz :
2. Pour extraire le fichier et lancer sqlpackage, ouvrez une nouvelle fenêtre de Terminal et tapez les commandes suivantes :

   ```bash
   cd ~
   $ mkdir sqlpackage
   $ unzip ~/Downloads/sqlpackage-linux-<version string>.zip -d ~/sqlpackage 
   $ echo "export PATH=\"\$PATH:$HOME/sqlpackage\"" >> ~/.bashrc
   $ chmod a+x ~/sqlpackage/sqlpackage
   $ source ~/.bashrc
   $ sqlpackage
   ```

   > [!NOTE]
   > Sur Debian, Red Hat et Ubuntu, vous pouvez avoir des dépendances manquantes. Utilisez les commandes suivantes pour installer ces dépendances selon votre version de Linux :

   **Debian :**

   ```bash
   $ sudo apt-get install libunwind8
   ```

   **Redhat :**

   ```bash
   $ yum install libunwind
   $ yum install libicu
   ```

   **Ubuntu :**

   ```bash
   $ sudo apt-get install libunwind8

   # install the libicu library based on the Ubuntu version
   $ sudo apt-get install libicu52      # for 14.x
   $ sudo apt-get install libicu55      # for 16.x
   $ sudo apt-get install libicu57      # for 17.x
   $ sudo apt-get install libicu60      # for 18.x
   ```

## <a name="uninstall-sqlpackage-preview"></a>Désinstaller sqlpackage (préversion)

Si vous avez installé sqlpackage à l’aide du programme d’installation Windows, alors désinstallez-le de la même manière que n’importe quelle application Windows.

Si vous avez installé sqlpackage avec un fichier .zip ou une autre archive, supprimez les fichiers.

## <a name="supported-operating-systems"></a>Systèmes d'exploitation pris en charge

sqlpackage s’exécute sur Windows, macOS et Linux et est pris en charge sur les plateformes suivantes :

### <a name="windows"></a>Windows

- Windows 10
- Windows 8.1
- Windows 7 SP1
- Windows Server 2008 R2
- Windows Server 2012 R2
- Windows Server 2016

### <a name="macos"></a>macOS

- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux-x64"></a>Linux (x64)

- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="available-languages"></a>Langues disponibles

Vous pouvez installer cette version de sqlpackage dans les langues suivantes :

SqlPackage Windows :  
[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2108813&clcid=0x40a)

SqlPackage Windows .NET Core :  
[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2109019&clcid=0x40a)

SqlPackage .NET Core macOS :  
[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2108815&clcid=0x40a)

SqlPackage .NET Core Linux :  
[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2108814&clcid=0x40a)

## <a name="next-steps"></a>Next Steps

- En savoir plus sur [sqlpackage](sqlpackage.md)

[Déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)

---
title: Télécharger et installer sqlpackage
description: Télécharger et installer sqlpackage pour Windows, macOS ou Linux
ms.custom: tools|sos
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
ms.reviewer: alayu; sstein
ms.date: 06/20/2018
ms.openlocfilehash: 6490dd15619c315288be6a094ceb26e68c0179d1
ms.sourcegitcommit: b8933ce09d0e631d1183a84d2c2ad3dfd0602180
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83151538"
---
# <a name="download-and-install-sqlpackage"></a>Télécharger et installer sqlpackage

sqlpackage s’exécute sur Windows, macOS et Linux.

Téléchargez et installez la dernière version de .NET Framework et les versions préliminaires de macOS et de Linux :

|Plateforme|Téléchargement|Date de publication|Version|Build
|:---|:---|:---|:---|:---|
| Windows|[Programme d’installation MSI](https://go.microsoft.com/fwlink/?linkid=2128142)|28 avril 2020|18.5|15.0.4769.1|
|macOS .NET Core |[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2128145)|28 avril 2020| 18.5|15.0.4769.1|
|Linux .NET Core |[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2128144)|28 avril 2020| 18.5|15.0.4769.1|
|Windows .NET Core |[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2128143)|28 avril 2020| 18.5|15.0.4769.1|

Pour plus d’informations sur la dernière version, consultez les [notes de publication](release-notes-sqlpackage.md). Pour télécharger des langues supplémentaires, consultez la section [Langues disponibles](#available-languages).

[!INCLUDE[Freshness](../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="get-sqlpackage-for-windows"></a>Obtenir sqlpackage pour Windows

Cette version de sqlpackage comprend une expérience du programme d’installation Windows standard et un fichier .zip : 

1. Téléchargez et exécutez le [programme d’installation DacFramework.msi pour Windows](https://go.microsoft.com/fwlink/?linkid=2128142).
2. Ouvrez une nouvelle fenêtre d’invite de commandes et exécutez sqlpackage.exe
    - sqlpackage est installé dans le dossier ```C:\Program Files\Microsoft SQL Server\150\DAC\bin```

## <a name="get-sqlpackage-net-core-for-windows"></a>Obtenir le sqlpackage .NET Core pour Windows

1. Télécharger [sqlpackage pour Windows](https://go.microsoft.com/fwlink/?linkid=2128143).
2. Pour extraire le fichier, cliquez avec le bouton droit sur le fichier dans l’Explorateur Windows, puis sélectionnez l’option « Extraire tout... » et sélectionnez le répertoire cible.
3. Ouvrez une nouvelle fenêtre de terminal et exécutez une commande cd sur l’emplacement où sqlpackage a été extrait :

   ```cmd
   > sqlpackage
   ```

## <a name="get-sqlpackage-net-core-for-macos"></a>Obtenir le sqlpackage .NET Core pour macOS

1. Téléchargez [sqlpackage pour macOS](https://go.microsoft.com/fwlink/?linkid=2128145).
2. Pour extraire le fichier et lancer sqlpackage, ouvrez une nouvelle fenêtre de Terminal et tapez les commandes suivantes :

   ```bash
   $ mkdir sqlpackage
   $ unzip ~/Downloads/sqlpackage-osx-<version string>.zip -d ~/sqlpackage 
   $ echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bash_profile
   $ source ~/.bash_profile
   $ sqlpackage
   ```

## <a name="get-sqlpackage-net-core-for-linux"></a>Obtenir le sqlpackage .NET Core pour Linux

1. Téléchargez [sqlpackage pour Linux](https://go.microsoft.com/fwlink/?linkid=2128144) à l’aide d’un des programmes d’installation ou de l’archive tar.gz :
2. Pour extraire le fichier et lancer sqlpackage, ouvrez une nouvelle fenêtre de Terminal et tapez les commandes suivantes :

   ```bash
   $ cd ~
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

## <a name="supported-operating-systems"></a>Systèmes d’exploitation pris en charge

sqlpackage s’exécute sur Windows, macOS et Linux et est pris en charge sur les plateformes suivantes :

### <a name="windows"></a> Windows

- Windows 10
- Windows 8.1
- Windows 7 SP1
- Windows Server 2008 R2
- Windows Server 2012 R2
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

sqlpackage Windows :  
[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2128142&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2128142&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2128142&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2128142&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2128142&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2128142&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2128142&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2128142&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2128142&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2128142&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2128142&clcid=0x40a)

sqlpackage .NET Core Windows :  
[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2128143&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2128143&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2128143&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2128143&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2128143&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2128143&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2128143&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2128143&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2128143&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2128143&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2128143&clcid=0x40a)

sqlpackage .NET Core macOS :  
[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2128145&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2128145&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2128145&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2128145&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2128145&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2128145&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2128145&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2128145&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2128145&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2128145&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2128145&clcid=0x40a)

sqlpackage .NET Core Linux :  
[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2128144&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2128144&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2128144&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2128144&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2128144&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2128144&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2128144&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2128144&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2128144&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2128144&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2128144&clcid=0x40a)

## <a name="next-steps"></a>Étapes suivantes

- En savoir plus sur [sqlpackage](sqlpackage.md)

[Déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)

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
ms.openlocfilehash: d8422146e3569ff991ef16179e54f0f78961fc79
ms.sourcegitcommit: 6413b7495313830ad1ae5aefe0c09e8e7a284b07
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71016868"
---
# <a name="download-and-install-sqlpackage"></a>Télécharger et installer sqlpackage

sqlpackage s’exécute sur Windows, macOS et Linux.

Téléchargez et installez la dernière version de .NET Framework et les versions préliminaires de macOS et de Linux :

|Plateforme|Télécharger|Date de publication|Options de version|Build
|:---|:---|:---|:---|:---|
|Windows|[Programme d’installation MSI](https://go.microsoft.com/fwlink/?linkid=2102893)|13 septembre 2019|18.3.1|15.0.4538.1|
|macOS .NET Core (préversion)|[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2102894)|13 septembre 2019| 18.3.1|15.0.4538.1|
|Linux .NET Core (préversion)|[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2102978)|13 septembre 2019| 18.3.1|15.0.4538.1|
|Windows .NET Core (version préliminaire)|[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2102979)|13 septembre 2019| 18.3.1|15.0.4538.1|

Pour plus d’informations sur la dernière version, consultez les [notes de publication](release-notes-sqlpackage.md).

[!INCLUDE[Freshness](../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="get-sqlpackage-for-windows"></a>Obtenir sqlpackage pour Windows

Cette version de sqlpackage comprend une expérience du programme d’installation Windows standard et un fichier .zip : 

1. Téléchargez et exécutez le [programme d’installation DacFramework.msi pour Windows](https://go.microsoft.com/fwlink/?linkid=2102893).
2. Ouvrez une nouvelle fenêtre d’invite de commandes et exécutez sqlpackage.exe
    - sqlpackage est installé dans le dossier ```C:\Program Files\Microsoft SQL Server\150\DAC\bin```
    - En cas d’installation de la version x86 sur un ordinateur x64, sqlpackage est installé dans le dossier ```C:\Program Files (x86)\Microsoft SQL Server\150\DAC\bin```

## <a name="get-sqlpackage-net-core-preview-for-windows"></a>Obtenir SqlPackage .NET Core (version préliminaire) pour Windows

1. Télécharger [sqlpackage pour Windows](https://go.microsoft.com/fwlink/?linkid=2102979).
2. Pour extraire le fichier en cliquant avec le bouton droit sur le fichier dans l’Explorateur Windows, puis en sélectionnant l’option « extraire tout... », sélectionnez le répertoire cible.
3. Ouvrez une nouvelle fenêtre de terminal et un CD-ROM à l’emplacement où SqlPackage a été extrait :

   **Installation de fichier .zip :**

   ```bash
   sqlpackage
   ```

## <a name="get-sqlpackage-net-core-preview-for-macos"></a>Obtenir SqlPackage .NET Core (version préliminaire) pour macOS

1. Téléchargez [sqlpackage pour macOS](https://go.microsoft.com/fwlink/?linkid=2102894).
2. Pour extraire le fichier et lancer sqlpackage, ouvrez une nouvelle fenêtre de Terminal et tapez les commandes suivantes :

   **Installation de fichier .zip :**

   ```bash
   mkdir sqlpackage
   unzip ~/Downloads/sqlpackage-osx-<version string>.zip ~/sqlpackage 
   echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bash_profile
   source ~/.bash_profile
   sqlpackage
   ```

## <a name="get-sqlpackage-net-core-preview-for-linux"></a>Obtenir SqlPackage .NET Core (version préliminaire) pour Linux

1. Téléchargez [sqlpackage pour Linux](https://go.microsoft.com/fwlink/?linkid=2102978) à l’aide d’un des programmes d’installation ou de l’archive tar.gz :
2. Pour extraire le fichier et lancer sqlpackage, ouvrez une nouvelle fenêtre de Terminal et tapez les commandes suivantes :

   **Installation de fichier .zip :**

   ```bash
   cd ~
   mkdir sqlpackage
   unzip ~/Downloads/sqlpackage-linux-<version string>.zip -d ~/sqlpackage 
   echo "export PATH=\"\$PATH:$HOME/sqlpackage\"" >> ~/.bashrc
   chmod a+x ~/sqlpackage/sqlpackage
   source ~/.bashrc
   sqlpackage
   ```

   > [!NOTE]
   > Sur Debian, Red Hat et Ubuntu, vous pouvez avoir des dépendances manquantes. Utilisez les commandes suivantes pour installer ces dépendances selon votre version de Linux :

   **Debian :**

   ```bash
   sudo apt-get install libunwind8
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

## <a name="uninstall-sqlpackage-preview"></a>Désinstaller sqlpackage (préversion)

Si vous avez installé sqlpackage à l’aide du programme d’installation Windows, alors désinstallez-le de la même manière que n’importe quelle application Windows.

Si vous avez installé sqlpackage avec un fichier .zip ou une archive, supprimez simplement les fichiers.

## <a name="supported-operating-systems"></a>Systèmes d'exploitation pris en charge

sqlpackage s’exécute sur Windows, macOS et Linux et est pris en charge sur les plateformes suivantes :

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

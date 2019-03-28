---
title: Téléchargez et installez sqlpackage | Microsoft Docs
description: Téléchargez et installez sqlpackage pour Windows, macOS ou Linux
ms.custom: tools|sos
ms.date: 06/19/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
manager: craigg
ms.openlocfilehash: 5a45803f4ce2a91962a5bba824a468ca436f7839
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58527211"
---
# <a name="download-and-install-sqlpackage"></a>Téléchargez et installez sqlpackage

Sqlpackage s’exécute sur Windows, macOS et Linux.

Téléchargez et installez la dernière version de .NET Framework et de macOS et de versions préliminaires de Linux :

|Plateforme|Télécharger|Date de publication|Options de version|Build
|:---|:---|:---|:---|:---|
|Windows|[Programme d’installation MSI](https://go.microsoft.com/fwlink/?linkid=2069405)|1er février 2019|18.1|15.0.4316.1|
|macOS .NET Core (version préliminaire)|[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2069126)|1er février 2019 | 18.1 |15.0.4316.1|
|Linux .NET Core (version préliminaire)|[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2069122)|1er février 2019 | 18.1 |15.0.4316.1|

Pour plus d’informations sur la dernière version, consultez le [notes de version](release-notes-sqlpackage.md).

## <a name="get-sqlpackage-for-windows"></a>Obtenir sqlpackage pour Windows

Cette version de sqlpackage comprend une expérience de programme d’installation Windows standard et un fichier zip : 

1. Téléchargez et exécutez le [DacFramework.msi programme d’installation Windows](https://go.microsoft.com/fwlink/?linkid=2069405).
2. Ouvrez une nouvelle fenêtre d’invite de commandes et exécutez sqlpackage.exe
    - Sqlpackage est installé dans le ```C:\Program Files\Microsoft SQL Server\150\DAC\bin``` dossier
    - L’installation de le x86 version sur un x64 machine, sqlpackage est installé dans le ```C:\Program Files (x86)\Microsoft SQL Server\150\DAC\bin``` dossier

## <a name="get-sqlpackage-preview-for-macos"></a>Obtenir sqlpackage (version préliminaire) pour macOS

1. Télécharger [sqlpackage pour macOS](https://go.microsoft.com/fwlink/?linkid=2069126).
2. Pour extraire le fichier et lancer sqlpackage, ouvrez une nouvelle fenêtre de Terminal et tapez les commandes suivantes :

   **Installation de fichier .zip :**

   ```bash
   mkdir sqlpackage
   unzip ~/Downloads/sqlpackage-osx-<version string>.zip ~/sqlpackage 
   echo 'export PATH="$PATH:~/sqlpackage"' >> ~/.bash_profile
   source ~/.bash_profile
   sqlpackage
   ```

## <a name="get-sqlpackage-preview-for-linux"></a>Obtenir sqlpackage (version préliminaire) pour Linux

1. Télécharger [sqlpackage pour Linux](https://go.microsoft.com/fwlink/?linkid=2069122) à l’aide d’un des programmes d’installation ou de l’archive tar.gz :
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
   > Sur Ubuntu, Red Hat et Debian, vous pouvez avoir de dépendances manquantes. Utilisez les commandes suivantes pour installer ces dépendances selon votre version de Linux :

   **Debian :**

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

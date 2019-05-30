---
title: Installer les outils de ligne de SQL Server sur Linux
titleSuffix: SQL Server
description: Cet article décrit comment installer les outils SQL Server sur Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 05/28/2019
ms.topic: conceptual
ms.prod: sql
ms.custom: sqlfreshmay19
ms.technology: linux
ms.assetid: eff8e226-185f-46d4-a3e3-e18b7a439e63
ms.openlocfilehash: 86a452237628df8952beaa09277a79b1de507aa1
ms.sourcegitcommit: 02df4e7965b2a858030bb508eaf8daa9bc10b00b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66265401"
---
# <a name="install-sqlcmd-and-bcp-the-sql-server-command-line-tools-on-linux"></a>Installer sqlcmd et bcp les outils de ligne de commande de SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Les étapes suivantes installent les outils de ligne de commande, les pilotes ODBC de Microsoft et leurs dépendances. Le package **mssql-tools** contient :

- **SQLCMD**: Utilitaire de ligne de commande de requête.
- **bcp**: Utilitaire d’importation / exportation en bloc.

Installer les outils pour votre plateforme :

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)
- [macOS](#macos)
- [Docker](#docker)

Cet article décrit comment installer les outils de ligne de commande. Si vous recherchez des exemples montrant comment utiliser **sqlcmd** ou **bcp**, consultez le [liens](#next-steps) à la fin de cette rubrique.

## <a name="a-idrhelainstall-tools-on-rhel-7"></a><a id="RHEL"><a/>Installer les outils sur RHEL 7

Utilisez les étapes suivantes pour installer le package **mssql-tools** sur Red Hat Enterprise Linux.  

1. Activer le mode Super utilisateur.

   ```bash
   sudo su
   ```

1. Téléchargez le fichier de configuration du référentiel Microsoft Red Hat.

   ```bash
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/msprod.repo
   ```

1. Quittez le mode Super utilisateur.

   ```bash
   exit
   ```

1. Si vous aviez une version précédente de **mssql-tools** installée, supprimez tous les packages unixODBC plus anciens.

   ```bash
   sudo yum remove mssql-tools unixODBC-utf16-devel
   ```

1. Exécutez les commandes suivantes pour installer **mssql-tools** avec le package développeur unixODBC.

   ```bash
   sudo yum install mssql-tools unixODBC-devel
   ```

   > [!Note] 
   > Pour mettre à jour vers la dernière version de **mssql-tools** exécutez les commandes suivantes :
   >    ```bash
   >   sudo yum check-update
   >   sudo yum update mssql-tools
   >   ```

1. **Facultatif**: Ajouter `/opt/mssql-tools/bin/` à votre **chemin d’accès** variable d’environnement dans un interpréteur de commandes bash.

   Pour rendre **sqlcmd et bcp** accessible à partir de l’interpréteur de commandes pour les sessions de connexion, modifiez votre **chemin d’accès** dans le fichier **~/.bash_profile**  avec la commande suivante :

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Pour rendre **sqlcmd/bcp** accessible à partir de l’interface de l’interpréteur de commandes pour les sessions interactives/de non-connexion, modifiez le **chemin d’accès** dans le fichier **~/.bashrc** avec la commande suivante :

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="ubuntu"></a>Installer les outils sur Ubuntu 16.04

Utilisez les étapes suivantes pour installer le package **mssql-tools** sur Ubuntu.  

1. Importez les clés publiques GPG de référentiel.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Inscrire le référentiel Microsoft Ubuntu.

   ```bash
   curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/msprod.list
   ```

1. Mettre à jour la liste de sources et exécutez la commande d’installation avec le package de développeur unixODBC.

   ```bash
   sudo apt-get update 
   sudo apt-get install mssql-tools unixodbc-dev
   ```

   > [!Note] 
   > Pour mettre à jour vers la dernière version de **mssql-tools** exécutez les commandes suivantes :
   >    ```bash
   >   sudo apt-get update 
   >   sudo apt-get install mssql-tools 
   >   ```

1. **Facultatif**: Ajouter `/opt/mssql-tools/bin/` à votre **chemin d’accès** variable d’environnement dans un interpréteur de commandes bash.

   Pour rendre **sqlcmd et bcp** accessible à partir de l’interpréteur de commandes pour les sessions de connexion, modifiez votre **chemin d’accès** dans le fichier **~/.bash_profile**  avec la commande suivante :

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Pour rendre **sqlcmd/bcp** accessible à partir de l’interface de l’interpréteur de commandes pour les sessions interactives/de non-connexion, modifiez le **chemin d’accès** dans le fichier **~/.bashrc** avec la commande suivante :

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="SLES"></a>Installer les outils sur SLES 12

Utilisez les étapes suivantes pour installer le package **mssql-tools** sur SUSE Linux Enterprise Server.  

1. Ajouter le référentiel Microsoft SQL Server à Zypper.

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo 
   sudo zypper --gpg-auto-import-keys refresh
   ```

1. Installer **mssql-tools** avec le package de développeur unixODBC.

   ```bash
   sudo zypper install mssql-tools unixODBC-devel
   ```

   > [!Note] 
   > Pour mettre à jour vers la dernière version de **mssql-tools** exécutez les commandes suivantes :
   >    ```bash
   >   sudo zypper refresh
   >   sudo zypper update mssql-tools
   >   ```

1. **Facultatif**: Ajouter `/opt/mssql-tools/bin/` à votre **chemin d’accès** variable d’environnement dans un interpréteur de commandes bash.

   Pour rendre **sqlcmd et bcp** accessible à partir de l’interpréteur de commandes pour les sessions de connexion, modifiez votre **chemin d’accès** dans le fichier **~/.bash_profile**  avec la commande suivante :

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Pour rendre **sqlcmd/bcp** accessible à partir de l’interface de l’interpréteur de commandes pour les sessions interactives/de non-connexion, modifiez le **chemin d’accès** dans le fichier **~/.bashrc** avec la commande suivante :

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="macos"></a> Installer les outils sur macOS

Un aperçu de **sqlcmd** et **bcp** est maintenant disponible sur macOS. Pour plus d’informations, consultez l'[annonce](https://blogs.technet.microsoft.com/dataplatforminsider/2017/05/16/sql-server-command-line-tools-for-macos-released/).

*Installer [Homebrew](https://brew.sh) si elle n’est pas déjà :*

        /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

Pour installer les outils pour Mac El Capitan et Sierra, utilisez les commandes suivantes :

```
# brew untap microsoft/mssql-preview if you installed the preview version 
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
brew install mssql-tools
#for silent install: 
#HOMEBREW_NO_ENV_FILTERING=1 ACCEPT_EULA=y brew install mssql-tools
```

## <a id="docker"></a> Docker

Les outils de ligne de commande de SQL Server sont inclus dans l’image Docker. Si vous vous attachez à l’image avec une invite de commandes interactive, vous pouvez exécuter les outils localement.

## <a name="offline-installation"></a>Installation hors connexion

[!INCLUDE[SQL Server Linux offline package installation](../includes/sql-server-linux-offline-package-install-intro.md)]

1. Tout d’abord, localisez et copiez le **mssql-tools** package pour votre distribution Linux :

   | Distribution de Linux | **MSSQL-tools** emplacement du package |
   |---|---|
   | Red Hat | [https://packages.microsoft.com/rhel/7.3/prod](https://packages.microsoft.com/rhel/7.3/prod) |
   | SLES | [https://packages.microsoft.com/sles/12/prod](https://packages.microsoft.com/sles/12/prod)|
   | Ubuntu 16.04 | [https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/mssql-tools](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/mssql-tools) |

1. Également rechercher et copier le **msodbcsql** package, qui est une dépendance. Le **msodbcsql** package a également une dépendance sur soit **unixODBC-devel** (Red Hat et SLES) ou **unixodbc-dev** (Ubuntu). L’emplacement des packages **msodbcsql** est répertorié dans le tableau suivant :

   | Distribution de Linux | Emplacement des packages ODBC |
   |---|---|
   | Red Hat | [https://packages.microsoft.com/rhel/7.3/prod](https://packages.microsoft.com/rhel/7.3/prod) |
   | SLES | [https://packages.microsoft.com/sles/12/prod](https://packages.microsoft.com/sles/12/prod)|
   | Ubuntu 16.04 | [**msodbcsql**](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql)<br/>[**unixodbc-dev**](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/u/unixodbc/) |

1. **Déplacez les packages téléchargés sur votre ordinateur Linux**. Si vous avez utilisé un autre ordinateur pour télécharger les packages, une façon de déplacer les packages vers l’ordinateur Linux est d'utiliser la commande **scp**.

1. **Installer les packages et**: Installer le **mssql-tools** et **msodbc** packages. Si vous obtenez des erreurs de dépendance, ignorez-les jusqu'à l’étape suivante.

    | Plateforme | Commandes d’installation de package |
    |-----|-----|
    | Red Hat | `sudo yum localinstall msodbcsql-<version>.rpm`<br/>`sudo yum localinstall mssql-tools-<version>.rpm` |
    | SLES | `sudo zypper install msodbcsql-<version>.rpm`<br/>`sudo zypper install mssql-tools-<version>.rpm` |
    | Ubuntu | `sudo dpkg -i msodbcsql_<version>.deb`<br/>`sudo dpkg -i mssql-tools_<version>.deb` |

1. **Résoudre les dépendances manquantes**: Vous pouvez avoir de dépendances manquantes à ce stade. Si ce n’est pas le cas, vous pouvez ignorer cette étape. Dans certains cas, vous devez manuellement identifier et installer ces dépendances.

    Pour les packages RPM, vous pouvez examiner les dépendances requises avec les commandes suivantes :

    ```bash
    rpm -qpR msodbcsql-<version>.rpm
    rpm -qpR mssql-tools-<version>.rpm
    ```

    Pour les packages Debian, si vous avez accès à des référentiels approuvés contenant ces dépendances, la solution la plus simple consiste à utiliser la commande **apt-get** :

    ```bash
    sudo apt-get -f install
    ```

    > [!NOTE]
    > Cette commande termine l’installation des packages SQL Server également.

    Si cela ne fonctionne pas pour votre package Debian, vous pouvez examiner les dépendances requises avec les commandes suivantes :

    ```bash
    dpkg -I msodbcsql_<version>_amd64.deb | grep "Depends:"
    dpkg -I mssql-tools_<version>_amd64.deb | grep "Depends:"
    ```

## <a name="next-steps"></a>Étapes suivantes

Pour obtenir un exemple montrant comment utiliser **sqlcmd** pour se connecter à SQL Server et créer une base de données, consultez les didacticiels de démarrage rapide suivants :

- [Installation sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md)
- [Exécuter sur Docker](quickstart-install-connect-ubuntu.md)

Pour obtenir un exemple montrant comment utiliser **bcp** pour importer et exporter des données en bloc, consultez [opie de données en bloc vers SQL Server sur Linux](sql-server-linux-migrate-bcp.md).

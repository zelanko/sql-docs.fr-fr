---
title: Installer les outils de ligne de commande de SQL Server sur Linux | Documents Microsoft
description: "Cette rubrique décrit comment installer les outils SQL Server sur Linux."
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: eff8e226-185f-46d4-a3e3-e18b7a439e63
ms.workload: Active
ms.openlocfilehash: 16a2366541809237609c88f8458a3930a5569c3a
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="install-sqlcmd-and-bcp-the-sql-server-command-line-tools-on-linux"></a>Installer les outils de ligne de commande SQL Server sqlcmd et bcp sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Les étapes suivantes installer les outils de ligne de commande, les pilotes ODBC de Microsoft et leurs dépendances. Le **mssql-tools** package contient :

- **SQLCMD**: utilitaire de ligne de commande de requête.
- **bcp**: en bloc utilitaire d’importation / exportation.

Installer les outils pour votre plateforme :

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)
- [macOS](#macos)
- [Docker](#docker)

Cette rubrique décrit comment installer les outils de ligne de commande. Si vous recherchez des exemples d’utilisation **sqlcmd** ou **bcp**, consultez la [liens](#next-steps) à la fin de cette rubrique.

## <a name="a-idrhelainstall-tools-on-rhel-7"></a><a id="RHEL"><a/>Installer les outils sur RHEL 7

Utilisez les étapes suivantes pour installer le **mssql-tools** sur Red Hat Enterprise Linux. 

1. Activer le mode de super utilisateur.

   ```bash
   sudo su
   ```

1. Téléchargez le fichier de configuration du référentiel Microsoft Red Hat.

   ```bash
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/msprod.repo
   ```

1. Quitter le mode Super utilisateur.

   ```bash
   exit
   ```

1. Si vous aviez une version précédente de **mssql-tools** installé, supprimez tous les packages unixODBC plus anciens.

   ```bash
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel
   ```

1. Exécutez les commandes suivantes pour installer **mssql-tools** avec le kit du développeur unixODBC.

   ```bash
   sudo yum install mssql-tools unixODBC-devel
   ```

   > [!Note] 
   > Pour mettre à jour vers la dernière version de **mssql-tools** exécutez les commandes suivantes :
   >    ```bash
   >   sudo yum check-update
   >   sudo yum update mssql-tools
   >   ```

1. **Facultatif**: ajouter `/opt/mssql-tools/bin/` à votre **chemin d’accès** variable d’environnement dans un interpréteur de commandes bash.

   Pour rendre **sqlcmd/bcp** accessible à partir de l’interface de l’interpréteur de commandes pour les sessions de connexion, modifiez votre **chemin d’accès** dans les **~/.bash_profile** fichier avec la commande suivante :

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Pour rendre **sqlcmd/bcp** accessible à partir de l’interface de l’interpréteur de commandes pour les sessions/non-connexion interactive, modifiez le **chemin d’accès** dans le **~/.bashrc** fichier avec la commande suivante :

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="ubuntu"></a>Installer les outils sur Ubuntu 16.04

Utilisez les étapes suivantes pour installer le **mssql-tools** sur Ubuntu. 

1. Importer les clés GPG référentiel public.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Inscrire le référentiel Microsoft Ubuntu.

   ```bash
   curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/msprod.list
   ```

1. Mettre à jour la liste des sources et exécutez la commande d’installation avec le kit du développeur unixODBC.

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

1. **Facultatif**: ajouter `/opt/mssql-tools/bin/` à votre **chemin d’accès** variable d’environnement dans un interpréteur de commandes bash.

   Pour rendre **sqlcmd/bcp** accessible à partir de l’interface de l’interpréteur de commandes pour les sessions de connexion, modifiez votre **chemin d’accès** dans les **~/.bash_profile** fichier avec la commande suivante :

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Pour rendre **sqlcmd/bcp** accessible à partir de l’interface de l’interpréteur de commandes pour les sessions/non-connexion interactive, modifiez le **chemin d’accès** dans le **~/.bashrc** fichier avec la commande suivante :

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="SLES"></a>Installer les outils sur SLES 12

Utilisez les étapes suivantes pour installer le **mssql-tools** sur SUSE Linux Enterprise Server. 

1. Ajoutez le référentiel Microsoft SQL Server à Zypper.

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo 
   sudo zypper --gpg-auto-import-keys refresh
   ```

1. Installer **mssql-tools** avec le kit du développeur unixODBC.

   ```bash
   sudo zypper install mssql-tools unixODBC-devel
   ```

   > [!Note] 
   > Pour mettre à jour vers la dernière version de **mssql-tools** exécutez les commandes suivantes :
   >    ```bash
   >   sudo zypper refresh
   >   sudo zypper update mssql-tools
   >   ```

1. **Facultatif**: ajouter `/opt/mssql-tools/bin/` à votre **chemin d’accès** variable d’environnement dans un interpréteur de commandes bash.

   Pour rendre **sqlcmd/bcp** accessible à partir de l’interface de l’interpréteur de commandes pour les sessions de connexion, modifiez votre **chemin d’accès** dans les **~/.bash_profile** fichier avec la commande suivante :

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Pour rendre **sqlcmd/bcp** accessible à partir de l’interface de l’interpréteur de commandes pour les sessions/non-connexion interactive, modifiez le **chemin d’accès** dans le **~/.bashrc** fichier avec la commande suivante :

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

## <a id="macos"></a>Installer les outils sur macOS

Un aperçu de **sqlcmd** et **bcp** est maintenant disponible sur macOS. Pour plus d’informations, consultez la [annonce](https://blogs.technet.microsoft.com/dataplatforminsider/2017/05/16/sql-server-command-line-tools-for-macos-released/).

Pour installer les outils pour Mac El Capitan et Sierra, utilisez les commandes suivantes :

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
#brew untap microsoft/mssql-preview if you installed the preview version 
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
brew install --no-sandbox mssql-tools
#for silent install: 
#ACCEPT_EULA=y brew install --no-sandbox mssql-tools
```

## <a id="docker"></a>Docker

À compter de SQL Server 2017 CTP 2.0, les outils de ligne de commande de SQL Server sont inclus dans l’image de Docker. Si vous attachez à l’image avec une invite de commandes interactive, vous pouvez exécuter les outils localement.

## <a name="offline-installation"></a>Installation hors connexion

[!INCLUDE[SQL Server Linux offline package installation](../includes/sql-server-linux-offline-package-install-intro.md)]

Le tableau suivant fournit l’emplacement pour les packages d’outils plus récentes :

| Package d’outils | Version | Télécharger |
|-----|-----|-----|
| Package d’outils de Red Hat RPM | 14.0.5.0-1 | [package RPM de MSSQL-outils](https://packages.microsoft.com/rhel/7.3/prod/mssql-tools-14.0.5.0-1.x86_64.rpm) | 
| Package d’outils SLES RPM | 14.0.5.0-1 | [package RPM de MSSQL-outils](https://packages.microsoft.com/sles/12/prod/mssql-tools-14.0.5.0-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian package des outils | 14.0.5.0-1 | [package de Debian MSSQL-outils](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/mssql-tools/mssql-tools_14.0.5.0-1_amd64.deb) |
| Ubuntu 16.10 Debian package des outils | 14.0.5.0-1 | [package de Debian MSSQL-outils](https://packages.microsoft.com/ubuntu/16.10/prod/pool/main/m/mssql-tools/mssql-tools_14.0.5.0-1_amd64.deb) |

Ces packages dépendent de **msodbcsql**, qui doit être installé en premier. Le **msodbcsql** celui-ci a également une dépendance sur le **unixODBC-développement** (RPM) ou **unixodbc-dev** (Debian). L’emplacement de la **msodbcsql** packages sont répertoriés dans le tableau suivant :

| package de msodbcsql | Version | Télécharger |
|-----|-----|-----|
| Red Hat RPM de msodbcsql | 13.1.6.0-1 | [package RPM de msodbcsql](https://packages.microsoft.com/rhel/7.3/prod/msodbcsql-13.1.6.0-1.x86_64.rpm) | 
| SLES RPM de msodbcsql | 13.1.6.0-1 | [package RPM de msodbcsql](https://packages.microsoft.com/sles/12/prod/msodbcsql-13.1.6.0-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian msodbcsql package | 13.1.6.0-1 | [package de Debian msodbcsql](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql/msodbcsql_13.1.6.0-1_amd64.deb) |
| Ubuntu 16.10 msodbcsql Debian package | 13.1.6.0-1 | [package de Debian msodbcsql](https://packages.microsoft.com/ubuntu/16.10/prod/pool/main/m/msodbcsql/msodbcsql_13.1.6.0-1_amd64.deb) |

Pour installer manuellement ces packages, procédez comme suit :

1. **Déplacer les packages téléchargés sur votre ordinateur Linux**. Si vous avez utilisé un autre ordinateur pour télécharger les packages, un pour déplacer les packages à l’ordinateur Linux est la **scp** commande.

1. **Installer les packages et**: installer le **mssql-tools** et **msodbc** packages. Si vous obtenez des erreurs de dépendance, les ignorer jusqu'à ce que l’étape suivante.

    | Plateforme | Commandes d’installation de package |
    |-----|-----|
    | Red Hat | `sudo yum localinstall msodbcsql-13.1.6.0-1.x86_64.rpm`<br/>`sudo yum localinstall mssql-tools-14.0.5.0-1.x86_64.rpm` |
    | SLES | `sudo zypper install msodbcsql-13.1.6.0-1.x86_64.rpm`<br/>`sudo zypper install mssql-tools-14.0.5.0-1.x86_64.rpm` |
    | Ubuntu | `sudo dpkg -i msodbcsql_13.1.6.0-1_amd64.deb`<br/>`sudo dpkg -i mssql-tools_14.0.5.0-1_amd64.deb` |

1. **Résoudre les dépendances manquantes**: vous pouvez avoir des dépendances manquantes à ce stade. Si ce n’est pas le cas, vous pouvez ignorer cette étape. Dans certains cas, vous devez localiser et installer manuellement ces dépendances.

    Pour les packages RPM, vous pouvez inspecter les dépendances nécessaires avec les commandes suivantes :

    ```bash
    rpm -qpR msodbcsql-13.1.6.0-1.x86_64.rpm
    rpm -qpR mssql-tools-14.0.5.0-1.x86_64.rpm
    ```

    Pour les packages Debian, si vous avez accès à des référentiels approuvées contenant ces dépendances, la solution la plus simple consiste à utiliser le **apt-get** commande :

    ```bash
    sudo apt-get -f install
    ```

    > [!NOTE]
    > Cette commande termine l’installation des packages SQL Server également.

    Si cela ne fonctionne pas pour votre package Debian, vous pouvez inspecter les dépendances nécessaires avec les commandes suivantes :

    ```bash
    dpkg -I msodbcsql_13.1.6.0-1_amd64.deb | grep "Depends:"
    dpkg -I mssql-tools_14.0.5.0-1_amd64.deb | grep "Depends:"
    ```

## <a name="next-steps"></a>Étapes suivantes

Pour obtenir un exemple montrant comment utiliser **sqlcmd** pour se connecter à SQL Server et créer une base de données, consultez une des Démarrages rapides suivants :

- [Installer sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md)
- [Exécutez sur Docker](quickstart-install-connect-ubuntu.md)

Pour obtenir un exemple montrant comment utiliser **bcp** pour importer en bloc et exporter des données, consultez [des données de copie en bloc vers SQL Server sur Linux](sql-server-linux-migrate-bcp.md).

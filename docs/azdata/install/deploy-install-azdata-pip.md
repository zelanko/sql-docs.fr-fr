---
title: Installer Azure Data CLI (azdata) avec pip
titleSuffix: ''
description: Découvrez comment installer l’outil azdata avec pip.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 09/30/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4aa52ebe56cbe4af3d2983a9ed800ebbc1538971
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257452"
---
# <a name="install-azure-data-cli-azdata-with-pip"></a>Installer [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)] avec `pip`

[!INCLUDE[azdata](../../includes/applies-to-version/azdata.md)]

Cet article explique comment installer l’outil [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)] sur Windows, Linux ou macOS/OS X à l’aide de `pip`.

> [!TIP]
> Pour bénéficier d’une expérience plus simple, `azdata` peut être installé avec un [gestionnaire de package](./deploy-install-azdata.md) pour Windows, Linux (distributions Ubuntu, Debian, RHEL, CentOS, openSUSE et SLE) et macOS.

## <a name="prerequisites"></a><a id="prerequisites"></a> Conditions préalables

`azdata` est un utilitaire en ligne de commande écrit en Python qui permet aux administrateurs de clusters de démarrer et de gérer des ressources de données par le biais des API REST. Vous devez utiliser au minimum Python version 3.5. `pip` est nécessaire pour télécharger et installer l’outil `azdata`. Les instructions ci-dessous fournissent des exemples pour Windows, Linux (Ubuntu) et macOS/OS X. Pour installer Python sur d’autres plateformes, consultez la [documentation Python](https://wiki.python.org/moin/BeginnersGuide/Download). En outre, installez et mettez à jour la dernière version du package Python `requests` :

```bash
pip3 install -U requests
```

## <a name="windows-azdata-installation"></a><a id="windows"></a> Installation de `azdata` sur Windows

1. Sur un client Windows, téléchargez le package Python nécessaire à partir de [https://www.python.org/downloads/](https://www.python.org/downloads/). Pour Python 3.5.3 et les versions ultérieures, pip3 est installé en même temps que Python.

   > [!TIP]
   > Lorsque vous installez Python 3, ajoutez Python à votre chemin (`PATH`). Si vous ne le faites pas, vous pourrez rechercher plus tard l’emplacement de PIP3 et l’ajouter manuellement à `PATH`.

1. Ouvrez une nouvelle session Windows PowerShell afin d’obtenir le chemin le plus récent avec Python.

1. À compter de SQL Server 2019 CU5, azdata inclut une version sémantique indépendante du serveur. Si des versions précédentes d’`azdata` sont déjà installées avant celle-ci, il est important de les désinstaller d’abord, puis d’installer la dernière version.

   Par exemple, pour 2019-cu4, exécutez la commande suivante :

   ```powershell
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-cu4/requirements.txt
   ```

  > [!NOTE]
  > Dans les exemples précédents, remplacez `2019-cu6` par la version et la mise à jour cumulative (CU) de votre installation d’`azdata`. 

1. Installez `azdata`.

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

## <a name="linux-azdata-installation"></a><a id="linux"></a> Installation de `azdata` sur Linux

Sur Linux, vous devez installer Python 3.5, puis mettre à niveau pip. L’exemple suivant montre les commandes qui fonctionnent pour Ubuntu. Pour les autres plateformes Linux, consultez la [documentation Python](https://wiki.python.org/moin/BeginnersGuide/Download).

1. Installez les packages Python nécessaires :

   ```bash
   sudo apt-get update && \
   sudo apt-get install -y python3 && \
   sudo apt-get install -y python3-pip && \
   sudo apt-get install -y libkrb5-dev && \
   sudo apt-get install -y libsqlite3-dev && \
   sudo apt-get install -y unixodbc-dev
   ```

1. Mettez à niveau pip3.

   ```bash
   sudo -H pip3 install --upgrade pip
   ```

1. À compter de SQL Server 2019 CU5, azdata inclut une version sémantique indépendante du serveur. Si des versions précédentes d’`azdata` sont déjà installées avant celle-ci, il est important de les désinstaller d’abord, puis d’installer la dernière version.

   Par exemple, pour `2019-cu6`, exécutez la commande suivante :

   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-cu6/requirements.txt
   ```

  > [!NOTE]
  > Dans les exemples précédents, remplacez `2019-cu6` par la version et la mise à jour cumulative (CU) de votre installation d’`azdata`.

1. Installez `azdata`.

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!NOTE]
   > Le commutateur `--user` installe `azdata` dans le répertoire d’installation de l’utilisateur Python. Sur Linux, il s’agit généralement de `~/.local/bin`. Ajoutez ce répertoire à votre chemin ou accédez au répertoire d’installation de l’utilisateur et exécutez `./azdata` à partir de ce répertoire.

## <a name="install-azdata-on-macos-or-os-x"></a><a id="macOSX"></a> Installer `azdata` sur macOS ou OS X

Pour installer `azdata` sur macOS ou OS X, effectuez les étapes suivantes. Pour chaque étape, exécutez l’exemple dans Terminal.

1. Sur un client macOS, installez [Homebrew](https://brew.sh) si vous ne l’avez pas déjà :

   ```bash
   /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
   ```

1. Installez Python et PIP, au minimum la version 3.0 :

   ```bash
   brew install python3
   ```

1. Installez des dépendances :

   ```bash
   pip3 install -U requests
   brew install freetds
   ```

1. À compter de SQL Server 2019 CU5, azdata inclut une version sémantique indépendante du serveur. Si des versions précédentes d’`azdata` sont déjà installées avant celle-ci, il est important de les désinstaller d’abord, puis d’installer la dernière version. Par exemple, la commande suivante supprime la version RC1 disque défini au d’`azdata` :

   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-rc1/requirements.txt
   ```

1. Installer Azure Data CLI.

   ```bash
   pip3 install -r https://aka.ms/azdata
   ```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [Que sont les [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)] ?](../../big-data-cluster/big-data-cluster-overview.md).

Utiliser azdata avec les [services de données dotés d’Azure Arc](/azure/azure-arc/data/)

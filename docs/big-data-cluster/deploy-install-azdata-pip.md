---
title: Installer azdata à l’aide de PIP
titleSuffix: SQL Server big data clusters
description: Découvrez comment installer l’outil azdata pour installer et gérer des clusters Big Data avec PIP.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5360e7aa9718fef0d17bf73b9064c2d1a61a4577
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75726946"
---
# <a name="install-azdata-with-pip"></a>Installer `azdata` avec `pip`

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article explique comment installer l’outil `azdata` Windows ou Linux à l’aide de `pip`.

Pour Windows et Linux (distribution Ubuntu), vous pouvez effectuer l’installation avec un [gestionnaire de package](./deploy-install-azdata-installer.md) pour bénéficier d’une expérience plus simple.

## <a name="prerequisites"></a><a id="prerequisites"></a> Conditions préalables

`azdata` est un utilitaire en ligne de commande écrit en Python qui permet aux administrateurs de clusters de démarrer et de gérer les clusters Big Data via des API REST. Vous devez utiliser au minimum Python version 3.5. `pip` est requis pour télécharger et installer l’outil `azdata`. Les instructions ci-dessous fournissent des exemples pour Windows et Ubuntu. Pour installer Python sur d’autres plateformes, consultez la [documentation Python](https://wiki.python.org/moin/BeginnersGuide/Download).
En outre, installez et mettez à jour la dernière version du package Python `requests` :

```bash
pip3 install -U requests
```

> [!IMPORTANT]
> Si vous installez une version plus récente de clusters Big Data, sauvegardez vos données et supprimez les anciens clusters avant de mettre à niveau `azdata` et d’installer la nouvelle version. Pour plus d’informations, consultez [Mise à niveau vers une nouvelle version](deployment-upgrade.md).

## <a name="windows-azdata-installation"></a><a id="windows"></a> Installation de `azdata` sur Windows

1. Sur un client Windows, téléchargez le package Python nécessaire à partir de [https://www.python.org/downloads/](https://www.python.org/downloads/). Pour Python 3.5.3 et versions ultérieures, pip3 est installé en même temps que Python. 

   > [!TIP] 
   > Lorsque vous installez Python 3, ajoutez Python à votre chemin (`PATH`). Si vous ne le faites pas, vous pourrez rechercher plus tard l’emplacement de PIP3 et l’ajouter manuellement à `PATH`.

1. Ouvrez une nouvelle session Windows PowerShell afin d’obtenir le chemin le plus récent avec Python.

1. Si des versions release précédentes d’`azdata` sont déjà installées, il est important de commencer par les désinstaller avant d’installer la dernière version.

   Pour CTP 3.2 ou RC1, exécutez la commande suivante.

   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-ctp3.2/requirements.txt
   ```
   or
   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-rc1/requirements.txt
   ```

1. Installez `azdata` avec la commande suivante :

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

1. Mettez à niveau pip3 :

   ```bash
   sudo -H pip3 install --upgrade pip
   ```

1. Si des versions release précédentes d’`azdata` sont déjà installées, il est important de commencer par les désinstaller avant d’installer la dernière version.

   Pour CTP 3.2 ou RC1, exécutez la commande suivante.

   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-ctp3.2/requirements.txt
   ```
   or
   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-rc1/requirements.txt
   ```

1. Installez `azdata` avec la commande suivante :

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!NOTE]
   > Le commutateur `--user` installe `azdata` dans le répertoire d’installation de l’utilisateur Python. Sur Linux, il s’agit généralement de `~/.local/bin`. Ajoutez ce répertoire à votre chemin ou accédez au répertoire d’installation de l’utilisateur et exécutez `./azdata` à partir de ce répertoire.

## <a name="install-azdata-on-macos-or-os-x"></a><a id="macOSX"></a> Installer `azdata` sur macOS ou OS X

Pour installer `azdata` sur macOS ou OS X, effectuez les étapes suivantes. Pour chaque étape, exécutez l’exemple dans Terminal.

1. Sur un client macOS, installez [Homebrew](https://brew.sh) si vous ne l’avez pas déjà :

   ```
   /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
   ```

1. Installez Python et PIP, au minimum la version 3.0 :

   ```
   brew install python3
   ```

1. Installez des dépendances :

   ```
   pip3 install -U requests
   brew install freetds
   ```

1. Si des versions précédentes de l’outil sont installées, il est important de commencer par les désinstaller avant d’installer la dernière version de `azdata`. La commande suivante supprime la version de `azdata`.

   ```
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-rc1/requirements.txt
   ```

1. Installez `azdata` avec la commande suivante :

   ```
   pip3 install -r https://aka.ms/azdata
   ```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [Que sont les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] ?](big-data-cluster-overview.md).

---
title: Installer azdata à l’aide de PIP
titleSuffix: SQL Server big data clusters
description: Découvrez comment installer l’outil azdata pour installer et gérer [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (version préliminaire) avec PIP.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a72e2ab39a17adef6c330f1ae17dcdc8a5dd8ddf
ms.sourcegitcommit: 71fac5fee00e0eca57e555f44274dd7e08d47e1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70160731"
---
# <a name="install-azdata-for-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd-using-pip"></a>Installer `azdata` pour [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] à l’aide de`pip`

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article explique comment installer l' `azdata` outil pour la version Release Candidate sur Windows ou Linux à l’aide `pip`de.

## <a id="prerequisites"></a> Conditions préalables

`azdata`est un utilitaire de ligne de commande écrit en Python qui permet aux administrateurs de clusters de démarrer et de gérer le cluster Big Data via des API REST. Vous devez utiliser au minimum Python version 3.5. Vous devez également avoir `pip` utilisé pour télécharger et installer `azdata` l’outil. Les instructions ci-dessous fournissent des exemples pour Windows et Ubuntu. Pour installer Python sur d’autres plateformes, consultez la [documentation Python](https://wiki.python.org/moin/BeginnersGuide/Download).
En outre, vous devez également installer et mettre à jour la dernière version du package Python *requests* :
```bash
pip3 install -U requests
```

> [!IMPORTANT]
> Si vous installez une version plus récente de Big Data clusters, vous devez sauvegarder vos données et supprimer l’ancien cluster *avant* d’effectuer `azdata` la mise à niveau et l’installation de la nouvelle version. Pour plus d’informations, consultez [Mise à niveau vers une nouvelle version](deployment-upgrade.md).

## <a id="windows"></a>Installation `azdata` de Windows

1. Sur un client Windows, téléchargez le package Python nécessaire à partir de [https://www.python.org/downloads/](https://www.python.org/downloads/). Pour Python 3.5.3 et versions ultérieures, pip3 est installé en même temps que Python. 

   > [!TIP] 
   > Lorsque vous installez Python 3, ajoutez Python à votre chemin (**PATH**). Si vous ne le faites pas, vous pourrez rechercher plus tard l’emplacement de PIP3 et l’ajouter manuellement à **PATH**.

1. Ouvrez une nouvelle session Windows PowerShell afin d’obtenir le chemin le plus récent avec Python.

1. Si vous avez installé des versions précédentes de l’outil (avant la version CTP 3,2, l’outil était appelé **mssqlctl**), il est important de le désinstaller avant d’installer la dernière `azdata`version de. La commande suivante supprime la version CTP 3,1 de **mssqlctl**.

   ```powershell
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. Si vous avez installé des versions antérieures `azdata` de, il est important de le désinstaller avant d’installer la dernière version.

   Pour CTP 3,2, exécutez la commande suivante.

   ```powershell
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-ctp3.2/requirements.txt
   ```

1. Installez `azdata` à l’aide de la commande suivante:

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

## <a id="linux"></a>Installation `azdata` de Linux

Sur Linux, vous devez installer Python 3.5, puis mettre à niveau pip. L’exemple suivant montre les commandes qui fonctionnent pour Ubuntu. Pour les autres plateformes Linux, consultez la [documentation Python](https://wiki.python.org/moin/BeginnersGuide/Download).

1. Installez les packages Python nécessaires :

   ```bash
   sudo apt-get update && \
   sudo apt-get install -y python3 && \
   sudo apt-get install -y python3-pip
   ```

1. Mettez à niveau pip3 :

   ```bash
   sudo -H pip3 install --upgrade pip
   ```

1. Si vous avez installé des versions précédentes de l’outil (avant la version CTP 3,2, l’outil était appelé **mssqlctl**), il est important de le désinstaller avant d’installer la dernière `azdata`version de. La commande suivante supprime la version CTP 3,1 de **mssqlctl**.

   ```bash
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. Si vous avez installé des versions antérieures `azdata` de, il est important de le désinstaller avant d’installer la dernière version.

   Pour CTP 3,2, exécutez la commande suivante.

   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-ctp3.2/requirements.txt
   ```

1. Installez `azdata` à l’aide de la commande suivante:

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!NOTE]
   > Le `--user` commutateur `azdata` s’installe dans le répertoire d’installation de l’utilisateur Python. Sur Linux, il s’agit généralement de `~/.local/bin`. Ajoutez ce répertoire à votre chemin ou accédez au répertoire d’installation de l’utilisateur et exécutez `./azdata` à partir de ce répertoire.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [ [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]que sont?](big-data-cluster-overview.md).

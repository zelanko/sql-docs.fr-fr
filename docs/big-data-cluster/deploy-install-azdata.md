---
title: Installer azdata
titleSuffix: SQL Server big data clusters
description: Découvrez comment installer l’outil azdata pour l’installation et la [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] gestion (version préliminaire).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e95fe15877dd6d22ca575b79f9fb213b6104d3aa
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69652419"
---
# <a name="install-azdata-to-manage-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Installer azdata pour gérer[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article explique comment installer l’outil **azdata** pour CTP 3.2 sur Windows ou Linux.

## <a id="prerequisites"></a> Conditions préalables

**azdata** est un utilitaire de ligne de commande écrit en Python qui permet aux administrateurs de clusters de démarrer et de gérer les clusters Big Data via des API REST. Vous devez utiliser au minimum Python version 3.5. Vous devez également disposer de `pip`, qui permet de télécharger et d’installer l’outil **azdata**. Les instructions ci-dessous fournissent des exemples pour Windows et Ubuntu. Pour installer Python sur d’autres plateformes, consultez la [documentation Python](https://wiki.python.org/moin/BeginnersGuide/Download).
En outre, vous devez également installer et mettre à jour la dernière version du package Python *requests* :
```bash
pip3 install -U requests
```

> [!IMPORTANT]
> Si vous installez une version plus récente de clusters Big Data, vous devez sauvegarder vos données et supprimer les anciens clusters *avant* de mettre à niveau **azdata** et d’installer la nouvelle version. Pour plus d’informations, consultez [Mise à niveau vers une nouvelle version](deployment-upgrade.md).

## <a id="windows"></a> Installation de azdata sur Windows

1. Sur un client Windows, téléchargez le package Python nécessaire à partir de [https://www.python.org/downloads/](https://www.python.org/downloads/). Pour Python 3.5.3 et versions ultérieures, pip3 est installé en même temps que Python. 

   > [!TIP] 
   > Lorsque vous installez Python 3, ajoutez Python à votre chemin (**PATH**). Si vous ne le faites pas, vous pourrez rechercher plus tard l’emplacement de PIP3 et l’ajouter manuellement à **PATH**.

1. Ouvrez une nouvelle session Windows PowerShell afin d’obtenir le chemin le plus récent avec Python.

1. Si des versions précédentes de l’outil (anciennement **mssqlctl**) sont déjà installées, il est important de le désinstaller avant d’installer la dernière version de **azdata**.

   Pour CTP 3.1 et antérieur, exécutez la commande suivante. Dans la commande, remplacez `ctp3.1` par la version de **mssqlctl** que vous désinstallez. 

   ```powershell
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. Si des versions précédentes de **azdata** sont installées, il est important de commencer par les désinstaller avant d’installer la dernière version.

   Pour CTP 3.2 et ultérieur, exécutez la commande suivante. Dans la commande, remplacez `ctp3.2` par la version de **azdata** que vous désinstallez.

   ```powershell
   pip3 uninstall -r https://aka.ms/azdata
   ```

1. Installez **azdata** à l’aide de la commande suivante :

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

## <a id="linux"></a> Installation de azdata sur Linux

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

1. Si des versions précédentes de l’outil (anciennement **mssqlctl**) sont déjà installées, il est important de le désinstaller avant d’installer la dernière version de **azdata**.

   Pour CTP 3.1 et antérieur, exécutez la commande suivante. Dans la commande, remplacez `ctp3.1` par la version de **mssqlctl** que vous désinstallez. 

   ```powershell
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. Si des versions précédentes de **azdata** sont installées, il est important de commencer par les désinstaller avant d’installer la dernière version.

   Pour CTP 3.2 et ultérieur, exécutez la commande suivante. Dans la commande, remplacez `ctp3.2` par la version de **azdata** que vous désinstallez.

   ```powershell
   pip3 uninstall -r https://aka.ms/azdata
   ```

1. Installez **azdata** à l’aide de la commande suivante :

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!NOTE]
   > Le commutateur `--user` installe azdata dans le répertoire d’installation de l’utilisateur Python. Sur Linux, il s’agit généralement de `~/.local/bin`. Ajoutez ce répertoire à votre chemin ou accédez au répertoire d’installation de l’utilisateur et exécutez `./azdata` à partir de ce répertoire.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [ [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]que sont?](big-data-cluster-overview.md).

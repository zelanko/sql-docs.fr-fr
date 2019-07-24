---
title: Installer azdata
titleSuffix: SQL Server big data clusters
description: Découvrez comment installer l’outil azdata pour installer et gérer des clusters SQL Server 2019 Big Data (version préliminaire).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9444842081456563f411ad618f32b8dbd59f7513
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426439"
---
# <a name="install-azdata-to-manage-sql-server-big-data-clusters"></a>Installer azdata pour gérer les clusters de Big Data SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article explique comment installer l’outil **azdata** pour CTP 3,2 sur Windows ou Linux.

## <a id="prerequisites"></a> Conditions préalables

**azdata** est un utilitaire de ligne de commande écrit en Python qui permet aux administrateurs de clusters de démarrer et de gérer le cluster Big Data via des API REST. La version minimale de Python requise est v 3.5. Vous devez également avoir `pip` utilisé pour télécharger et installer l’outil **azdata** . Les instructions ci-dessous fournissent des exemples pour Windows et Ubuntu. Pour installer Python sur d’autres plateformes, consultez la [documentation python](https://wiki.python.org/moin/BeginnersGuide/Download).
En outre, vous devez également installer et mettre à jour la dernière version des *demandes* de package Python:
```bash
pip3 install -U requests
```

> [!IMPORTANT]
> Si vous installez une version plus récente de Big Data clusters, vous devez sauvegarder vos données et supprimer l’ancien cluster *avant* de mettre à niveau **azdata** et d’installer la nouvelle version. Pour plus d’informations, consultez [mise à niveau vers une nouvelle version](deployment-upgrade.md).

## <a id="windows"></a>Installation de Windows azdata

1. Sur un client Windows, téléchargez le package Python nécessaire à [https://www.python.org/downloads/](https://www.python.org/downloads/)partir de. Pour Python 3.5.3 et versions ultérieures, PIP3 est également installé lorsque vous installez Python. 

   > [!TIP] 
   > Lors de l’installation de Python3, sélectionnez pour ajouter Python à votre **chemin d’accès**. Si vous ne le faites pas, vous pourrez ensuite trouver l’emplacement où se trouve PIP3 et l’ajouter manuellement à votre **chemin**.

1. Ouvrez une nouvelle session Windows PowerShell afin d’obtenir le chemin d’accès le plus récent avec Python.

1. Si vous avez installé des versions précédentes de l’outil (previosly nommé **mssqlctl**), il est important de le désinstaller avant d’installer la dernière version de **azdata**.

   Pour CTP 3,1 ou version antérieure, exécutez la commande suivante. Remplacez `ctp3.1` dans la commande par la version de **mssqlctl** que vous désinstallez. 

   ```powershell
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. Si des versions précédentes de **azdata** sont installées, il est important de les désinstaller avant d’installer la dernière version.

   Pour la version CTP 3,2 ou une version ultérieure, exécutez la commande suivante. Remplacez `ctp3.2` dans la commande par la version de **azdata** que vous désinstallez.

   ```powershell
   pip3 uninstall -r https://aka.ms/azdata
   ```

1. Installez **azdata** à l’aide de la commande suivante:

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

## <a id="linux"></a>Installation de Linux azdata

Sur Linux, vous devez installer python 3,5, puis mettre à niveau PIP. L’exemple suivant montre les commandes qui fonctionnent pour Ubuntu. Pour les autres plateformes Linux, consultez la [documentation python](https://wiki.python.org/moin/BeginnersGuide/Download).

1. Installez les packages python nécessaires:

   ```bash
   sudo apt-get update && /
   sudo apt-get install -y python3 && /
   sudo apt-get install -y python3-pip
   ```

1. Mettre à niveau PIP3:

   ```bash
   sudo -H pip3 install --upgrade pip
   ```

1. Si vous avez installé des versions précédentes de l’outil (précédemment nommé **mssqlctl**), il est important de le désinstaller avant d’installer la dernière version de **azdata**.

   Pour CTP 3,1 ou version antérieure, exécutez la commande suivante. Remplacez `ctp3.1` dans la commande par la version de **mssqlctl** que vous désinstallez. 

   ```powershell
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. Si des versions précédentes de **azdata** sont installées, il est important de les désinstaller avant d’installer la dernière version.

   Pour la version CTP 3,2 ou une version ultérieure, exécutez la commande suivante. Remplacez `ctp3.2` dans la commande par la version de **azdata** que vous désinstallez.

   ```powershell
   pip3 uninstall -r https://aka.ms/azdata
   ```

1. Installez **azdata** à l’aide de la commande suivante:

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!NOTE]
   > Le `--user` commutateur installe azdata dans le répertoire d’installation de l’utilisateur Python. Il s’agit `~/.local/bin` généralement de Linux. Ajoutez ce répertoire à votre chemin d’accès ou accédez au répertoire d’installation de l' `./azdata` utilisateur et exécutez à partir de cet emplacement.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [que sont SQL Server les clusters Big Data 2019?](big-data-cluster-overview.md).

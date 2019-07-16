---
title: Installer mssqlctl
titleSuffix: SQL Server big data clusters
description: Découvrez comment installer l’outil mssqlctl pour l’installation et la gestion des clusters de données volumineuses de SQL Server 2019 (version préliminaire).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 3be1987baed27aeb49b03942ca3c4f07c2b0ce0c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67958525"
---
# <a name="install-mssqlctl-to-manage-sql-server-big-data-clusters"></a>Installer mssqlctl pour gérer les clusters de données volumineuses de SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article décrit comment installer le **mssqlctl** outil pour la version CTP 3.1 sur Windows ou Linux.

**mssqlctl** est un utilitaire de ligne de commande écrit dans Python que permet aux administrateurs de démarrer et de gérer le cluster de données volumineuses via les API REST de cluster. La version de Python minimale requise est v3.5. Vous devez également avoir `pip` qui est utilisé pour télécharger et installer **mssqlctl** outil. Les instructions ci-dessous fournissent des exemples pour Windows et Ubuntu. Pour l’installation de Python sur d’autres plateformes, consultez le [documentation Python](https://wiki.python.org/moin/BeginnersGuide/Download).

> [!IMPORTANT]
> Si vous installez une version plus récente de clusters de données volumineuses, vous devez sauvegarder vos données et supprimer l’ancien cluster *avant* la mise à niveau **mssqlctl** et l’installation de la nouvelle version. Pour plus d’informations, consultez [mise à niveau vers une nouvelle version](deployment-upgrade.md).

## <a id="windows"></a> Installation de mssqlctl Windows

1. Sur un client Windows, téléchargez le package Python nécessaire [ https://www.python.org/downloads/ ](https://www.python.org/downloads/). Pour python3.5.3 et versions ultérieures, pip3 est également installé lorsque vous installez Python. 

   > [!TIP] 
   > Lorsque vous installez Python3, sélectionnez cette option pour ajouter Python à votre **chemin d’accès**. Si vous ne le faites pas, vous pouvez êtes amené à constater où se trouve pip3 et l’ajouter manuellement à votre **chemin d’accès**.

1. Ouvrez une nouvelle session Windows PowerShell afin qu’il obtient le chemin d’accès plus récente avec Python qu’il contient.

1. Si vous disposez de toutes les versions précédentes de **mssqlctl** installé, il est important de désinstaller **mssqlctl** premier avant d’installer la dernière version.

   Si vous désinstallez **mssqlctl** correspondant à la version 2.2 ou inférieur de CTP exécuter :

   ```powershell
   pip3 uninstall mssqlctl
   ```

   Pour CTP 2.3 ou version ultérieure, exécutez la commande suivante. Remplacez `ctp3.0` dans la commande avec la version de **mssqlctl** que vous désinstallez. Si la version est avant CTP 3.0, ajoutez un tiret avant le numéro de version (par exemple, `ctp-2.5`).

   ```powershell
   pip3 uninstall -r  https://private-repo.microsoft.com/python/ctp3.0/mssqlctl/requirements.txt
   ```

1. Installer **mssqlctl** avec la commande suivante :

   ```powershell
   pip3 install -r  https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

## <a id="linux"></a> Installation de mssqlctl Linux

Sur Linux, vous devez installer Python 3.5 et ensuite mettre à niveau pip. L’exemple suivant montre les commandes qui fonctionneraient pour Ubuntu. Pour d’autres plateformes Linux, consultez le [documentation Python](https://wiki.python.org/moin/BeginnersGuide/Download).

1. Installer les packages Python nécessaires :

   ```bash
   sudo apt-get update && /
   sudo apt-get install -y python3 && /
   sudo apt-get install -y python3-pip
   ```

1. Mise à niveau pip3 :

   ```bash
   sudo -H pip3 install --upgrade pip
   ```

1. Si vous disposez de toutes les versions précédentes de **mssqlctl** installé, il est important de désinstaller **mssqlctl** premier avant d’installer la dernière version.

   Si vous désinstallez **mssqlctl** correspondant à la version 2.2 ou inférieur de CTP exécuter :

   ```powershell
   pip3 uninstall mssqlctl
   ```

   Pour CTP 2.3 ou version ultérieure, exécutez la commande suivante. Remplacez `ctp3.0` dans la commande avec la version de **mssqlctl** que vous désinstallez. Si la version est avant CTP 3.0, ajoutez un tiret avant le numéro de version (par exemple, `ctp-2.5`).

   ```powershell
   pip3 uninstall -r  https://private-repo.microsoft.com/python/ctp3.0/mssqlctl/requirements.txt
   ```

1. Installer **mssqlctl** avec la commande suivante :

   ```bash
   pip3 install -r  https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt --user
   ```

   > [!NOTE]
   > Le `--user` commutateur installe mssqlctl dans le répertoire d’installation de Python utilisateur. Il s’agit généralement `~/.local/bin` sur Linux. Soit ajouter ce répertoire à votre chemin d’accès ou accédez au répertoire d’installation utilisateur et que vous exécutez `./mssqlctl` à partir de là.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters de données volumineuses, consultez [que sont les clusters de données volumineuses de SQL Server 2019 ?](big-data-cluster-overview.md).

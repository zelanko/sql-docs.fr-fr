---
title: Effectuer une mise à niveau vers une nouvelle version
titleSuffix: SQL Server big data clusters
description: Découvrez comment mettre à niveau des clusters Big Data SQL Server 2019 (préversion) vers une nouvelle version.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 29bdd3996112154b222ffb7d43390050c9af2d02
ms.sourcegitcommit: 0d89bcaebdf87db3bd26db2ca263be9c671b0220
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2019
ms.locfileid: "68731088"
---
# <a name="how-to-upgrade-sql-server-big-data-clusters"></a>Guide pratique pour mettre à niveau des clusters Big Data SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article fournit des conseils sur la façon de mettre à niveau un cluster Big Data SQL Server vers une nouvelle version. Les étapes décrites dans cet article s’appliquent spécifiquement à la mise à niveau entre des préversions.

## <a name="backup-and-delete-the-old-cluster"></a>Sauvegarder et supprimer l’ancien cluster

La seule façon de mettre à niveau un cluster Big Data vers une nouvelle version consiste à supprimer le cluster et à le recréer manuellement. Chaque version a une version unique d’**azdata** qui n’est pas compatible avec la version précédente. En outre, si un cluster plus ancien devait télécharger une image sur un nouveau nœud, la dernière image risquerait de ne pas être compatible avec les anciennes images sur le cluster. Pour effectuer une mise à niveau vers la dernière version, procédez comme suit :

1. Avant de supprimer l’ancien cluster, sauvegardez les données sur l’instance maître SQL Server et sur HDFS. Pour l’instance maître SQL Server, vous pouvez utiliser [Sauvegarde et restauration d’une base de données SQL Server](data-ingestion-restore-database.md). Pour HDFS, vous [pouvez copier les données avec **curl**](data-ingestion-curl.md).

1. Supprimez l’ancien cluster à l’aide de la commande `azdata delete cluster`.

   ```bash
    azdata bdc delete --name <old-cluster-name>
   ```

   > [!Important]
   > Utilisez la version d’**azdata** qui correspond à votre cluster. Ne supprimez pas un ancien cluster avec la version d’**azdata** plus récente.

1. Avant CTP 3.2, **azdata** était appelé **mssqlctl**. Si des versions précédentes de **mssqlctl** ou **azdata** sont installées, il est important de commencer par les désinstaller avant d’installer la dernière version d’**azdata**.

   Pour CTP  version 2.3 ou ultérieure, exécutez la commande suivante. Dans la commande, remplacez `ctp3.1` par la version de **mssqlctl** que vous désinstallez. Si la version est antérieure à CTP 3.1, ajoutez un tiret avant le numéro de version (par exemple, `ctp-2.5`).

   ```powershell
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. Installez la dernière version d’**azdata**. Les commandes suivantes installent **azdata** pour CTP 3.2 :

   **Windows :**

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

   **Linux :**

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!IMPORTANT]
   > Pour chaque version, le chemin d’**azdata** change. Même si vous avez déjà installé **azdata** ou **mssqlctl**, vous devez effectuer une réinstallation à partir du chemin le plus récent avant de créer le cluster.

## <a id="azdataversion"></a> Vérifier la version d’azdata

Avant de déployer un nouveau cluster Big Data, vérifiez que vous utilisez la dernière version d’**azdata** avec le paramètre `--version` :

```bash
azdata --version
```

## <a name="install-the-new-release"></a>Installer la nouvelle version

Après avoir supprimé le cluster Big Data précédent et installé la dernière version d’**azdata**, déployez le nouveau cluster Big Data à l’aide des instructions de déploiement actuelles. Pour plus d’informations, consultez [Guide pratique pour déployer des clusters Big Data SQL Server sur Kubernetes](deployment-guidance.md). Ensuite, restaurez les bases de données ou les fichiers requis.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [Présentation des clusters Big Data SQL Server](big-data-cluster-overview.md).

---
title: Effectuer une mise à niveau vers une nouvelle version
titleSuffix: SQL Server big data clusters
description: Découvrez comment effectuer la mise à niveau de [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (préversion) vers une nouvelle version release.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 90bfaaa1a8cb6fd42081d8afa5feff13f9aec37c
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531958"
---
# <a name="how-to-upgrade-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Guide pratique pour effectuer la mise à niveau de [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article fournit des conseils sur la façon de mettre à niveau un cluster Big Data SQL Server vers une nouvelle version. Les étapes décrites dans cet article s’appliquent spécifiquement à la mise à niveau d’une préversion vers une mise à jour de Service Release SQL Server 2019.

## <a name="backup-and-delete-the-old-cluster"></a>Sauvegarder et supprimer l’ancien cluster

Il n’existe pas de mise à niveau sur place pour les clusters Big Data, le seul moyen de procéder à une mise à niveau vers une nouvelle version release consiste à supprimer et à recréer manuellement le cluster. Chaque version release comporte une version unique d’`azdata`, qui n’est pas compatible avec la version précédente. De plus, si un ancien cluster doit télécharger une image conteneur sur un nouveau nœud, la dernière image risque de ne pas être compatible avec les anciennes images sur le cluster. Notez que l’image la plus récente est tirée (pull) uniquement si vous utilisez l’étiquette d’image `latest` dans le fichier config de déploiement pour les paramètres de conteneur. Par défaut, chaque version release a une étiquette d’image spécifique qui correspond à la version release de SQL Server. Pour effectuer une mise à niveau vers la dernière version, procédez comme suit :

1. Avant de supprimer l’ancien cluster, sauvegardez les données sur l’instance maître SQL Server et sur HDFS. Pour l’instance maître SQL Server, vous pouvez utiliser [Sauvegarde et restauration d’une base de données SQL Server](data-ingestion-restore-database.md). Pour HDFS, vous [pouvez copier les données avec `curl`](data-ingestion-curl.md).

1. Supprimez l’ancien cluster à l’aide de la commande `azdata delete cluster`.

   ```bash
    azdata bdc delete --name <old-cluster-name>
   ```

   > [!Important]
   > Utilisez la version d’`azdata` qui correspond à votre cluster. Ne supprimez pas un ancien cluster avec la version la plus récente d’`azdata`.

   > [!Note]
   > Si vous exécutez une commande `azdata bdc delete`, tous les objets créés dans l’espace de noms identifié par le nom du cluster Big Data sont supprimés, mais pas l’espace de noms lui-même. Vous pouvez réutiliser l’espace de noms pour d’autres déploiements, à condition qu’il soit vide et qu’aucune autre application n’y ait été créée.

1. Désinstallez l’ancienne version d’`azdata`

   ```powershell
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-rc1/requirements.txt
   ```

1. Installez la dernière version de `azdata`. Les commandes suivantes permettent d’installer `azdata` à partir de la dernière version release :

   **Windows :**

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

   **Linux :**

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!IMPORTANT]
   > Pour chaque version release, le chemin de la version `n-1` d’`azdata` change. Même si vous avez déjà installé `azdata`, vous devez le réinstaller à partir du chemin le plus récent avant de créer le cluster.

## <a id="azdataversion"></a> Vérifier la version d’azdata

Avant de déployer un nouveau cluster Big Data, vérifiez que vous utilisez la dernière version de `azdata` avec le paramètre `--version` :

```bash
azdata --version
```

## <a name="install-the-new-release"></a>Installer la nouvelle version

Après avoir supprimé le cluster Big Data précédent et installé la dernière version d’`azdata`, déployez le nouveau cluster Big Data à l’aide des instructions de déploiement actuelles. Pour plus d’informations, consultez [Guide pratique pour déployer [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] sur Kubernetes](deployment-guidance.md). Ensuite, restaurez les bases de données ou les fichiers requis.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters Big Data, consultez [Que sont les [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] ?](big-data-cluster-overview.md)
